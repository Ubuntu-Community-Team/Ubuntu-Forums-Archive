---
title: "applications can't find filesystem root .."
date: 2007-04-24
forum: General Help
---

### Post by sveinn on 2007-04-24
Hello, 

After upgrading to Feisty I have the following problem.

When I try to open files from within applications, the applications can't find the filesystem root.

- My home directory shows up

- My Desktop shows up

- My Windows partition shows up twice labeled "26.3 GB Volume" and "windows", respectively. Only "windows" can be opened.

- Two Dell specific partitions show up ("DellRestore" and "DellUtility")

- An icon for Network Connections shows up

- My shortcuts show up

But there is no shortcut to the root of the filesystem as there used to be in Edgy. In its place there is an icon called "dev" which leads to "/dev/.static/dev". 

There are two issues:

- The root to my filesystem has disappeared and been replaced by a shortcut called "dev" leading to "/dev/.static/dev".

- My Windows partition appears twice and only one of the two icons opens up the Windows partition.

Any thoughts?

Sveinn  
 
Attached screenshot of "Open file" dialog.

I have both ntfs-config and ntfs-3g installed.

This is my partition table:

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96358+  de  Dell Utility
/dev/sda2   *          13        3446    27583605    7  HPFS/NTFS
/dev/sda3            9338        9729     3148740   db  CP/M / CTOS / ...
/dev/sda4            3447        9337    47319457+   5  Extended
/dev/sda5            3447        9090    45335367   83  Linux
/dev/sda6            9091        9337     1983996   82  Linux swap / Solaris

Partition table entries are not in disk order

---

### Post by sveinn on 2007-04-29
RESOLVED - reinstalled 7.04 from scratch.

---

### Post by m.musashi on 2007-04-29
That is usually my solution too. If you put your /home on its own partition you can reinstall a lot easier (although I would still make sure important files are backed up).

---

