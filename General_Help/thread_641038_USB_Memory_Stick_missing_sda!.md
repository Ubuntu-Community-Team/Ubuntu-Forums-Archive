---
title: "USB Memory Stick: missing sda*!"
date: 2007-12-14
forum: General Help
---

### Post by Sagadon on 2007-12-14
I'm trying to mount my USB memory stick, and it's not showing up!  I've tried rebooting with the memory stick in place to see if it would pick it up, but no luck.  It's simply missing all sd* from /dev/. Here's some details:

lspci:
> 
00:04.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)


fdisk -l:
> Disk /dev/hda: 2559 MB, 2559836160 bytes
255 heads, 63 sectors/track, 311 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1         290     2329393+  83  Linux
/dev/hda2             291         311      168682+   5  Extended
/dev/hda5             291         311      168651   82  Linux swap / Solaris

Disk /dev/hdb: 1281 MB, 1281982464 bytes
255 heads, 63 sectors/track, 155 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         141     1132551   83  Linux
/dev/hdb2             142         155      112455    5  Extended
/dev/hdb5             142         155      112423+  82  Linux swap / Solaris


See - /dev/sda1 should be there, but it's simply missing!  I've even made sure the checkbox for auto-detect removable media is checked.

ls /dev/s*
> 
/dev/snapshot  /dev/sndstat  /dev/stderr  /dev/stdin  /dev/stdout

/dev/shm:


dmesg isn't showing any activity when I unplug and plug in the memory stick.

What should I try next?

---

### Post by rfruth on 2007-12-14
Does ROM BIOS see all the memory ?

---

### Post by shirilover on 2007-12-15
Try the following:
```

sudo modprobe -v sd_mod

```
or
```

sudo modprobe -v usb_storage

```

---

### Post by Sagadon on 2007-12-15
modprobe -v sd_mod
> 
insmod /lib/modules/2.6.20-16-generic/kernel/drivers/scsi/sd_mod.ko 


modprobe -v usb_storage
> 
insmod /lib/modules/2.6.20-16-generic/kernel/drivers/usb/storage/libusual.ko 
insmod /lib/modules/2.6.20-16-generic/kernel/drivers/usb/storage/usb-storage.ko 


I'm assuming this means I have the proper libraries installed?

---

### Post by shirilover on 2007-12-15
Yes, have you tried plugging in your USB stick?

---

### Post by Sagadon on 2007-12-15
Yes, of course!   The auto-detect should be picking up my USB memory stick, but it doesn't.  What makes me the most concerned is that /dev/sd* is missing.  Even if there is nothing plugged in, the /dev/sd* descriptors should still be there!  I've even tried rebooting with the stick plugged into both usb ports.

Could it be my usb driver that is not working?

---

### Post by Sagadon on 2007-12-17
I still have no solution.  Any ideas out there?

---

### Post by Sagadon on 2007-12-19
Ok, So lshw shows my usbdriver has not been installed:
> 
*-usb UNCLAIMED
     description: USB Controller
     product: 82371AB/EB/MB PIIX4 USB
     vendor: Intel Corporation
     physical id: 4.2
     bus info: pci@00:04.2
     version: 01
     width: 32 bits
     clock: 33MHz
     capabilities: uhci
     configuration: latency=0
     resources: ioport:d400-d41f


'UNCLAIMED' in lshw means no driver is installed... So I'm searching for a driver to install apparently.  I only see windows drivers so far.

Anyone have any suggestions?

---

### Post by ragzid on 2007-12-28
Hi,

I have a very simillar problem. I can't connect to my father's phone to my laptop (Debian unstable) and to his desktop neither (Gutsy). But it was working in Feisty. So I turned my old desktop, connected the phone and run lsmod. I saw a module **libusual**, but newer kernel (2.6.22 in Gutsy and .23 in my Debian) doesn't include it. I think there is a way to make it running. Now I am going to try to compile that module from kernel source.

Ragzid

P.S.: Sorry for my English :)

---

