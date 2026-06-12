---
title: "Root denied access to network shares?!"
date: 2013-03-23
forum: General Help
---

### Post by Rebelli0us on 2013-03-23
I want to copy a file from the File System to a mounted network share. So I start Nautilus as root, but root cannot access "network:///". So I navigate to "/home/<USER>/.gvfs" and I'm denied access!

[ATTACH=CONFIG]240456[/ATTACH]

 Why is this happening?

---

### Post by Rebelli0us on 2013-03-23
Also I went into "Samba Server Configuration" on the target machine and added root to the list of users allowed to access the shared folder. But root is still denied access! Why is it so hard to drag a file from my computer to another machine on my network?

---

### Post by coldcritter64 on 2013-03-23
> **Rebelli0us said:**
> I want to copy a file from the File System to a mounted network share. So I start Nautilus as root, but root cannot access "network:///". So I navigate to "/home/<USER>/.gvfs" and I'm denied access!

[ATTACH=CONFIG]240456[/ATTACH]

 Why is this happening?
That sounds like you are trying to write to a file in another machine by altering its mounted version locally. 

It won' t work because the file's mounted permissions are set by the remote machine on which the original file exists, not the machine on which you are viewing it and attempting to change it; even using root locally won't help, as the file is on another physical machine. 

Write permissions and user access need to be set on the remote machine itself for you to change the file in the manner you are currently using. Cheers.

Edit: root accounts in Ubuntu are locked by default, I don't think allowing "root" on the target is going to help you much. User level access and file / folder ownership/permissions on the target machine are more likely to be your problem.

---

### Post by Rebelli0us on 2013-03-23
Thank you. I would gladly (re)mount the network shares by logging into the remote machine  as root. But root cannot even see the network in Nautilus. So how can root mount network shares?

---

### Post by deadflowr on 2013-03-23
You shouldn't need to run as root to merely copy files from the system folders to your user folder. Only if you move or change them.
At least that's the case I've always encountered.

---

### Post by steeldriver on 2013-03-23
gvfs mounts are user mounts - by default they are not even readable by root

try just using regular nautilus (not sudo)

---

### Post by coldcritter64 on 2013-03-23
> **steeldriver said:**
> gvfs mounts are user mounts - by default they are not even readable by root

**try just using regular nautilus (not sudo)**
This OP, if access for your user to the remote machine is  OK and permissions to read and write are set in the remote machine for your user, then accessing the share through a user nautilus window should work fine. 

If you can't set the access and permissions on the remote machine, then even using root on the local machine will not help you.

---

### Post by Rebelli0us on 2013-04-06
Thank you. Yes I **can** access the network shares as a regular user, but I can't copy from them into the file system. So I end up copying from them into my local home dir and then I open Nautilus as root to copy/edit them. It looks like the runaround.  Isn't the chief administrator's job to prevent unauthorized access to networks? How can he do that when he can't even see what shares users are mounting?!

---

### Post by bab1 on 2013-04-06
> **Rebelli0us said:**
> Thank you. Yes I **can** access the network shares as a regular user, but I can't copy from them into the file system. 
As it should be.  A mortal user has no permission to copy or create files outside of their home directory by default> 
So I end up copying from them into my local home dir and then I open Nautilus as root to copy/edit them. It looks like the runaround. 
 Of course it's a run around, remember only the root user has the rights to the entire local file system.  This could include creating mounting shares in such a fashion that anyone can copy the data to anywhere.  To do this you would have to edit the smb.conf file.> 
 Isn't the chief administrator's job to prevent unauthorized access to networks? 
Indeed it is.> 
How can he do that when he can't even see what shares users are mounting?!I assume that you have created Samba *usershares*, not root administrated Samba Shares.  These usershares are for users to share their data to other users, not to move their data to the system file structure.

On the other hand I could be completely misunderstanding what you are trying to do.  How about an example of what you are attempting?

---

### Post by Rebelli0us on 2013-04-06
I mounted a share on my network to fetch a script .sh file and copy it to /usr/local/sbin/       ...simple stuff.

