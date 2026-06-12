---
title: "How to share files in UBUNTU (newbie)"
date: 2005-03-18
forum: General Help
---

### Post by emmbec on 2005-03-18
Hi, I'm new to linux and I want to share a folder with write permission, so I can back up some files I have in another computer running GENTOO, I want to install UBUNTU on the gentoo machine but I don't know how to share a folder like in WINDOWS so I can search my computer on the network(LAN) and then just copy the files to the UBUNTU computer. Thanks

---

### Post by lifewithryan on 2005-03-18
You shouldn't have to share.  You must abandon the windows mentality ;)

There are a few ways to do this.  My recommended way is to have an ssh server installed on one of your two machine and an ssh client.
(SSH stands for secure shell).

So say you have an ssh server insalled on your Gentoo box.  (for arguments sake we'll call this box gentoo, creative huh?!?)

From your Ubuntu box, cd to the directory you want to copy the files to and type:

"scp -r username@gentoo:/path/to/files/* ."  (dont' forget the trailing period)

that should prompt you for your password on the gentoo box.  Once entered, it will copy the files to your current directory.

You can do the same thing with Nautilus, (Gnome's file browser) but I've noticed that tends to corrupt image file occasionally.  Try using the command line version first.

---

### Post by emmbec on 2005-03-20
OK, how do I install the ssh server so windows computers can also connect to the UBUNTU box and be able to upload files to it. Thanx

---

### Post by kaptk2 on 2005-03-21
To share files with a windows box I found that samba works best. To get samba:
```
sudo apt-get install samba smbfs
``` 

The web is full of stuff on how to setup samba and it is really quite easy. Once that is installed you can go to your windows box and from the network neighborhood access your linux box.

---

### Post by ubuntu_demon on 2005-03-21
[QUOTE=kaptk2]To share files with a windows box I found that samba works best. To get samba:
```
sudo apt-get install samba smbfs
``` 

The web is full of stuff on how to setup samba and it is really quite easy. Once that is installed you can go to your windows box and from the network neighborhood access your linux box.[/QUOTE]
 [www.ubuntuguide.org](www.ubuntuguide.org) is a good starting point

---

### Post by rookie on 2005-03-22
i have installed samba and smbfs and i can access my windows shares from the ubuntu box.

i also see my ubuntu box in windows, but i can't access it. it asks me for username and password, but it won't accept anything. i tried username/pw is use to start ubuntu and i also tried the root/pw. it didn't work.

any ideas? don't i have to specify in ubuntu which folders i'd like to share? if so, how would i do this?

---

