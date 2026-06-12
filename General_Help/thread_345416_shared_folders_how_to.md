---
title: "shared folders how to"
date: 2007-01-24
forum: General Help
---

### Post by BackwardsDown on 2007-01-24
I have got 2 pc's:

computer 1 with kubuntu dual boot windows (most of the time I am using kubuntu) 
ip: 192.168.123.148

computer 2 with kubuntu with xubuntu package installed (most of the time I am using xfce)

So now I want to let them share folders, but I have no idea how this works:( .
I have now shared a folder on computer 1, the folder is called Downloads, and when I right-click->share it says with samba options:
name: DOWNLOADS

On my pc 2 I do this command:
> niels@pentium3:/home/public$ sudo mount -t smbfs //192.168.123.148/DOWNLOADS /home/public -o username=niels,password=pass4computer1,uid=1000,gid=1000
niels@pentium3:/home/public$ ls
niels@pentium3:/home/public$ 

But my /home/public is still empty!

How come?:confused:

---

### Post by scrooge_74 on 2007-01-25
If you are sharing in Linux use NFS and mount the folders as drivers, if you are doing it with a XP machine you need to configure SAMBA properly

---

### Post by steveneddy on 2007-01-25
> **scrooge_74 said:**
> If you are sharing in Linux use NFS and mount the folders as drivers, if you are doing it with a XP machine you need to configure SAMBA properly

Continue the conversation and tell him HOW to configure SAMBA properly.

I want to know also.

---

### Post by bodhi.zazen on 2007-01-25
> **steveneddy said:**
> Continue the conversation and tell him HOW to configure SAMBA properly.

I want to know also.

Start here: [http://ubuntuforums.org/showthread.php?&t=202605](http://ubuntuforums.org/showthread.php?&t=202605)

Post if you have specific questions.

---

### Post by scrooge_74 on 2007-01-25
> **steveneddy said:**
> Continue the conversation and tell him HOW to configure SAMBA properly.

I want to know also.

The link bodhi provided is very usefull, should get you working

I dont know if in there was the link about configuring SAMBA and FIRESTARTER so you can use NetBios without problems

[http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138](http://www.ubuntuforums.org/showthread.php?t=190542&highlight=open+port+138)

---

