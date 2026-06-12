---
title: "Boot Error 24 at Grub loading"
date: 2007-11-01
forum: General Help
---

### Post by ADloser on 2007-11-01
A few days ago I tried booting up my Ubuntu machine and got this message right at the start:

Error 24.

At which point everything freezes.

I put in the boot disk and ran e2fsck, and got this message:

The superblock could not be read or does not describe a correct ext2
filesystem. If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
e2fsck -b 8193 <device>

(same message when I try e2fsck -b 8193 <device>)

I'm sure I put the right drive for <device>. Can someone please help me out?

---

### Post by ADloser on 2007-11-02
help anyone?

---

### Post by petruha on 2007-11-11
Only in case you had several HDDs in your system:

Might well be that GRUB is trying to boot from another disk, that does not have what GRUB expects to see there, let's say one of the RAID devices or such. 

It happened to me a few times already because of a magic (read - random, or more precisely: based on who wins in a race) way that BIOS uses to list disks in the system, especially if one had different disks/controllers (like Onboard_SATA + IDE + AddOnCard_SATA). The GRUB relies on the BIOS in order to enumerate disks, AFAIK.

In my case I fixed it by simply disabling all other disks from the BIOS boot order.

You may also consider revising your /boot/grub/menu.lst and /boot/grub/device.map. Needless to say you'll have to boot from another media.

Good luck!

---

### Post by ADloser on 2007-12-02
Ok I found a solution.
Use

mke2fs -n <device>

to find alternative superblocks and then run e2fsck
using one of those alternative superblocks.
Worked for me,

---

### Post by fjgaude on 2007-12-03
Congrats for fixing the problem. But, I would worry that my hard drive is going bad... How old is it?

---

