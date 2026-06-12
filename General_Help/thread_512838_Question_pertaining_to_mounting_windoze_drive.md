---
title: "Question pertaining to mounting windoze drive"
date: 2007-07-29
forum: General Help
---

### Post by MerlinsLair on 2007-07-29
I did run a search but haven't run across an answer to my problem as yet. I've tried the tutorial that I found on [Psychocats site]("http://www.psychocats.net/ubuntu/mountwindows") and it isn't working.

Here is the output from running sudo fdisk -l

```
Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/hdc: 123.5 GB, 123522416640 bytes
255 heads, 63 sectors/track, 15017 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       14640   117595768+  83  Linux
/dev/hdc2           14641       15017     3028252+   5  Extended
/dev/hdc5           14641       15017     3028221   82  Linux swap / Solaris

```

And here is the output from my fstab file:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc5       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I had this once before but had to reinstall Ubuntu on the 2nd drive due to a corrupted disk. For some reason that eludes me...I can't seem to get it to work this time.

Any ideas?

---

### Post by merlinus on 2007-07-29
If you have not already done this:

```

sudo apt-get install ntfs-3g ntfs-config

```

then:

```

sudo ntfs-config

```

Tick the appropriate boxes and restart.

-merlin

---

### Post by MerlinsLair on 2007-07-30
Hmm, I get this Merlin:

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ntfs-3g

```

Suggestions?

---

