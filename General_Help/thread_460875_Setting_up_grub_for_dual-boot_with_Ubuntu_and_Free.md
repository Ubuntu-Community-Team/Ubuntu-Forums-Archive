---
title: "Setting up grub for dual-boot with Ubuntu and FreeBSD"
date: 2007-06-01
forum: General Help
---

### Post by boomklever on 2007-06-01
Hi

First of all, I hope that I posted this on the right board.
In the past, I ran a FreeBSD only system. Having bought a new (and significantly larger) hard disk, I decided to set up a dual-boot system with Ubuntu. I've now messed around with grub for some time but I seem to be unable to make it boot my FreeBSD.
Has anybody got some help on how to achieve this or can point me to a good howto?
I never needed to worry about setting up a boot-loader, so I have to admit that I'm sort of a newbie in that respect. ;)

Here's the output of fdisk -l:
```

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1824    14651248+  83  Linux
/dev/hda2            1825        4801    23912752+  83  Linux
/dev/hda3            4802        4863      498015   82  Linux swap / Solaris
/dev/hda4   *        4864        9729    39086145   a5  FreeBSD

```

Thanks in advance for your help.

boomklever

---

