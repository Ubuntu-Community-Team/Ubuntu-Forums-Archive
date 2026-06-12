---
title: "complaint- Disc Image writer poor sorry it is, fails"
date: 2017-11-12
forum: General Help
---

### Post by sdowney717 on 2017-11-12
My situation.
I had an ubuntu 18 install-able iso on the sandisk cruiser 4gb thumb drive, made by unetbootin.
I download mint iso
I go to write the iso using disc image writer.
Says not enough space, I say ok write it thinking it will simply erase and write the new iso.
No, it writes what it can then quits...

I try booting it, fails to boot mint.

So I go to look at it, and try to delete the files on it, they are locked, SEL linux rules says I cant delete, cant drag files to trash, It is owned by me.

Only solution quickly is put it in windows PC, format to fat.
Install unetbootin and get this thing going again...

---

### Post by sdowney717 on 2017-11-12
ok, ubuntu has created a serious problem with the usb drive.
I formated in windows, works, I copied some picture files they work.

Now EVERY time I put the drive in the ubuntu PC, it loads up linux mint like those files are on there!
It also shows 2 mounts for the drive when I plug it in.

my 4gb drive says only 2mb , and the other location says 1.7gb

gparted wont let me delete it.
quess I will use win10, delete the partition, redownload mint and write using unetbootin on windows.

---

### Post by sdowney717 on 2017-11-12
success with win10. Disk management successfully erased the useless partition. 
Downloaded mint 
ran unetbootin on windows

done.

---

### Post by oldos2er on 2017-11-12
18 is pre-alpha, so moved to Ubuntu Development Version.

---

### Post by sdowney717 on 2017-11-12
> **oldos2er said:**
> 18 is pre-alpha, so moved to Ubuntu Development Version.

scott@scott-MS-7596:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	**Ubuntu 17.10**
Release:	17.10
Codename:	artful
scott@scott-MS-7596:~$ 

It is mint 18 iso, but ubuntu 17.10 is what I am running. I am using ubuntu 17.10 to write the iso of mint 18.2

---

### Post by wildmanne39 on 2017-11-12
*Thread moved to **General Help for a more appropriate fit**.*

---

### Post by HermanAB on 2017-11-12
To write an ISO file to a USB thingy, there is a hard way and an easy way.  The problem is that the easy way requires the operator to be very careful.

The easy way, is to write the ISO file to the USB thingy using Data Definition (dd).  The problem is that if you don't pay attention to what you are doing, then you can overwrite your hard disk instead.

Basically, open a terminal and run dmesg.  Stare at the screen a bit.  Now plug in the USB thingy, run dmesg again and stare at the screen a bit.  Write down the name of the USB device, e.g. 'sdb'.

Now copy the ISO file to the USB thingy:
$ sudo dd if=filename of=devicename

That's it.  

It can hardly be simpler, but if you get your 'if' and 'of' wrong, then your whole computer will fall over, so don't come crying if that happens.

---

### Post by oldos2er on 2017-11-13
Since your first post says Ubuntu 18 that's the information I was going off of. It helps to be clear.

---

