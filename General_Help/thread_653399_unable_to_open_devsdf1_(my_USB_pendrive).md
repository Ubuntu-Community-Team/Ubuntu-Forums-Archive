---
title: "unable to open /dev/sdf1 (my USB pendrive)"
date: 2007-12-29
forum: General Help
---

### Post by Ioky on 2007-12-29
I tried a partition my USB drive, and install linux on it, however, after a few try, My USB drive are no longer working, I try to fix it in many difference OS such as Mac, linux and window, but no luck on any of those, Windows are able to detect it, but can't load it, and Linux is able to connect it as well, but can not mount it. when even I try to do something to it, it say Unable to open /dev/sdf1

ioky@BiTuX:~$ fdisk /dev/sdf1

Unable to open /dev/sdf1

I hope this is only a software problem, if it is the USB itself , I need to exchange it.

---

### Post by taurus on 2007-12-29
First, you need to include the sudo if you want to use fdisk.

```
**sudo** fdisk /dev/sdf1
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by Ioky on 2007-12-29
ioky@BiTuX:~$ sudo fdisk /dev/sdf1
[sudo] password for ioky:

Unable to open /dev/sdf1
ioky@BiTuX:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d2f5a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1229     9871911   82  Linux swap / Solaris
/dev/sda2   *        1230        7307    48821535   83  Linux
/dev/sda3            7308       60801   429690555   83  Linux
ioky@BiTuX:~$ 

it turn out the same thing, no lucky.

---

### Post by taurus on 2007-12-29
If you don't have it, install gparted.  Then, fire it up, System -> Administration, and see what does it say about that USB drive.

---

### Post by Ioky on 2007-12-29
There don't even have anything about USB , all I have is thing about hard drive.

it seems like it can't even get detected.

---

### Post by Ioky on 2007-12-30
thanks for your help though

---

