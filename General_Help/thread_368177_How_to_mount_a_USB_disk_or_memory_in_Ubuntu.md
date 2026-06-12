---
title: "How to mount a USB disk or memory in Ubuntu"
date: 2007-02-23
forum: General Help
---

### Post by I.You on 2007-02-23
Hi.

I have a 128MB USB memory which is FAT-formatted and a 40GB USB disk ext3-formatted, and using them well on Windows XP.
By the way, (in case of USB disk) I did raw sectors reading from that USB disk (to get superblock infomations), but all values of sector2 (from offset 1024) were zero.
So in order to check it on Linux, I inserted them to Ubuntu.
However, I was unable to mount them on Ubuntu, and errors as follow:

<USB memory>
mount: wrong fs type, bad option, bad superblock on /dev/sdc, missing codepage or other error ...

<USB disk>
mount: /dev/sdc1: can't read superblock

It doesn't matter on Windows but does matter on Ubuntu Linux.
What happen? or is there any other way to mount on Ubuntu?

Help me please.
Thank you.

---

### Post by gradedcheese on 2007-02-23
sure, you can manually mount it:

```

sudo mkdir -p /mnt/usbdisk
sudo mount -t vfat /dev/sdc1 /mnt/usbdisk

```

Does that work?

---

### Post by I.You on 2007-02-23
Thanks a lot, gradedcheese.

That works (USB disk). Thanks!!
However, USB memory doesn't work.

I commanded like this:

sudo mkdir -p /mnt/usbmem
sudo mount -t vfat /dev/sdd /mnt/usbmem

Please...

---

### Post by gradedcheese on 2007-02-23
Instead of /dev/sdd it's probably /dev/sdd1 (you need a partition number).  When in doubt, plug the disk in and then wait a little and run "dmesg" and, toward the end, see what device names it wound up with (there are other ways to do this too of course)

---

### Post by I.You on 2007-02-23
Thanks for quick reply.

I already tried by /dev/sdd1, and then

mount: special device /dev/sdd1 does not exist

Also I already tried dmesg and made sure /dev/sdd.

Thank you.

---

### Post by gradedcheese on 2007-02-23
hmm... what sort of disk is this /dev/sdd anyway?  Please post the output of running:

```

ls -l /dev/disk/by-id/

```
(at least the relevant drives)

---

### Post by I.You on 2007-02-23
Sorry for late reply.

That is NAND flash USB memory.
and output is as follow:

$ls -l /dev/disk/by-id/
total 0
...
~ usb-USB_2.0_Flash_Disk_AA00000000004740 -> ../../sdb

(Here, don't care about sdb because no USB disk which was tested before)

Thank you.

---

