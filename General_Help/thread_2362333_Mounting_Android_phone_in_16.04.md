---
title: "Mounting Android phone in 16.04"
date: 2017-05-27
forum: General Help
---

### Post by oygle on 2017-05-27
I have installed all the 'mtp' software, as advised in other posts. I can connect USB cable and browse the phone (Samsung Galaxy S4), but I want to be able to **MOUNT** it.

Mount point is /media/mtp/phone and the permissions are 775

When I connect the cable and do the required command ..

> 
**sudo mtpfs -o allow_other /media/mtp/phone**
Listing raw device(s)
Device 0 (VID=04e8 and PID=6860) is a Samsung Galaxy models (MTP).
   Found 1 device(s):
   Samsung: Galaxy models (MTP) (04e8:6860) @ bus 1, dev 8
Attempting to connect device
Listing File Information on Device with name: ********** (Galaxy S4)
fuse: bad mount point `/media/mtp/phone': Transport endpoint is not connected

There is nothing showing in the folder /media/mtp/phone

If I try to access that path I get a msg "Could not enter folder /media/mtp/phone"

The phone shows up with an lsusb command ..

```

**lsusb**
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 008: ID 04e8:6860 Samsung Electronics Co., Ltd Galaxy (MTP)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

and the mount for it is there with the mount command ..

> 
mtpfs on /media/mtp/phone type fuse.mtpfs (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other)


any attempt to look in that path or even the one above it is unsuccessful ..

> 
**ls -al /media/mtp/phone**
ls: cannot access '/media/mtp/phone': Transport endpoint is not connected

**ls -al /media/mtp/**
ls: cannot access '/media/mtp/phone': Transport endpoint is not connected
total 8
drwxr-xr-x 3 *********  ********* 4096 May 27 13:41 .
drwxr-xr-x 9 root  root  4096 May 27 13:41 ..
d????????? ? ?     ?        ?            ? phone


How do I get this phone to mount properly please ?

---

### Post by ajgreeny on 2017-05-27
Difficult to help much as we do not know what you've already tried, but as a start, have a good read through the long thread at [https://ubuntuforums.org/showthread.php?t=2226702](https://ubuntuforums.org/showthread.php?t=2226702) and come back again if that's no help.

---

### Post by vasa1 on 2017-05-27
And use [CODE] tags instead of [QUOTE] tags when providing information copied from the terminal or from log files.

---

### Post by gordintoronto on 2017-05-27
In my experience, you no longer need to use mtp to access an Android phone. I plug in my phone, a file manager window opens up -- and the phone is mounted. I'm pretty sure this behaviour started in 16.04, but I'm currently running 17.04.

---

### Post by ajgreeny on 2017-05-28
> **gordintoronto said:**
> In my experience, you no longer need to use mtp to access an Android phone. I plug in my phone, a file manager window opens up -- and the phone is mounted. I'm pretty sure this behaviour started in 16.04, but I'm currently running 17.04.
Yes, I believe you are correct; I had to go through all that procedure in 14.04 but since running 16.04 my phone and tablet mount with no action needed from me, just like any other USB mass storage device.

---

