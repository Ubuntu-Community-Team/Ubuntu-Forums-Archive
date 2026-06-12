---
title: "Is there a way to backup some data from a HD when on a live cd?"
date: 2006-11-01
forum: General Help
---

### Post by eighthate on 2006-11-01
Hey i have my ipod that is connected to my computer, I want to do the clean update to Edgy eft cause i just upgraded and X bugged out and i cant make it work, so anyways, is there any way that i can go in my Hd from this live cd and fetch some data that i want to keep?
thanks :D

---

### Post by Joe_CoT on 2006-11-01
Assuming your linux partition is hda1, 
```

mkdir /media/linuxpart
sudo mount /dev/hda1 /media/linuxpart/ -t ext3 -o iocharset=utf8,umask=000

```

Then your files will be visible in /media/linuxpart and you can copy them from there.

If it's not hda1, and you don't knwo what partion it's on, sudo fdisk -l will list them all, and you'll hopefully be able to figure it out from that.

---

### Post by eighthate on 2006-11-01
> **Joe_CoT said:**
> Assuming your linux partition is hda1, 
```

mkdir /media/linuxpart
sudo mount /dev/hda1 /media/linuxpart/ -t ext3 -o iocharset=utf8,umask=000

```

Then your files will be visible in /media/linuxpart and you can copy them from there.

If it's not hda1, and you don't knwo what partion it's on, sudo fdisk -l will list them all, and you'll hopefully be able to figure it out from that.

it says this:

mount: wrong fs type, bad option, bad superblock on /dev/hda,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Joe_CoT on 2006-11-01
Are you sure that hda1 is your linux partition? Did you running fdisk -l to see what partitions there were? Is your linux filesystem not ext3?

---

### Post by eighthate on 2006-11-01
that is the given code:

> code
Disk /dev/hda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7109    57103011   83  Linux
/dev/hda2            7110        7297     1510110    5  Extended
/dev/hda5            7110        7297     1510078+  82  Linux swap / Solaris

Disk /dev/sda: 20.0 GB, 20000267776 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131    0  Empty
/dev/sda2               6        2431    19486845    b  W95 FAT32
root@ubuntu:/home/ubuntu# 



---

### Post by Joe_CoT on 2006-11-01
Hmm, it looks like hda1 is the right one. does this work?
sudo mount /dev/hda1 /media/linuxpart/

---

### Post by eighthate on 2006-11-01
yep

---

### Post by eighthate on 2006-11-01
gosh thanks my friend!!! U saved My Life!! :D

---

