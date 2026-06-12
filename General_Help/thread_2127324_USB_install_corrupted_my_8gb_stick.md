---
title: "USB install corrupted my 8gb stick?"
date: 2013-03-19
forum: General Help
---

### Post by steel74 on 2013-03-19
I realize that by installing the image onto a USB it could corrupt the stick (or so a disclaimer told me) however I expected that I would be able to fix it as I have done in the past. This time not so much and I am at a loss for a next step. I tried reformatting in Windows, says it can not format the drive and to make sure it is connected or that the device is not Read Only. I cannot do this as I can not access the device. It shows up in computer as J: with 0 used and 0 free space. I tried using DISKPART to format but it says no volume selected, even though it shows disk 5 as being selected (i DID select it). I tried "attributes volume clear hidden" but it says no volume selected (again it IS selected). I tried list partition and it says no partitions. Any help would be appreciated, I am sorry if this is a repost but I am off to class tonight and do not have the time to sift through forums. Please any help/links! Thank you!

P.S. I would prefer not to download random apps from unknown sources to get this usb back to 8gb. Sorry the dos shell was not letting me highlight text to copy and paste otherwise i would have :/

---

### Post by Cheesemill on 2013-03-19
You should be able to use [gparted]("apt://gparted") to sort this out, just select your USB drive from the drop-down box in the top right and then got to Device > Create Partition Table.

Once this is done you should be able to create an 8GB partition that fills the drive.

---

### Post by sanderj on 2013-03-19
Under Windows or Linux I would expect "fdisk" should see the drive. Delete the partition. Unplug it. Plug it in. Then Windows should be able to create a partition and format it.

WARNING: using fdisk is like playin with fire. Be careful.

HTH

---

### Post by steel74 on 2013-03-20
> **Cheesemill said:**
> You should be able to use [gparted]("apt://gparted") to sort this out, just select your USB drive from the drop-down box in the top right and then got to Device > Create Partition Table.

Once this is done you should be able to create an 8GB partition that fills the drive.

Gparted does not see the drive at all, i think. I am seeing dev/sda1(ext4) / dev/sd2(extended) / dev/sda5(linux-swap)

removed the usb, all 3 still show up upon refresh, however...

sudo blkid command shows sda1 and sda5...with and without the usb in

sorry i am kind of a noob to linux i have been spoon fed by windows and now trying to get into Linux - i used to love DOS, but i am very unfamiliar right now with all things Linux, am learning as i go bare with me please!

---

### Post by steel74 on 2013-03-20
> **sanderj said:**
> Under Windows or Linux I would expect "fdisk" should see the drive. Delete the partition. Unplug it. Plug it in. Then Windows should be able to create a partition and format it.

WARNING: using fdisk is like playin with fire. Be careful.

HTH

fdisk does not even seem to work in win7?? well atleast not from the shell..from what i have read on the net, its for formatting a new hdd via a boot disc - i do not have windows cd/boot disc for this

Microsoft Windows [Version 6.1.7601]
Copyright (c) 2009 Microsoft Corporation.  All rights reserved.


C:\Users\ian>format J:
Insert new disk for drive J:
and press ENTER when ready...
The type of the file system is RAW.
The new file system is FAT.
Verifying 0M
The specified cluster size is too big for FAT.

C:\Users\ian>fdisk j:
'fdisk' is not recognized as an internal or external command,
operable program or batch file.

---

### Post by steel74 on 2013-03-20
ok i got it figured out...sdb from the dropdown list was my usb (i completely missed that part of your instructions at first) thank you for the help

this is exactly what i wanted to do..learn by trial and error...i am off to a roaring start HAHA - thanks again!

---

