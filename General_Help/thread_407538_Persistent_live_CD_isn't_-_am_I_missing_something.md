---
title: "Persistent live CD isn't - am I missing something?"
date: 2007-04-12
forum: General Help
---

### Post by Rootman on 2007-04-12
I have a USB pen drive that I used the tutorial  found here - > [https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent) to make a persistent CD image boot partition.  It boots and runs fine but is not persistent. I have the "live CD" image and other needed files in a fat32 partition and a separate EXT2 casper-rw partition. I am using the latest beta of Kubuntu.

I have the following in the  syslinux.cfg:
```
DEFAULT custom
GFXBOOT bootlogo
APPEND   preseed/file=preseed/kubuntu.seed boot=casper persistent initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
LABEL custom
  menu label ^Start Ubuntu in persistent mode
  kernel vmlinuz
  append  preseed/file=preseed/kubuntu.seed boot=casper persistent initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash --
TIMEOUT 0
PROMPT 0
F1 f1.txt
F2 f2.txt
F3 f3.txt
F4 f4.txt
F5 f5.txt
F6 f6.txt
F7 f7.txt
F8 f8.txt
F9 f9.txt
F0 f10.txt
```
One thing that is not "normal" in this setup is that I have 3 partitions on the pen drive, 6.7GB fat32 primary #1, 1.0 GB fat32 primary #2 and .3 GB EXT2 primary #3.  I have BartPE stuff on #1 and chain boot to the syslinux boot mbr using GRUB4DOS with the following menu.lst entry:

```
title Kubuntu Feisty Fawn
rootnoverify (hd0,1)
makeactive
chainloader +1
boot
```

As I stated it boots and runs fine - I just loose everything I add or change once I reboot, despite the persistent parameter being used in the syslinux.cfg and the presence of the casper-rw partition.  Any ideas where I'm going wrong?

---

### Post by zvacet on 2007-04-12
> When the Live CD starts up, you will see a menu. Normally, you would just press Enter to start the boot process, but instead, press F4 to access the Other Options menu that allows you to start up the Live CD in special modes. You'll see a list of the arguments that will be passed to the kernel on startup; just add a space and type persistent, then hit Enter. 

That is all I can find.Hope it helped.

---

### Post by Rootman on 2007-04-16
Thanks, I already have the persistent keyword in the APPEND line like so

```
APPEND preseed/file=preseed/kubuntu.seed boot=casper persistent initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- LABEL custom
```

When ever I add or make changes it never stays, examining the casper-rw volume also revels northing's been written to it.  I just tried USBubuntu ( [http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610) ) and it works.  All changed I make are committed to the casper-rw volume.

---

### Post by K0LO on 2007-04-23
Same problem here. It's a bug:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591)

---

### Post by LAF4U on 2007-04-25
> **Rootman said:**
> Thanks, I already have the persistent keyword in the APPEND line like so

```
APPEND preseed/file=preseed/kubuntu.seed boot=casper persistent initrd=initrd.gz ramdisk_size=1048576 root=/dev/ram rw quiet splash -- LABEL custom
```

When ever I add or make changes it never stays, examining the casper-rw volume also revels northing's been written to it.  I just tried USBubuntu ( [http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610](http://www.pendrivelinux.com/2007/01/25/usb-x-ubuntu-610) ) and it works.  All changed I make are committed to the casper-rw volume.

Hi Rootman,

I tried that link too, and it works for me. I boot up my usb key, EXCEPT... I don't see my casper-rw volume. What did I do wrong?

Can I just REFORMAT casper-rw?

Marc.:confused:

---

