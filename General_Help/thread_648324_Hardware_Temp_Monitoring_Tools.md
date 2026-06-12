---
title: "Hardware Temp Monitoring Tools"
date: 2007-12-23
forum: General Help
---

### Post by dethredic on 2007-12-23
Are there any programs that well show me my temps?

---

### Post by nick_h on 2007-12-23
hddtemp will monitor hard drive temperatures.
sensors-applet is good for displaying CPU temperature and hard drive temperature.

For other temperatures such as GPU and motherboard try lm-sensors.
If you need a more comprehensive program to display system information have a look at gkrellm.

---

### Post by hit on 2008-01-28
A nice alternative to sensors-applet is also **computertemp**.

---

### Post by articpenguin on 2008-01-28
you can see cpu temp in terminal by
> acpi -t

---

### Post by Micro-soft_WIn_Dos_SuCkS on 2008-07-13
Hello I'm kind of new in this Whole Ubuntu thing, I don't know Code or terminal stuff, I chnage to Linux cu'z muy name said so... Anyways  I wanted to Write on my Secondary Disk of 60GB but it doesn't let me delete, or write, it just read only... 

I tried to use this code that I looked on this post:

```
sudo umount /dev/sda1
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/hdb1 /media/sda1
ls -la /media/sda1
```

It works until it says 

```
joey@joey-pc:~$ sudo umount /dev/sda1
joey@joey-pc:~$ sudo apt-get update
Get:1 http://security.ubuntu.com feisty-security Release.gpg [189B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:2 http://pr.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://pr.archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Ign http://pr.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://pr.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://pr.archive.ubuntu.com feisty/multiverse Translation-en_US
Ign http://pr.archive.ubuntu.com feisty/universe Translation-en_US
Get:3 http://pr.archive.ubuntu.com feisty-updates Release.gpg [189B]
Ign http://pr.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://pr.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://pr.archive.ubuntu.com feisty Release
Hit http://pr.archive.ubuntu.com feisty-updates Release             
Hit http://security.ubuntu.com feisty-security/main Packages        
Hit http://pr.archive.ubuntu.com feisty/main Packages               
Hit http://security.ubuntu.com feisty-security/restricted Packages  
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://pr.archive.ubuntu.com feisty/restricted Packages         
Hit http://pr.archive.ubuntu.com feisty/main Sources
Hit http://pr.archive.ubuntu.com feisty/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://pr.archive.ubuntu.com feisty/universe Packages
Hit http://pr.archive.ubuntu.com feisty/universe Sources
Hit http://pr.archive.ubuntu.com feisty/multiverse Packages
Hit http://pr.archive.ubuntu.com feisty/multiverse Sources
Hit http://pr.archive.ubuntu.com feisty/universe Packages
Hit http://pr.archive.ubuntu.com feisty-updates/main Packages
Hit http://pr.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://pr.archive.ubuntu.com feisty-updates/main Sources
Hit http://pr.archive.ubuntu.com feisty-updates/restricted Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
joey@joey-pc:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fuse-utils libfuse2 libntfs-3g0
The following NEW packages will be installed:
  fuse-utils libfuse2 libntfs-3g0 ntfs-3g
0 upgraded, 4 newly installed, 0 to remove and 203 not upgraded.
Need to get 265kB of archives.
After unpacking 717kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.

```

I say Yes with an y on lower caps and in Caps Y and it ABORTS.

Why does it aborts if I say Yes with an Y or y?

Thanks for the help in advance. :)

---

### Post by dethredic on 2008-07-13
> **Micro-soft_WIn_Dos_SuCkS said:**
> Hello I'm kind of new in this Whole Ubuntu thing, I don't know Code or terminal stuff, I chnage to Linux cu'z muy name said so... Anyways  I wanted to Write on my Secondary Disk of 60GB but it doesn't let me delete, or write, it just read only... 

I tried to use this code that I looked on this post:

```
sudo umount /dev/sda1
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda1
sudo mount -t ntfs-3g /dev/hdb1 /media/sda1
ls -la /media/sda1
```

It works until it says 

```
joey@joey-pc:~$ sudo umount /dev/sda1
joey@joey-pc:~$ sudo apt-get update
Get:1 http://security.ubuntu.com feisty-security Release.gpg [189B]
Ign http://security.ubuntu.com feisty-security/main Translation-en_US
Get:2 http://pr.archive.ubuntu.com feisty Release.gpg [191B]
Ign http://pr.archive.ubuntu.com feisty/main Translation-en_US
Ign http://security.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://security.ubuntu.com feisty-security/universe Translation-en_US
Ign http://security.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://security.ubuntu.com feisty-security Release
Ign http://pr.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://pr.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://pr.archive.ubuntu.com feisty/multiverse Translation-en_US
Ign http://pr.archive.ubuntu.com feisty/universe Translation-en_US
Get:3 http://pr.archive.ubuntu.com feisty-updates Release.gpg [189B]
Ign http://pr.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://pr.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Hit http://pr.archive.ubuntu.com feisty Release
Hit http://pr.archive.ubuntu.com feisty-updates Release             
Hit http://security.ubuntu.com feisty-security/main Packages        
Hit http://pr.archive.ubuntu.com feisty/main Packages               
Hit http://security.ubuntu.com feisty-security/restricted Packages  
Hit http://security.ubuntu.com feisty-security/main Sources
Hit http://security.ubuntu.com feisty-security/restricted Sources
Hit http://pr.archive.ubuntu.com feisty/restricted Packages         
Hit http://pr.archive.ubuntu.com feisty/main Sources
Hit http://pr.archive.ubuntu.com feisty/restricted Sources
Hit http://security.ubuntu.com feisty-security/universe Packages
Hit http://security.ubuntu.com feisty-security/universe Sources
Hit http://security.ubuntu.com feisty-security/multiverse Packages
Hit http://security.ubuntu.com feisty-security/multiverse Sources
Hit http://pr.archive.ubuntu.com feisty/universe Packages
Hit http://pr.archive.ubuntu.com feisty/universe Sources
Hit http://pr.archive.ubuntu.com feisty/multiverse Packages
Hit http://pr.archive.ubuntu.com feisty/multiverse Sources
Hit http://pr.archive.ubuntu.com feisty/universe Packages
Hit http://pr.archive.ubuntu.com feisty-updates/main Packages
Hit http://pr.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://pr.archive.ubuntu.com feisty-updates/main Sources
Hit http://pr.archive.ubuntu.com feisty-updates/restricted Sources
Fetched 3B in 1s (2B/s)  
Reading package lists... Done
joey@joey-pc:~$ sudo apt-get install ntfs-3g
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  fuse-utils libfuse2 libntfs-3g0
The following NEW packages will be installed:
  fuse-utils libfuse2 libntfs-3g0 ntfs-3g
0 upgraded, 4 newly installed, 0 to remove and 203 not upgraded.
Need to get 265kB of archives.
After unpacking 717kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.

```

I say Yes with an y on lower caps and in Caps Y and it ABORTS.

Why does it aborts if I say Yes with an Y or y?

Thanks for the help in advance. :)

Hi. Welcome to the forums.
1) I don't think this is the right thread for you post.
2) Proper english always helps ;)

Do you have enough space on your HD?

---

