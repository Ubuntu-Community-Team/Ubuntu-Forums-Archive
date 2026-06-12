---
title: "problem with mapping folders"
date: 2015-05-16
forum: General Help
---

### Post by daemoncesar on 2015-05-16
Hello , I have a LTSP server on your network running (Ubuntu 14).


On the same network have a file server running Samba .


When the user logs LTSP I run the following script to map a folder on the file server in your home :

```

#!/bin/bash
sudo umount /home/user/public
sudo mount -t cifs -o username=user,password=123,uid=user,gid=user //192.168.0.1/public /home/user/public

```


My problem is that this script sometimes does not work often need to log out and log in again to run the mapping.


Can anyone tell the reason that the mapping does not work often ?


note: I have this script running on various users, and each user has folders other than the public.

---

### Post by bab1 on 2015-05-16
> **daemoncesar said:**
> Hello , I have a LTSP server on your network running (Ubuntu 14).


On the same network have a file server running Samba .


When the user logs LTSP I run the following script to map a folder on the file server in your home :

```

#!/bin/bash
sudo umount /home/user/public
sudo mount -t cifs -o username=user,password=123,uid=user,gid=user //192.168.0.1/public /home/user/public

```


My problem is that this script sometimes does not work often need to log out and log in again to run the mapping.


Can anyone tell the reason that the mapping does not work often ?


note: I have this script running on various users, and each user has folders other than the public.

I wouldn't use sudo in a script to begin with.  You can have an entry in fstab that doesn't mount at boot that allows the users to mount the share via a script as simple as```
mount /home/user/public

```
I have several scripts that I use for mounting Samba shares and/or NFS exports.  The user just clicks on an icon and the file share is mounted.

I would not use the umount command to insure that the mountpoint is clean.  I have two error checks before the share is mounted.  The first is a ping to make sure the server is available and the second is a check to see if a **readme** file can be seen at the mountpoint.  If either of these conditions fail then I send an error message back to the user.  If the conditions are met then a simple mount of the share listed in the fstab is executed. 

Is the script really just as you have it above?  is there really a user named *user*?  You should declare the uid and gid numbers; not the user name.  Most folks put the password in a hidden file.

Samba has a mechanism for private folders on a per user basis.  You do not need to script that for each user.  You just need to setup the one [homes] share.  You only need to configure the public or semi-public file shares for the specific groups of users.

---

### Post by daemoncesar on 2015-05-16
There is no user "user" .


It was only an example ...


Do you have any examples of your script ?

```

mount /home/myuser/public

```

As my file is in another SAMBA server network , such as the "mount " command would be ?

---

### Post by daemoncesar on 2015-05-16
I tried to modify the script as follows:

```

#!/bin/bash
sudo mount -t cifs -o username=user1,password=123,uid=1004,gid=1004 //192.168.0.252/share1 /home/user1/intranet/share1
sudo mount -t cifs -o username=user1,password=123,uid=1004,gid=1004 //192.168.0.252/share2 /home/user1/intranet/share2

```
Yet sometimes it does not work sharing ... Yet sometimes not sharing works ... must use the umount command and mount again to work.

---

### Post by daemoncesar on 2015-05-16
I found the problem ... can not mount the same point in two users ....

```

mount: //192.168.0.1/share1 already mounted or /home/user2/share1 busy

```


Its mount the same directory in different homes ?

---

### Post by bab1 on 2015-05-16
> **daemoncesar said:**
> I found the problem ... can not mount the same point in two users ....

```

mount: //192.168.0.1/share1 already mounted or /home/user2/share1 busy

```


Its mount the same directory in different homes ?

That's correct.  Is it the data the same for both users?  Is this a public share or is it a private share (e.g. for that user only)?

---

### Post by daemoncesar on 2015-05-16
... it is for multiple users sharing has password, but must share in various directories of my system. (LTSP Server).

---

### Post by bab1 on 2015-05-16
> **daemoncesar said:**
> ... it is for multiple users sharing has password, but must share in various directories of my system. (LTSP Server).

I'm not talking about multiple users of LTSP.  I am only referring to the Samba shares.  If you have multiple users sharing the data then you should manage them with group ownership and permissions.  If I have a group of users (i.e. devs).  Then I create a group name and add all of those users into that group.  Then I set the group ownership on the folder I'm sharing and set it to inherit the group ownership.  If you don't do that on a Ubuntu machine you always have file ownership problems.

---

### Post by SeijiSensei on 2015-05-17
Did you specifically choose not to use NFS?  For systems where all the machines are running *nix variants, it's the preferred method of file-sharing.

---

