---
title: "Installed Ubuntu to seperate hard drive, now windows 7 wont boot."
date: 2012-12-14
forum: General Help
---

### Post by Toobatee on 2012-12-14
Hello! I'm new to these forums and very new to Ubuntu.
Ive been using windows 7 for the longest time and recently got a new hard drive. I decided to try out Ubuntu and install it to a 10gb partition on the new, empty hard drive. 

The problem is, that grub cant seem to find the windows 7 boot even though it recognizes that its there. Ive tried the boot repair tool.

Results: **_[http://paste.ubuntu.com/1440936/](http://paste.ubuntu.com/1440936/)_**


Ive had this ubuntu CD lying around for about a year and I didn't want to re download the installer for ubuntu 12. So, I ended up installing 10.04 LTS.
ok, pop in the disk and since I didn't want to wipe windows 7 off of my first hard drive, and i only wanted to install Ubuntu to a small 10gb partition, I selected the advanced options. I created a partition for the system files and the swap. Ok. Ubuntu installed fine, boots up.. yay! You may want to know that the video drivers didnt work with my nvidia graphics card until i got the drivers. 

Ok, so, ubuntu is working fine. yay! ok. I decided that I was done messing with ubuntu for now and wanted to go back to windows 7. Probelm is, i get this error.


Error: no such device: se1055bb10559abb,
error: no such partition.
Press any key to continue.




Im not very farmiliar with ubuntu. Ive looked up and down the internet for my problem, but i cant find any answer. Id be happy to answer any questions anybody has.


Thanks guys!

---

### Post by techvish81 on 2012-12-14
the problem is with the partitioning of your second hdd, it is a gpt partition. so you may have to repartition the drive and reinstall ubuntu.

---

### Post by Toobatee on 2012-12-14
> the problem is with the partitioning of your second hdd, it is a gpt  partition. so you may have to repartition the drive and reinstall  ubuntu.

First of all: Thanks for the quick response!
Second of all: Thanks for understanding what the heck is going on! O:)

So, do you think I should just download the newest Ubuntu and reinstall it from a CD?

And what does GPD partition mean anyways?

---

### Post by techvish81 on 2012-12-14
it is type of partition table , i'm not an expert on the subject but i know by my experience that what is going to work.

now you should better download latest iso 12.04 lts for stability and 12.10 if you want the latest software. create a dvd and boot in to it.  select 'try ubuntu' and enter 'gpart in the dash, select the application shown below. 

in gparted , you have to repartition your drive . (backup,  if you have imp data) delete all the partitions on the drive, make sure it is the new drive.  create a 50-100gb primary ext4 partition and a fat32/ntfs  partition for the rest of space. reboot with dvd and select install ubuntu. select 'something else' in the installer. now select the required ext4 partition for ubuntu and set the mount point as root. select the windows drive for bootloader installation. now proceed with installation. 

done.:-)

---

### Post by oldfred on 2012-12-14
I converted to gpt partitioning with 10.10 on a 160GB drive and had Windows XP on the other drive. Back then you had to add a parameter to get chain loading from gpt to mbr to work.
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:GTP_MS_DOS](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:GTP_MS_DOS)
Alternative fix:
[http://ubuntuforums.org/showthread.php?t=1545165](http://ubuntuforums.org/showthread.php?t=1545165)

With the new versions there is no issues as it sees both MBR & gpt and add the extra parameters automatically..

---

### Post by Toobatee on 2012-12-15
Ok! I got it to work! Thanks guys!

I tried downloading the ISO for ubuntu 12.04 LTS overnight ( my internet is not very good) And i think it failed somehow because the file is only 300 or so MB when it should be around 600. So, i tried burning onto the disk, then booting from it anyways. It didnt boot so i tried doing what oldfred said. And it worked! yay!

So now my question would be, should I redownload 12.04, or just update linux from the update manager?

Thanks a million guys!

---

### Post by oldfred on 2012-12-15
It is up to you. The new version has lots of changes, should work better with newer hardware. Unity is one of the biggest changes. 
Best to download and test in live mode. I prefer USB flash drives now as install or live mode is a bit faster and it is reusable.

10.04 Desktop expires April 2013.
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

---

### Post by Toobatee on 2012-12-17
Alright. Ill update via reinstalling. 

Thanks for all the help, guys!

---

### Post by YannBuntu on 2012-12-17
Hi
Please use the thread tools to mark it [SOLVED]

---

### Post by CJ_Hudson on 2012-12-19
If I can just figuratively "stick my oar in" here, if I have new installations/re-installations of Windows etc. when I've already got an Ubuntu partition and the boot loader, she goes AWOL her, I use [Boot Repair utility]("http://sourceforge.net/projects/boot-repair/files/")- burnt to a CD ROM, runs 'live', works like magic every time!

---

### Post by Toobatee on 2012-12-20
Oh! ok, Ill have to remember that.

Thanks guys!

---

