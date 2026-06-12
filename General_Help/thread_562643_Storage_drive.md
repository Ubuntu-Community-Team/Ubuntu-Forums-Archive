---
title: "Storage drive"
date: 2007-09-29
forum: General Help
---

### Post by gimpguy2000 on 2007-09-29
Hi , 

Well, I read up on any link possible but wondering if someone can help me out here. I installed Ubuntu on another PC, it's a self built of my son's friend. 
Has Asus 939 mb, 512 ram, 64 dual core AMD and two hard drives, as follows...

Samsung 80 gig > has Ubuntu , using full disk >hda

Samsung 40 gig> Nothing so far>hdb

The problem is, I wanted to set it up as pure storage, nothing more. Now , I used parted to try and create a partition or anything to get this thing recognized and mountable. When I tried mount -a , it's not recognized among other suggestions. What I have now is a part called...

loop 
hdb1
hdb2 
 
and I think one more. Problem is, I want to wipe them out and wipe out the whole drive, start over, and hopefully get it right. 

I can't access the internet with this PC as it's onboard nic is not running right, is there a way to use Parted to wipe the drive? What should I set the drive up as in order to use it for basic storage? 

Note: there are no Windows OSs on here , only Ubuntu and my description above. 

Thanks all,

Paul

---

### Post by dcstar on 2007-09-29
> **gimpguy2000 said:**
> Hi , 

Well, I read up on any link possible but wondering if someone can help me out here. I installed Ubuntu on another PC, it's a self built of my son's friend. 
Has Asus 939 mb, 512 ram, 64 dual core AMD and two hard drives, as follows...

Samsung 80 gig > has Ubuntu , using full disk >hda

Samsung 40 gig> Nothing so far>hdb

The problem is, I wanted to set it up as pure storage, nothing more. Now , I used parted to try and create a partition or anything to get this thing recognized and mountable. When I tried mount -a , it's not recognized among other suggestions. What I have now is a part called...

loop 
hdb1
hdb2 
 
and I think one more. Problem is, I want to wipe them out and wipe out the whole drive, start over, and hopefully get it right. 

I can't access the internet with this PC as it's onboard nic is not running right, is there a way to use Parted to wipe the drive? What should I set the drive up as in order to use it for basic storage? 

Note: there are no Windows OSs on here , only Ubuntu and my description above. 

Thanks all,

Paul

Unless you manually add the mounting information to /etc/fstab, then "mount -a" won't do anything.

Do a forum search as there are numerous detailed HOWTOs on what you need to do.

---

### Post by gimpguy2000 on 2007-09-29
> **dcstar said:**
> Unless you manually add the mounting information to /etc/fstab, then "mount -a" won't do anything.

Do a forum search as there are numerous detailed HOWTOs on what you need to do.

Well thanks for the info but I already spent most of a day searching for my specific issue here, as well followed the /etc/fstab instructions that I found here numerous times and it still won't work. I searched yet again today for some time and nothing seems to fit my problem or answers what type of format an extra drive should be for basic storage. I tried partition manager to format the drive as linux, ntfs, fat 32, <and many others, none would be detected "even with the instructions to mount the drive". Yet I am left with the pieces that I listed above and they won't go away. Oh, well, thanks anyway. 

Paul

---

### Post by southernman on 2007-09-29
[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")

The above link will help you out. It gives info on how to do this using fdisk, which I find much better than using gparted (even it's livecd).

Using fdisk is really easy (relatively speaking of course once you understand the commands and your hdd geometry), and is much more powerful than any gui app out there... or likely to be out there.

---

### Post by gimpguy2000 on 2007-09-29
> **southernman said:**
> [https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive")

The above link will help you out. It gives info on how to do this using fdisk, which I find much better than using gparted (even it's livecd).

Using fdisk is really easy (relatively speaking of course once you understand the commands and your hdd geometry), and is much more powerful than any gui app out there... or likely to be out there.

Thanks for that link, I used Fdisk but not on linux prior to your post, I just used Win98 SE floppy and did Fdisk through there and got rid of all non dos and it seemed to work. Gparted wouldn't create an ext #3 for whatever reason before but did now :)  I am a bit surprised though, it seems lately, all my hard drives are only accessible through root gui. I don't know if it's from an update or what. This being on my PC now, not the one mentioned above. I had to login as root in gui and simply mount them and then they were accessible to me in my user mode. Very odd, they were accessible before, not sure why now they weren't. I did two updates so maybe this had something to do with it, not sure. Anyway, thanks for that link and if I run across this again, I am going to try that. 

Cheers,

Paul

---

### Post by southernman on 2007-09-29
Setting up new partitions, using fdisk has always been a root only task... AFAIK

Don't login as root, as their is nothing you can't do without sudo, or gksudo for gui applications. Login in as root often enough and you'll be back on the forums using a livecd begging for help and mercy from the sudo gods! ;)

---