All this security nonsense is out of control and it's killing the desktop in favor of mobile devices.

---

### Post by bab1 on 2013-04-06
> **Rebelli0us said:**
> I mounted a share on my network to fetch a script .sh file and copy it to /usr/local/sbin/       ...simple stuff.
Yes it's very simple -- if you do a few things in preparation.  The directory* /usr/local/sbin/   * is owned by root:root with no permissions to either read or write for any other users.  So you need (as the administrator) to provide access to: either that directory or a suitable subdirectory of * /usr/local/sbin/   * for your users.  I provide access via group permissions so I have this as the directory ownership root:users.  Then I provide 0775 permissions. This took me 2 minutes to do.  Once this is done you should be able to copy a file from wherever you have mounted the share. 

[COLOR="#0000FF"]Edit:  The use of the *users* group works only if you add your user to that group.  All of my users that I feel comfortable with are in that group.  You can see the users in that group with this command ```
getent group |grep users
```[/COLOR]
> 

All this security nonsense is out of control and it's killing the desktop in favor of mobile devices.
I disagree.  The security paradigm has been the same for a long time and is well understood.  This ( /usr/local/sbin/ ) is a directory for system binaries, not  for general data or personal scripts.

---

### Post by Rebelli0us on 2013-04-07
> **bab1 said:**
> Yes it's very simple -- if you do a few things in preparation.  The directory* /usr/local/sbin/   * is owned by root:root with no permissions to either read or write for any other users.  So you need (as the administrator) to provide access to: either that directory or a suitable subdirectory of * /usr/local/sbin/   * for your users.  I provide access via group permissions so I have this as the directory ownership root:users.  Then I provide 0775 permissions. This took me 2 minutes to do.  Once this is done you should be able to copy a file from wherever you have mounted the share. 

[COLOR="#0000FF"]Edit:  The use of the *users* group works only if you add your user to that group.  All of my users that I feel comfortable with are in that group.  You can see the users in that group with this command ```
getent group |grep users
```[/COLOR]

I disagree.  The security paradigm has been the same for a long time and is well understood.  This ( /usr/local/sbin/ ) is a directory for system binaries, not  for general data or personal scripts.



Thank you, that’s too complex for copying a couple of files. Linux assumes that **every** user is the IT Administrator at Fort Knox. 

It’s my computer, I decide how much security I want. I can’t allow some imaginary entity named *root* to prevent me form doing **my** work on **my** computer.

The solution is very simple. The **real** owner should be asked during installation how much security he wants, if any. In many cases **none** is needed. e.g., I have a machine for friends to play with Linux. There is no security required, and as such I don’t want the OS harassing my friends or constantly asking for password, especially since the machine is remotely operated **without a keyboard**.

Does any of this make sense?:popcorn: ...cause 0775 means nothing to me:)

---

### Post by bab1 on 2013-04-07
> **Rebelli0us said:**
> Thank you, that’s too complex for copying a couple of files. Linux assumes that **every** user is the IT Administrator at Fort Knox. 

It’s my computer, I decide how much security I want. I can’t allow some imaginary entity named *root* to prevent me form doing **my** work on **my** computer.
Root doesn't prevent you from doing anything.  If you want it changed then you have to change it.  You are the administrator (root) of your machine, 
> 
The solution is very simple. The **real** owner should be asked during installation how much security he wants, if any. In many cases **none** is needed. e.g., I have a machine for friends to play with Linux. There is no security required, and as such I don’t want the OS harassing my friends or constantly asking for password...There is nothing in the OS preventing you from doing that.  You can set it up however you wish.  You are the master of the machine.  I don't think you can blame the vehicle, just because you don't know how to drive it>  

...especially since the machine is remotely operated **without a keyboard**.
The remote machine has nothing to do with permissions on the local machine.  The permissions are set when the share is mounted.  No keyboard on the remote machine is irrelevant > 

Does any of this make sense?:popcorn: ...cause 0775 means nothing to me:)
Exactly!  until you decide to learn about how Linux works you will always have issues.

---

