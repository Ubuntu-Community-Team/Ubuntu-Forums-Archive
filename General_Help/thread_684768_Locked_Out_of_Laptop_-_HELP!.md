---
title: "Locked Out of Laptop - HELP!"
date: 2008-02-01
forum: General Help
---

### Post by hodad on 2008-02-01
Did a backup of my work files using archive manager.  I decided to archive my Desktop folder, and did it successfully, resulting in Desktop.tar.gz.  Unfortunately, this hosed my laptop GUI, and now I can't even get into the GUI.  I get a blocky screen on reboot that says "the GDM group 'gdm' does not exist. Please correct gdm..."

It then drops into a command line as root.  Have tried lots of things to get back my laptop to no avail.

I would like to try and copy the "Desktop.tar.gz" file onto my USB flash drive, and just reinstall Ubuntu, but I can't get the file to copy onto the flash.  I think it has something to do with mount points,  I cant understand how to mount the flash drive under the command terminal.  When I'm logged in as root, I can access the Destop.tar.gz file, but can't transfer it to the flash drive.

How can I mount the flash memory stick , so that I can copy off the .tar.gz file?

Thanks:confused:

---

### Post by doddo on 2008-02-01
Hello!

I assume ur using VFAT as filesystem for that device, so here's how to copy that archieve:

#1 plug in the device. then

```
 dmesg 
```

when i plug in a usb stick to my gentoo box. dmesg outputs this 

```
scsi 5:0:0:0: Direct-Access     SigmaTel MSCN             0100 PQ: 0 ANSI: 4
sd 5:0:0:0: [sda] 241920 512-byte hardware sectors (124 MB)
sd 5:0:0:0: [sda] Write Protect is off
sd 5:0:0:0: [sda] Mode Sense: 38 00 00 00
sd 5:0:0:0: [sda] Assuming drive cache: write through
sd 5:0:0:0: [sda] 241920 512-byte hardware sectors (124 MB)
sd 5:0:0:0: [sda] Write Protect is off
sd 5:0:0:0: [sda] Mode Sense: 38 00 00 00
sd 5:0:0:0: [sda] Assuming drive cache: write through
 sda: sda1
sd 5:0:0:0: [sda] Attached SCSI removable disk
sd 5:0:0:0: Attached scsi generic sg0 type 0
usb-storage: device scan complete

```
the device name listed between those brackets there is the device name, so my stick gets mapped as "sda"

then
```

mkdir /media/tmp
mount -t vfat /dev/sda1 /media/tmp

```
Assuming that you wanna mount the first partition of that device

then just cp the tar file to /media/tmp

oh and dont forget to umount the device once done
```
umount /media/tmp
```

---

### Post by hodad on 2008-02-01
Thanks!  I'll give it a try and report back!

---

### Post by hodad on 2008-02-01
It WORKED!!

Thank you!  

Now I think I understand the mount process too (Bonus!).

:KS

---

### Post by doddo on 2008-02-01
Thats great =D

---

