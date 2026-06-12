---
title: "USB Drive problems"
date: 2008-02-22
forum: General Help
---

### Post by Periswell on 2008-02-22
I wanted to put the pendrivelinux distribution on my usb disk but on the tutorial it says to put in the drive letter of the usb drive:
[COLOR="Red"]
"Type fdisk -l and note which device is your USB device. Example:/dev/sdX (X represents your USB drive letter. Through the rest of this tutorial, replace X with your actual drive letter)"[/COLOR]

but for the life of my i cannot find out what letter it is. please help. 

addition, im using ubuntu gusty gibbon if that helps.

-josh

---

### Post by harlan on 2008-02-22
Please post the output of
  $sudo fdisk -l

---

### Post by kwilliam on 2008-02-22
Plug in the flash drive, make sure it's mounted, and then run GParted.  It should show up in the dropdown list in the top right.  (Don't do anything in GParted though!  GParted lets you delete hard drives, etc.)  On my laptop, the hard drive is /dev/sda, and flash drives show up as /dev/sdb, /dev/sdc, etc in the order I plug them in.

---

