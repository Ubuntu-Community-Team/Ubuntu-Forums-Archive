---
title: "Can't create a new folder."
date: 2008-05-18
forum: General Help
---

### Post by gammyhand on 2008-05-18
Hi,

I am obviously being really thick here as I can't seem to be able to right click and create a folder or create a folder where I want to from file > create folder.

Can someone point me in the right direction please.

---

### Post by Happy_Man on 2008-05-18
From what are you trying to do this? A liveCD? From your install to another partition? Are you trying to make a folder in an area of the filesystem that requires root permissions to modify? A little bit of background on your problem would be most helpful.

---

### Post by roe_polak on 2008-05-18
It depends on where in the filesystem you are trying to create a folder. You can't write anything in '/', i.e. the root of the filesystem. Actually the only place you are allowed to create files and folders are in '/home/USERNAME' where USERNAME is your, well, username. To write outside our home directory requires root privileges and a very good reason.

---

### Post by FuturePilot on 2008-05-18
Are you using Nautilus in List view?

---

### Post by gammyhand on 2008-05-18
I should have been more specific.

The location is /media/HDA5/music (my data drive so I should be able to) and I just right clicked and all I can do is share the file etc. No option to create a folder. Yes I was using Nautilus in list view. Does it need to be in icon view?

Thanks.

---

### Post by unutbu on 2008-05-18
What type of filesystem is at /media/HDA5? Is it FAT, NTFS, or ext3 for example?
It would be helpful if we could see the output of the command

```
mount
sudo fdisk -l
ls -ld /media/HDA5
ls -ld /media/HDA5/music
```


If the data partition is an ext3 filesystem, and if the problem is an ownership and/or permissions problem, you can probably solve the problem by issuing the following commands:

```
sudo chown -R gammyhand:gammyhand /media/HDA5
sudo chmod -R 755 /media/HDA5
```

Change gammyhand to whatever your username is on your machine.

---

### Post by chrisme on 2008-07-04
> **roe_polak said:**
> It depends on where in the filesystem you are trying to create a folder. You can't write anything in '/', i.e. the root of the filesystem. Actually the only place you are allowed to create files and folders are in '/home/USERNAME' where USERNAME is your, well, username. To write outside our home directory requires root privileges and a very good reason.

How can i set the permissions for '/' and other folders below this like '/var' so to allow me to cerate folders?

---

### Post by unutbu on 2008-07-04
Welcome to the forums chrisme.
You can change the permissions on a directory so that you as a normal user can create new files within that directory by running

sudo chmod 777 path-to-directory

Having said that, you really should not do this to '/' or '/var'. The system is setup with restricted permissions so that only certain programs can access, change or read certain files. By giving all users unrestricted access to all files you will make your system less secure.

Perhaps if you describe what you are trying to accomplish we can tell you how to get there more safely and easily.

---

### Post by chrisme on 2008-07-04
unutbu
Thanks for your answer.
What i am trying to do is to setup a cccam server. This is my first linux installation and i am trying to understand how things work and since i don't have any experience on linux i am following some instructions for  setting up cccam. These instructions are asking for creating folders like /emu, /emu/script, /var/etc and others. This is the reason i want to have permissions to these folders.

---

### Post by unutbu on 2008-07-04
In a terminal type
```

sudo -i
```
Type in your password, and you'll be dropped into a root shell. You can then type in whatever the instructions say as root. 
When you are done, type 
```
exit
```
and you'll be once again a normal user.

---

