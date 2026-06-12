---
title: "Unable to mount flash drives regardless of file system"
date: 2008-06-20
forum: General Help
---

### Post by Dark Coz on 2008-06-20
I tried mounting a flash drive and I got a pop-up message saying "Invalid mount option when attempting to mount the volume".  I'm using USB 1.1 and I installed ubuntu successfully from a flash drive before, but now I can't mount any of them, even if I formatted it to FAT32 or FAT.

---

### Post by 7raTEYdCql on 2008-06-20
I think you must format your hard disk to ext4 format. I had a similar problem earlier when i formatted my hard disk to FAT32 or any other format. I think you should format to either to ext2/ext3(pref. ext3)

---

### Post by Dark Coz on 2008-06-20
> **i.mehrzad said:**
> I think you must format your hard disk to ext4 format. I had a similar problem earlier when i formatted my hard disk to FAT32 or any other format. I think you should format to either to ext2/ext3(pref. ext3)

How do I do that?  And how do I get the ext4 working in Windows XP as well?

---

### Post by werries on 2008-06-20
eh, i have a computer that does that. i just force it to mount.
```
sudo mount /dev/sdc1 /media/disk 
```
This is where /dev/sdc1 is my flash drive and /media/disk is the mount point.
if you need to find out what your flash drive's /dev is, do 
```
sudo fdisk -l
```
and if it says the mount point doesn't exist, use something like
```
mkdir /media/disk 
```
or replace "disk" with whatever you want to name it.
and then to unmount, use
```
sudo umount /media/disk 
```
maybe this will help?

---

### Post by Dark Coz on 2008-06-20
Sorry about the bump, but I've got another question about mounting the drive.  Why doesn't ubuntu support FAT or FAT32 filesystems?

---

### Post by angelsguitar on 2008-06-20
> **Dark Coz said:**
> Sorry about the bump, but I've got another question about mounting the drive.  Why doesn't ubuntu support FAT or FAT32 filesystems?

What do you mean? Ubuntu DOES support FAT and FAT32 filesystems.  I've never had any problems with FAT or FAT32 filesystemas in Ubuntu.

---

### Post by werries on 2008-06-20
it does. im not sure what exactly it is about the drive not mounting..

the connection i see is that i installed it to that computer using a flash drive also.
so i think installing from a flash drive causes errors when connecting other drives via USB

So you can either use my brute-force-super-command-line method, or reinstall from a cd.

---

### Post by Dark Coz on 2008-06-20
> **werries said:**
> it does. im not sure what exactly it is about the drive not mounting..

the connection i see is that i installed it to that computer using a flash drive also.
so i think installing from a flash drive causes errors when connecting other drives via USB

So you can either use my brute-force-super-command-line method, or reinstall from a cd.

Installing from the CD was out of question because of buggy BIOS drivers or something.  Every time I boot from CD, it keeps on crashing unpredictably.  Regular CDs will not work at all since my CD-RW drive is dying, but it still recognizes CD-Rs and RWs, but that made the BIOS buggy.

---

### Post by werries on 2008-06-20
well i guess for now you can do my force method. i don't have enough knowledge to figure out the actual bug in the invalid boot methods. the error doesnt actually give any more information so im not sure what to do about a permanent solution instead of a forced workaround.

---

### Post by Dark Coz on 2008-06-20
> **werries said:**
> well i guess for now you can do my force method. i don't have enough knowledge to figure out the actual bug in the invalid boot methods. the error doesnt actually give any more information so im not sure what to do about a permanent solution instead of a forced workaround.

I did boot & install from USB (even though my BIOS didn't support USB booting, LOL - I ejected the disc after loading the kernel and the USB was recognized before installation).  Maybe that was the problem.  I'll see what I can do, but I won't reply until Tuesday.

---

### Post by wpshooter on 2008-06-20
> **Dark Coz said:**
> Installing from the CD was out of question because of buggy BIOS drivers or something.  Every time I boot from CD, it keeps on crashing unpredictably.  Regular CDs will not work at all since my CD-RW drive is dying, but it still recognizes CD-Rs and RWs, but that made the BIOS buggy.

Can you please tell me what you mean by "buggy BIOS drivers or something" ?

---

### Post by Dark Coz on 2008-06-20
> **wpshooter said:**
> Can you please tell me what you mean by "buggy BIOS drivers or something" ?

My BIOS was old (PhoenixBIOS 4.0 Revision 6 - it came with hp pavilion xt963 desktop computers).  Maybe the CD-RW driver is also dying, I don't know...

---

### Post by wpshooter on 2008-06-20
Have you looked to see if there is a newer BIOS update for your computer and have you checked to see if the firmware of your CD drive needs to be updated ?

---

### Post by Dark Coz on 2008-06-20
> **wpshooter said:**
> Have you looked to see if there is a newer BIOS update for your computer and have you checked to see if the firmware of your CD drive needs to be updated ?

I checked the hp site since I use the onboard cd-writer (it's a 16x speed, but I'm using a 12x RW).  I can't look inside the driver for more details without damaging the exterior.  BIOS Updates was also out of question.  Just go to hp.com and click on software & driver downloads, then type xt963, then click Windows XP and you'll see proof.  Or for a shortcut, here's the link.
[http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&lang=en&dlc=en&product=62764]("http://h10025.www1.hp.com/ewfrf/wc/softwareList?os=228&lc=en&cc=us&lang=en&dlc=en&product=62764")

---

### Post by wpshooter on 2008-06-20
When you are burning your Ubuntu CD, what speed are you burning it at ?

If you are burning at anything higher than 4X, it is likely that you are going to have problems with the integrity of the CD.

As far as the firmware for the CD drive is concerned you need to go to the website of the manufacturer of the drive and see if there is a firmware update that might be available.  If you have Windows on this computer you should be able to see the brand and model number of the CD drive in control panel.  As far as the BIOS update is concern, I would just not just take the fact that we are not obviously seeing one listed on the HP site that there might not be one available.  I would see if I could find an 800 number for HP support and see if they would be willing to tell me if there is an update available.

---

### Post by Dark Coz on 2008-06-21
> **wpshooter said:**
> When you are burning your Ubuntu CD, what speed are you burning it at ?

If you are burning at anything higher than 4X, it is likely that you are going to have problems with the integrity of the CD.

As far as the firmware for the CD drive is concerned you need to go to the website of the manufacturer of the drive and see if there is a firmware update that might be available.  If you have Windows on this computer you should be able to see the brand and model number of the CD drive in control panel.  As far as the BIOS update is concern, I would just not just take the fact that we are not obviously seeing one listed on the HP site that there might not be one available.  I would see if I could find an 800 number for HP support and see if they would be willing to tell me if there is an update available.

I did use Imgburn, but no matter what my write speed is set, the burn rate is always 4x and I can't lower it.  I used ImgBurn because of freeware, but is it buggy or something?  Actually, I figured out how to mount the flash drive in Ubuntu.  Apparently, it's in the web page on how to install ubuntu from the flash drive.  I forgot the link though...

---

