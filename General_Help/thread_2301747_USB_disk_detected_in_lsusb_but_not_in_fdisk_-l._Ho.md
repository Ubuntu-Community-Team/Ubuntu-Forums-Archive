---
title: "USB disk detected in lsusb but not in fdisk -l. How can I mount it?"
date: 2015-11-05
forum: General Help
---

### Post by aristosv on 2015-11-05
I’ve been struggling with this issue for a couple of days now, read a bunch of suggestions on forums, but it doesn’t seem to be working for me.
First of all this is my machine information: Linux FileServer 4.2.0-16-generic #19-Ubuntu SMP Thu Oct 8 14:46:51 UTC 2015 i686 i686 i686 GNU/Linux / Ubuntu 15.10

This is the output of lsusb:
```
root@FileServer:~# lsusb
Bus 001 Device 002: ID 1058:070a Western Digital Technologies, Inc. My Passport Essential (WDBAAA), My Passport for Mac (WDBAAB), My Passport Essential SE (WDBABM), My Passport SE for Mac (WDBABW

```

And this is the output of fdisk –l:
```
root@FileServer:~# fdisk –l
Disk /dev/sda: 20 GiB, 21474836480 bytes, 41943040 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x844c204c


Device     Boot    Start      End  Sectors  Size Id Type
/dev/sda1  *        2048 40894463 40892416 19.5G 83 Linux
/dev/sda2       40896510 41940991  1044482  510M  5 Extended
/dev/sda5       40896512 41940991  1044480  510M 82 Linux swap / Solaris

```
As you can see the western digital usb disk is detected in lsusb but not in fdisk -l. So I don't know how to mount it.
Why is it not appearing under fdisk -l, and what can I do to mount it?

Thanks

---

### Post by sudodus on 2015-11-05
I suggest some tests to try to identify what is wrong.

- Does the USB disk connect correctly in another computer (it can run linux, Windows or MacOS)?

- Try connecting it in another USB port of the computer.
- Try connecting it with another USB cable.

- Try connecting it in your computer when it is booted from a CD/DVD/USB drive. This is testing if there is something wrong with the installed system.

What computer is it? Maybe someone here knows about the particular hardware in your computer and your particular USB disk - if there are known problems.

So please specify the brand name and model of the computer, or if it is more relevant, the motherboard.

Have you got some USB extension hub or similar?

Is there some other USB device connected? In that case you can disconnect it and only connect your USB disk.

---

### Post by gordintoronto on 2015-11-05
If the external drive is always attached, you could mount it using an entry in fstab. What is the filesystem of the external drive?

---

### Post by aristosv on 2015-11-05
Yes, its always attached. It's an NTFS disk.

---

### Post by aristosv on 2015-11-06
I installed debian on the same computer and the problem was resolved. no worries.

---

### Post by sudodus on 2015-11-15
@ okkadiroglu,

Your problem might be very different, so I move your post to a new thread, and I suggest that we try to solve your problem in your own thread.

Edit: See this link

[How can I mount my USB disk? Detected in lsusb but not in fdisk -l ?](http://ubuntuforums.org/showthread.php?t=2302975)

---

