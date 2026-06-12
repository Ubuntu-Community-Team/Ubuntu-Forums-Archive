---
title: "USB problems"
date: 2007-10-29
forum: General Help
---

### Post by bonneyt on 2007-10-29
I'm a windows user but trying to find a good alternative.  I am running Gutsy, and everything is working great! but i cannot seem to get my USB thumb drive to work.  I've followed the instructions in many of the forums but nothing has fixed the problem.  It doesn't recognize the drive at all.  at first it was giving an error message saying it cannot mount the device, in the message it suggested that i edit the /etc/fstab file and add the line

/dev/sdb1       /media/Thumby ntfs-3g defaults,force 0 0

thumby is the name of the USB drive

after the reboot it still does not recognize the device but the error does not come up anymore.  I also noticed, if i have the drive list open (computer) it will flash a new device but will not stay there to use

thanks for the help!

---

### Post by Partyboi2 on 2007-10-29
Not sure if this will help
[http://ubuntuforums.org/showthread.php?t=582045](http://ubuntuforums.org/showthread.php?t=582045)

---

### Post by bonneyt on 2007-10-29
I tried that, didn't do anything unfortunately :(

---

### Post by Eystein Bye on 2007-10-29
Do you see the device listed with the command:
> lsusb

Are you sure the device uses ntfs and not fat?
> sudo mount -t vfat /dev/sdb1 /media/Thumby

---

### Post by bonneyt on 2007-10-29
lsusb says

Bus 004 Device 009: ID 058f:6390 Alcor Micro Corp. 
Bus 004 Device 006: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive

both devices say unable to mount.  I believe the first one alcor micro corp, is NTFS the one called thumby might be fat32 but i'm not certain

---

### Post by PmDematagoda on 2007-10-29
Try mounting your device like this:-

1) Create a folder in /media using nautilus in sudo mode(sudo nautilus) or other method.

2) Type this:-

[HTML]sudo ntfs-3g /dev/pathofUSB(such as sdg1) /media/nameofnewfolder -o rw[/HTML]

---

### Post by bonneyt on 2007-10-29
nothing happened new their either... 

I had an idea so i ran with it... I installed partition editor and formatted the drive with fat32.  It worked after that.  This drive was initially formatted with windows XP which i later found out that formatting NTFS with windows XP is somehow different than if i formatted with say windows Vista... why? i don't know but it seemed to have caused the problem this time.  That solves my problem!  thanks for all the help!!

---

### Post by fiskking on 2008-01-14
having the same problem...read within a different thread to format in FAT not FAT32.  here is the output that I have gotten:


fisk@RaneYisrael:~$ lsusb
Bus 004 Device 003: ID 0781:5406 SanDisk Corp. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:0920 Logitech, Inc. QuickCam Express
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000
fisk@RaneYisrael:~$ sudo mount -t vfat /dev/sdb1 /media/disk
Password:
mount: /dev/sdb1 already mounted or /media/disk busy
mount: according to mtab, /dev/sdb1 is already mounted on /media/disk

My problem is that I am trying to write an .iso to the drive using DeVeDe.
Should I go back to windows(xp) and format it using FAT 32?

---

### Post by fiskking on 2008-01-14
got it to work

---

