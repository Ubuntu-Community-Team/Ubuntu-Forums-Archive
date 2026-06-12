---
title: "Multiple users accessing one mounted share"
date: 2016-03-11
forum: General Help
---

### Post by sander12 on 2016-03-11
I am in to the process of setting up a new machine (ubuntu2) in which two users will login (let's name them user1 and user2). To manage the machine I have added a third user 'admin'. All users are all members of the same group (users).

On this machine the admin user permanently mounts a samba share shared by another ubuntu machine (ubuntu1) (the choice for samba was made as this share will also be mounted by windows and mac machines). 

The relevant section in the smb.cnf on ubuntu1:
```

[Linux-Share-01]
  guest ok           = no
  path               = /storage/shared
  valid users        = @users
  write list         = @users
  force group        = users
  force directory mode = 0775
  force create mode     = 0775
  browsable          = yes
```

The mount sequence in fstab is as follows:
```
//ubuntu1/Linux-Share-01 /mnt/Linux-Share-01   cifs    credentials=/home/admin/.smbcredentials     0     0
```

This set-up already brings me quite a long way to where I want to go. The share 'Linux-Share-01' is mounted using the credentials of the admin user. When user1 and user2 log into the machine, they can both read from and write to the share by accessing /mnt/Linux-Share-01. 

Currently, the files written by user1 and user2 on the share will be owned by the 'admin' user:

```
-rwxrwxr-x 1 admin users    0 mrt 11 19:13 x.dat
```

_My question_: is there a way to modify the current setup (or implement a different setup) that will allow the two users to access the share such that the files they create are fully owned by the respective user? The desired output would read like this if both users would create a file on the share:

```
-rwxrwxr-x 1 user1 users    0 mrt 11 19:13 x.dat
-rwxrwxr-x 1 user2 users    0 mrt 11 19:13 y.dat
```

Many thanks!

---

### Post by bab1 on 2016-03-11
> **sander12 said:**
> 
_My question_: is there a way to modify the current setup (or implement a different setup) that will allow the two users to access the share such that the files they create are fully owned by the respective user? 
File and directory ownership is set at mount time when using cifs.  Why do you feel you need to use fstab to mount the share?  You will not have this problem if you allow the user to browse to the share and mount it using the Gnome Virtual File System (gvfs).

On the other hand; why is it important for the user to "own" the file or directory?  This is really an access issue and as members of the *_**users**_ group*, that user has access already.  Am I missing something?

---

### Post by sander12 on 2016-03-12
> **bab1 said:**
> File and directory ownership is set at mount time when using cifs.  Why do you feel you need to use fstab to mount the share?  You will not have this problem if you allow the user to browse to the share and mount it using the Gnome Virtual File System (gvfs).

Indeed, true. However, the users will be able to launch calculation jobs that use processors on both machine. Hence, the share will need to be present on both machine, all the time (otherwise the software can't access the data needed for the calculations). So have the user manually mount it when they need it, is not the preferred option.

> On the other hand; why is it important for the user to "own" the file or directory?  This is really an access issue and as members of the *_**users**_ group*, that user has access already.  Am I missing something?

At the moment I can see a few reasons why this could be advantageous:
[LIST]
[*]Transparency: after working with this setup for some time, it might not be obvious anymore which user created or generated which files.
[*]Permission issues: users might move files from their home directory to the (calculation) share and back. Retaining the same uid in this process would be preferred.
[*]Ideally, it might even be preferred to set the forced directory and create mode to 0750, such that the users will be able to see each others data on the share, but not be able to delete it.
[/LIST]

Thanks for any feedback!

---

### Post by bab1 on 2016-03-12
> **sander12 said:**
> ...However, the users will be able to launch calculation jobs that use processors on both machine. Hence, the share will need to be present on both machine, all the time (otherwise the software can't access the data needed for the calculations). So have the user manually mount it when they need it, is not the preferred option.

Samba has nothing to do with processing data.  It merely provides a method of mounting a part of a remote file system (on the server) to the local host's file system (the Samba client).  My guess is that the processing of the data is done where the process executable resides.  Most likely this is at the client as Samba sever just a file server. 
> 
[QUOTE]On the other hand; why is it important for the user to "own" the file or directory? This is really an access issue and as members of the users group, that user has access already. Am I missing something? 


At the moment I can see a few reasons why this could be advantageous:
[LIST]
[*]Transparency: after working with this setup for some time, it might not be obvious anymore which user created or generated which files.
[/LIST]
[/QUOTE]If this is a concern, you will have to have each user mount the share via a script that sets their uid when they log in.  As I said before there is no other method when using the *_mount_* command in either a script or using only /etc/fstab.  In a sense this is what Autofs does and it might be worth looking into.  

Ultimately you will always be mounting the share to the local file system using CIFS as the file system protocol.  This means there is no way to change the owner (user or group) from the client side later on.  I give my users a clickable icon on the launcher that launches a script that both mounts and later un-mounts the share .  There is no reason that you couldn't create a script that does this same thing at bootup and shutdown.  You can use either Upstart (Ubuntu 14.04 LTS or less) or systemd (Ubuntu 16.04 LTS or greater) for this.  The old school method for this uses rc.local and rc0.d for bootup and shutdown scripts. > 
[LIST]
[*]Permission issues: users might move files from their home directory to the (calculation) share and back. Retaining the same uid in this process would be preferred.
[*]Ideally, it might even be preferred to set the forced directory and create mode to 0750, such that the users will be able to see each others data on the share, but not be able to delete it.
[/LIST]
Neither of these will positively force the file/directory ownership or permissions.  The latter permissions settings will not stop a user from being able to delete any files or subdirectories in the share.  You would have to set the Linux  permissions to include a sticky bit on the share directory.  The access right to delete is set on the directory that holds the data, not on the file itself.  If you can write to the directory you can delete in the directory also unless the is a sticky bit set.  The /tmp fdirectory is an example of this ```
drwxrwxrwt   5 root root  4096 Mar 12 00:18 tmp
```
FWIW, You should only set the directory permissions to *force directory mode = 0775 (or 770)*.  The file mode should be *force create mode  = 664 (or 660)*.  There is no need to set the files to executable generally.

---

### Post by sander12 on 2016-03-13
> **bab1 said:**
> My guess is that the processing of the data is done where the process executable resides.  Most likely this is at the client as Samba sever just a file server.

Indeed, this if often the case, but not in the current setup I am trying to establish. Calculations can be started from either of the two machines, and the software will then launch jobs on both machines to perform the task at hand. This is also why the data needs to be accessible on both machines (under the same path even).

> **bab1 said:**
> If this is a concern, you will have to have each user mount the share via a script that sets their uid when they log in.  As I said before there is no other method when using the *_mount_* command in either a script or using only /etc/fstab.

Thanks, I guess this is the answer I was looking for.
 
After a bit of further reading on the forum, I realised maybe I was try to solve two problems at the same time. I now opted for two approaches:
[LIST]
[*]I set up a separate samba share to users from Windows / Mac to assess the data on the machines (all data on this share is owned by the users group).
[*]For the calculations I established an NFS share between the two different machines. This maintains all user ids, and addresses the issues I mentioned before.
[/LIST]

Both solutions were easy and quick to setup using the standard Ubuntu HOWTO's.

---

