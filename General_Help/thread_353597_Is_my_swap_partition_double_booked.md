---
title: "Is my swap partition double booked?"
date: 2007-02-04
forum: General Help
---

### Post by Dodongo Dislikes Smoke on 2007-02-04
I recently noticed my swap partition had stopped being recognized.  I was able to sort that out thanks to this thread: [http://www.ubuntuforums.org/showthread.php?t=343570](http://www.ubuntuforums.org/showthread.php?t=343570)

In the process I noticed that my fdisk -l results were looking kind of weird compared to the others in said thread.  It looks as though the blocks that compose my swap partition are also listed as a separate extended partition:

Disk /dev/hda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2392    19213708+  83  Linux
[B]/dev/hda2            2393        2498      851445    5  Extended
/dev/hda5            2393        2498      851413+  82  Linux swap / Solaris[/B]

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       16907   135805446   83  Linux

As I recall its been this way ever since I first installed in the days of Breezy.  Is this an issue?

---

### Post by taurus on 2007-02-04
/dev/hda2 is known as an extended partition and /dev/hda5 is a logical partition under that extended partition.  There is nothing special about that.  Therefore, you can't technically use /dev/hda2.  Instead, you use the /dev/hda5.

See the space exactly identical for /dev/hda2 & /dev/hda5.

---

### Post by Dodongo Dislikes Smoke on 2007-02-04
Thank you so much!  That's what I hoped to hear.

---

