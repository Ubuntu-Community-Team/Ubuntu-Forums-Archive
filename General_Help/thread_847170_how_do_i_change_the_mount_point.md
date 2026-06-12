---
title: "how do i change the mount point?"
date: 2008-07-02
forum: General Help
---

### Post by chriskin on 2008-07-02
i have made a mistake and put as a mount point for the main disk of both ubuntu and linuxmint the point /


How can i change the mount point for linuxmint and which one should i put as mount point?

or does it not matter at all?


i cannot find my linuxmint on grub and i thought that this was the mistake

also on the livecd of linuxmint when i go to the computer, it says that i have 800mbs left when i have more than 8gbs, i tried adding the space both ubutnu and linuxmint has and it leave 800mbs, meaning that the linuxmint has a problem understanding that these are two different partitons :S

---

### Post by fooman on 2008-07-02
in a terminal, run the following command and post the output here:

```
sudo fdisk -l
```

---

### Post by chriskin on 2008-07-02
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x623f2f23

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1529    12281661    5  Extended
/dev/sda2   *        1530       13567    96685056    7  HPFS/NTFS
/dev/sda3           13568       14904    10739452+  83  Linux
/dev/sda4           14905       19457    36571972+   b  W95 FAT32
/dev/sda5               1         255     2048224+  82  Linux swap / Solaris
/dev/sda6             256        1529    10233373+  83  Linux
kalampokis@CNB:~$

---

### Post by chriskin on 2008-07-02
problem solved

---

