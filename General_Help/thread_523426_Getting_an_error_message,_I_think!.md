---
title: "Getting an error message, I think!"
date: 2007-08-11
forum: General Help
---

### Post by Kissablysoft on 2007-08-11
Hi,
I just restarted my computer for the first time after installing, and this is the error message I am getting...

Booting 'Ubuntu'

(hd0,0)
Filesystem type is fat, partition type 0xc
[Linux-bzImage, setup=0x1c00, size=0x1a82cc]
[Linux-initrd @ 0x1785e000, 0x7918a5 bytes]
Loading, please wait...
NO RAID disks
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! does not exist. Dropping to a shell!


BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh: can't access tty; job control turned off
(initramfs) _

I am trying to run this on a windows 98SE computer with a P2.
Just trying to check it out and see if I like it. I tried ubuntu, Kubuntu, and Xubuntu. Getting the same type of error with all three. Currently have Xubuntu installed now. Any suggestions would be great. Thanks!!

---

### Post by EXCiD3 on 2007-08-11
check this thread out: [http://ubuntuforums.org/showthread.php?t=415009&highlight=job+tty+control+turned+off]("http://ubuntuforums.org/showthread.php?t=415009&highlight=job+tty+control+turned+off")

---

### Post by Kissablysoft on 2007-08-11
> **EXCiD3 said:**
> check this thread out: [http://ubuntuforums.org/showthread.php?t=415009&highlight=job+tty+control+turned+off]("http://ubuntuforums.org/showthread.php?t=415009&highlight=job+tty+control+turned+off")

Is that thread also when booting with Wubi?

---

### Post by EXCiD3 on 2007-08-11
you dont boot with wubi, you just install with wubi.

---

### Post by Kissablysoft on 2007-08-11
You know what I mean. I just worded it wrong. :p

---

### Post by EXCiD3 on 2007-08-11
lol, it has to do with booting into ubuntu, its not wubi specific, its a problem lots of ppl have.

---

### Post by Kissablysoft on 2007-08-11
K, Thank you. Wow, that thread you gave me is LONG!! Been reading since you first posted and only on page 7 and there is 28 of them. :lolflag:

---

### Post by EXCiD3 on 2007-08-11
yeah, i had a thread on hp dv9000 laptops, got to 23 pages, i got it locked and read through everything and made a tutorial to make it easier ;)

---

### Post by ago on 2007-08-13
You should have a couple of log files under /tmp to give some hints

---

