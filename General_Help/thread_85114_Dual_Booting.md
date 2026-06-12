---
title: "Dual Booting?"
date: 2005-11-01
forum: General Help
---

### Post by Cidere on 2005-11-01
I've decided to try and run a dual-boot so I can install and run exe files. The computer will only support Windows 98 second edition. The hard drive of the comp is 13 Gb. I Whenever I run the setup it says there is not enough memory, is there a way I can uninstall Ubuntu, install Windows, and then reinstall Ubuntu?

---

### Post by John.Michael.Kane on 2005-11-01
You will have to give computer spec's ie amount of ram ect

---

### Post by Cidere on 2005-11-01
[http://www.liberteks.com/productcart/pc/viewPrd.asp?idcategory=46&idproduct=1884#details](http://www.liberteks.com/productcart/pc/viewPrd.asp?idcategory=46&idproduct=1884#details)

It's that exact same system right there with those specs. Although, it has Ubuntu on it instead.

---

### Post by John.Michael.Kane on 2005-11-01
ubuntu needs 256mb of ram as the min so you will have to upgrade your mem. since you only have 96mb

---

### Post by Cidere on 2005-11-01
I have Ubuntu on my comp already though. It's just trying to uninstall it and trying to partition it with windows is the problem

---

### Post by John.Michael.Kane on 2005-11-01
well if your using 5.10 then theres the options to resize freespace . install windows frist then reinstall 5.10 and let it resize the freee space for you.

---

### Post by fannymites on 2005-11-01
If your comp runs ubuntu,  just partition the drive, one for windows, one for ubuntu (the default install is about 1.5 gig so you would want maybe 3 minimum) and another one as a swap partition for ubuntu.
Then install windows first then ubuntu and it should detect the windows partition and add the boot menu.

[EDIT]  Or better still, do what the post above says ^.  (It appeared as I was typing)

---

### Post by Cidere on 2005-11-01
The problem is, when I try to install Winodws, it gets to the point where it asks what to do with the partition (I don't even have a partition), and the only option to choose is to remove it. I choose the option and it says insuffiscient memory. Maybe it's something to do with formatting the hard drive.

and how could I partition the drive from Ubuntu?

---

### Post by fannymites on 2005-11-01
I don't think you will be able to partition the drive from within ubuntu while it is being used.  Also, in the past I had trouble getting windows 98 to install on a partition formatted by a linux partitioner, I had to use fdisk (but maybe that was just a problem with the partitioner or something I did wrong).
Anyway.  Do you have a windows 98 boot disk?  If so you could run that then use fdisk to make the partitions.
Although I have read of people installing windows and linux on one partition I expect it wouldn't be very straight forward.

---

### Post by Cidere on 2005-11-01
After it says Insufficient memory, it quits the installation and shuts off the computer. So, I don't really know what to do. I'll try some things.

---

### Post by LittleReinhart on 2005-11-02
Hey,

On my old laptop (celeron 700, 128Mb ram (of wich 16Mb shared with the vga, hdd = 10Gb) I had dual boot (win98 / win2k) for years. Now I have ubuntu 5.10 installed on it, and it runs (very slow, but it works).
I am following this link [http://ubuntuforums.org/showthread.php?t=54476&highlight=enlightenment](http://ubuntuforums.org/showthread.php?t=54476&highlight=enlightenment) at this moment to try to speed up my ubuntu.

But, what I advice you to do:

1) Put the ubuntu cd back in, boot and remove all the partitions, then cancel the installation.
2) Put the windows 98 cd in, and boot from it
3) do not install windows 98, at the prompt, cleanup your master boot record
```
<a:\> fdisk /mbr
```
4) at the prompt, start fdisk
```
<a:\> fdisk
```
Create a primary partition of at least 3Gb (for windows 98) starting from the beginning of your harddrive
Save it, and exit fdisk (don't know by hard anymore how it was, just follow the instructions inside fdisk)
5) reboot, booting from the windows 98 cd  (this is important because your system still thinks your partitions are the same as befor step 3)
6) again, dont install windows 98 just yet, at the prompt type:
```
<a:\> format c:
```
7) Everytime you want to install some hardware, windows might ask you for the installations cd, personally, I just hate that, here is a way to get around this:
```
<a:\> c:
<c:\> md windows
<c:\> cd windows
<c:\windows\> md system
<c:\windows\> cd system
<c:\windows\system\> md precopy
<c:\windows\system\> cd precopy
<c:\windows\system\precopy\> d:
<d:\> cd win98
<d:\win98\> copy *.* c:\windows\system\precopy\*.*
<d:\win98\> c:
<c:\windows\system\precopy\> setup.exe

```
Don't let windows change your partitions now!
Also, you will get one error telling you that there is already a windows installed on that partition, and it will advice you to install it to an other dir (something like "c:\windows_new\" or something like that, just type the normal windows dir there -> "c:\windows" and go on.
Now windows will be installed from your harddrive, and it will never ever ask for the cd again.
Please remember that I don't use windows anymore, so the code above is what I remember from my old windows-period, so there might be some (type)errors in it.
The precopy dir is now 109Mb big (you may delete it if you nead the space, but then it will ask for the cd again)
8) When that's don, you can try to install linux again, make a swap partition (mine is 0.5Gb), a root partition (for ubuntu I chose ReiserFS (5Gb)) and a data partition (the /home partition, the rest of the disk-space, formatted in fat32).
Don't change anything about the first partion!

Then reboot using windows 98, and I just hope it can acces the data disk (if so, move the "my documents" dir to the d: drive (now if your windows chrashes, and you have to format it... you won't lose your data)).

Greetings,
Reinhart

Btw, just for your information:
If you want to take a backup of your system:
in windows type (after booting from bootdisk/bootcd)
```
<a:\> xcopy /s /c /h /r /e /k c:\*.* d:\backup\*.*
``` This workes for drives formatted in fat32 (doesn't work for ntfs)
I'm not shure anymore what the /x things stand for anymore, but it just copies everything (including system and hidden files).

---

### Post by fannymites on 2005-11-02
Now THAT's a reply.  Hope it solves the problem.

---

### Post by Cidere on 2005-11-02
Thanks a bunch!

---

### Post by Alacrity on 2005-11-02
Cidere,

How did you make out?  You should be in good shape with your system and those two operating systems.

If you are still struggling, I have done this many times on lower level PCs:

..put in 98 boot disc
..puts you into dos
..reformat C:
..do fdisk in dos to set up two partitions
..do FAT32.  Will need for both 98 and future Ubuntu
..install 98 on one partition
..boot on CD your Ubuntu and follow instructions.
..On Ubuntu, it will require you to delete the 2nd partition to make it usable for Linux and format for Linux

Good luck

---

### Post by BLTicklemonster on 2005-11-07
Once done, what happens? Like when you boot, are you allowed at that point a choice of which os to use, or is there something else to do to make this happen? I probably will need to dual boot, and I want to know exactly what to do before hand, and what to expect afterwards. I find too often that I'll get a how to and go and do what it says, and never see what happened but just that one time that I did it.

---

