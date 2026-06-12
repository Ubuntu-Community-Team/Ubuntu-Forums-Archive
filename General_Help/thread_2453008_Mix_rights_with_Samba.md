---
title: "Mix rights with Samba"
date: 2020-11-01
forum: General Help
---

### Post by WhiteTigerIT on 2020-11-01
They are in trouble granting the rights to Samba shares.
Three Samba users must have rights to folders owned by another user.
I give an example with these folders.
/FolderRoot/Folder1
/FolderRoot/Folder2
/FolderRoot/Folder3
**UserMaster** is the owner of the whole tree so the folders are now marked **UserMaster:UserMaster**.


**User1** must see all folders and be able to write into them.
In Win10 it must see the shared folders **FolderRoot**, **Folder1**, **Folder2** and **Folder3**.


**User2** must only be able to see the **Folder1** folder and be able to write into it.


**User3** must only be able to see the **Folder2** and **Folder3** folders and be able to write into them.


I'm doing some tests, but until now if I assign the rights of the users, I lose the rights of UserMaster _which instead absolutely must not lose_.

---

### Post by ActionParsnip on 2020-11-01
You could use smbpasswd to set a password then set user access in smb.conf to allow and block users. Do check this online

---

### Post by TheFu on 2020-11-01
> UserMaster is the owner of the whole tree so the folders are now marked UserMaster:UserMaster.
This is a really bad idea. 
[LIST]
[*]usernames should all be lowercase. Avoid future pain by doing that now. Always. 
[*]Don't mix case for hostnames or userids or groupids.
[*] The usermaster shouldn't be the owner of anything that others can also write.  I'm assuming usermaster is also in the sudo group.
[/LIST]

There are multiple solutions, but know that Samba ignores Unix permissions and each share can only have 1 permission for the owner and 1 permission for the group unless you run Active Directory and handle all the complexities that requires.

A few options:
[LIST=1]
[*] force all users to connect using the same Unix userid. All files and directories will be owned by a single userid:groupid on the Unix side. Look for "force user = " option. Their Samba userid/password would be whatever you setup for each.
[*] Setup SMB shares based on the permission for that group, then train the users to connect using their specific "share name" and block other connections.  Unix groups can be used for this.
[*] Setup the [homes] section where-by each user gains access to only their $HOME directory. Inside that home, typically /home/{userid}, setup symbolic links to the specific directories you want them to see. If those directories are on different partitions, you'll need to enable the "wide links = yes" option.  There are security ramifications with using that option, but if the users don't have ssh or any other access into the samba server, then they won't be able to create any other symbolic links, so the risks are minimal.  I think.
[/LIST]

If it were me, I'd train user1 to use **sftp**. sftp is available from any networked OS. In linux, every file manager supports the sftp:// URL (or perhaps ssh:// which is technically incorrect).  From Windows, use **WinSCP** or Filezilla. Then user1 would have whatever access their Unix userid provides. No more. No less. Then the permissions issues can be solved by using standard Unix group+directory+file permissions which are extremely well understood.

For example:
Create 2 new Unix groups.  u3nu1 u2nu1; I don't remember how off the top of my head, so you can use a GUI or CLI version. Doesn't matter.  Put user2 and user1 into the "u2nu1" group.  Put user3 and user1 into the "u3nu1" group. This will be important later.

```
cd /opt/  # this directory already exists. Use whatever you like, just know that some snap packages can only access very specific directories outside the /home/{userid} area.
sudo mkdir Folder1 Folder2 Folder3

sudo chown Folder1 user2

sudo chgrp Folder1  u2nu1
sudo chmod 770 Folder1
sudo chmod g+s Folder1

sudo chown Folder2 Folder3 user3
sudo chgrp Folder2 Folder3  u3nu1
sudo chmod 770 Folder2 Folder3
sudo chmod g+s Folder2 Folder3

```
From this point forward, any new files or directories created under those Folder[1-3] will get g+w for the correct group.

