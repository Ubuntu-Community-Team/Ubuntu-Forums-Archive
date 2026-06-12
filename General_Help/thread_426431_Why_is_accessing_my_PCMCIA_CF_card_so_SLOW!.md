---
title: "Why is accessing my PCMCIA CF card so SLOW!"
date: 2007-04-28
forum: General Help
---

### Post by kevdog on 2007-04-28
For the first time with kubuntu feisty I mounted my CF card via a CF card adaptor into my laptop PCMCIA slot.  After plugging in the device, I did the following:

sudo fdisk -l 
  This told me the device was listed at /dev/sda1

I then made a directory
sudo /media/cf

and then made a mount point
sudo mount /dev/sda1 /media/cf

Everything works -- I guess -- but when accessing the device at the command line, it takes like 5 minutes to open one of the dcim directories.

I used Konqueror also, and I kept receiving at the bottom of the interface -- device stalled..

Any idea how I can improve IO time.

Ive used a USB device before, and the response time of this device was normal.

---

### Post by kevdog on 2007-04-28
Is FAT16 notoriously slow as a filesystem with linux?

---

### Post by kevdog on 2007-04-28
No one else has this problem???


I added /dev/sda1 to the pmount.allow file.  This however if anything just slowed the access of this device down even further.  I takes almost 1 minute to mount the drive manually using pmount, despite that this is supposed to happen automatically since it is listed in the pmount.allow. file.

Im really confused whats going on here.

---

### Post by kevdog on 2007-04-29
Is there a bug in Feisty ---

After rebooting the computer wtih the CF card in place the boot process hangs,

If the computer is restarting with the CF card out of the slot and then inserted after boot, the system will try to automount the sda1 drive under /media/Lexar\ Media, but I can not access the directory.  What exactly is going on.  Attempting sudo cd /media/Lexar\ Media returns command not found???

---

