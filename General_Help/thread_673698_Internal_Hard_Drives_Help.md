---
title: "Internal Hard Drives Help"
date: 2008-01-20
forum: General Help
---

### Post by alexscott on 2008-01-20
So I've got my Ubuntu install on one hard drive, and two other hard drives which appear to be missing.  They're not in computer and I have no idea how I would access them. They weren't there when I installed Linux, because i swapped them out for a CD drive.  How can I get my hard drives to show up? Or mount them?
Thanks!

---

### Post by banewman on 2008-01-20
can you open a terminal and type ```
fdisk -l
``` and post the output here?
It will tell if the drives are seen by the os and what we need to do to mount them
:)

---

### Post by alexscott on 2008-01-20
Disk /dev/sdd: 1009 MB, 1009254400 bytes
64 heads, 32 sectors/track, 962 cylinders
Units = cylinders of 2048 * 512 = 1048576 bytes
Disk identifier: 0x2b0be047

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         963      985328    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(776, 63, 32) logical=(962, 15, 32)

---

### Post by FrankVdb on 2008-01-21
There are two steps. First you have to identify your drives, then you have to add them to fstab.

sudo lshw will show all your hardware, including your hard drives and their specs

Then you will have to enter your hard drives into your fstab file, so that they are recognised and mounted at start-up.

gedit /etc/fstab

Have a look at the how your root drive is mentioned in fstab and enter your other drives accordingly.

---

### Post by alexscott on 2008-01-21
Could you give a little more detail...I'm a little new to this.  Plus I can't save the Fstab file, it tells me I don't have permissions :S

---