Now, setup samba for 3 shares using the **valid users** as the 2 different groups you just setup. "valid users= @u2nu1" for the first share and "valid users= @u3nu1" for the 2nd and 3rd.

If you want to make life easier, you could just have 2 shares and put F2 and F3 under the 2nd share.  I'd lock down the share directory so user3 can't modify the parent or create F4, F5, F6, ... inside it.

I probably left out something.  Hopefully, someone else will see it and post a correction.

The way I set this up means their Linux userids will have similar permissions to the directories. If that isn't important, there are other methods, like using "invalid users =" as an option. I've never done that. All our systems have Unix users matched and samba is purely for local convenience.

I'm assuming you are using the /etc/samba/smb.conf file to setup everything for samba. Other tools probably don't support all the necessary options.

---

### Post by WhiteTigerIT on 2020-11-02
@TheFu
I use names with capital letters only for ease of reading. In fact, in Linux they all have only lowercase letters.


All users have their home folder in /home/{userid}.
Only usermaster has its home on /var/cloud/usermaster because it is associated with a script to manage Dropbox synchronization and only /var has enough space because it is located on a separate disk.


I use WinScp, but a normal user only uses "Explorer" in Windows.


I try to think about the examples you gave me, but my goal is to secure the files.
Making everyone use the same userid leads me to think that if there is some wrongly assigned right, a user can access a folder they shouldn't even see.

---

### Post by Morbius1 on 2020-11-02
Is there an objection to creating 4 separate shares instead of one?

You could create a "Master" share for User1 that allows access to the whole tree:
```
[FolderRoot]
path = /FolderRoot
read only = no
valid users = User1
force user = UserMaster

```
And a separate one for each of the other subdirectories. For example:
```
[Folder2]
path = /FolderRoot/Folder2
read only = no
valid users = User1, User3
force user = UserMaster
```

---

### Post by TheFu on 2020-11-02
> **Morbius1 said:**
> Is there an objection to creating 4 separate shares instead of one?
 
+1  Stated much more clearly than my feeble attempt describing options.
If the Unix-side permissions don't matter, very elegant.

---

### Post by rsteinmetz70112 on 2020-11-02
I typically set up shared folders some where besides the "/home" directory something like "/files". I then set the gid of shares to "domain users" then restrict access with the "valid users = " and "force group = domain users". That way when users change I can easily edit the access to the folders.

---

### Post by WhiteTigerIT on 2020-11-03
> **TheFu said:**
> This is a really bad idea. ...

I probably left out something.  Hopefully, someone else will see it and post a correction.
...


You forgot UserMaster (or usermaster).
I created a virtual machine to do these tests and once I applied the rights on the folders, then UserMaster lost the ability to access these folders.

Maybe I didn't explain myself well initially: UserMaster is the owner of the tree, **but must remain the owner**.
UserMaster is associated with a service that automatically writes and deletes files and folders in the entire tree.

Under FolderRoot there are not only subfolders, but also other subfolders under other subfolders and all of these, with their content, are managed by UserMaster.
Then there are the users who have the "parallel" rights on some folders and subfolders of those individual branches.
These users also have the rights to write, modify or delete files and folders, but without removing rights to UserMaster who must be able to continue managing this tree.

To be clear, UserMaster is associated with Dropbox's sync service and syncs all Dropbox content in real time.
Users access only those folders to which they have rights. They can create, modify and delete files and folders from the folder they have rights to and all under them.

In parallel UserMaster synchronizes the changes on Dropbox.
This is the reason why UserMaster cannot lose the rights.

---

### Post by WhiteTigerIT on 2020-11-03
> **Morbius1 said:**
> Is there an objection to creating 4 separate shares instead of one?

You could create a "Master" share for User1 that allows access to the whole tree:
...

This setup is very simple and clean, but most of all it works.:p


Many thanks to all of you.

---

