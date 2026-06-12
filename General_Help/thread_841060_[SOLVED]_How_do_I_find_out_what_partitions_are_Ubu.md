---
title: "[SOLVED] How do I find out what partitions are Ubuntu and which are Vista?"
date: 2008-06-26
forum: General Help
---

### Post by S3loth on 2008-06-26
I'm having to reinstall Ubuntu because it is a mess (right now I'm having to use a live CD). My question is how can I know which ones to tell Ubuntu to over right and make sure that I don't touch Vista at all.

---

### Post by iaculallad on 2008-06-26
> **S3loth said:**
> I'm having to reinstall Ubuntu because it is a mess (right now I'm having to use a live CD). My question is how can I know which ones to tell Ubuntu to over right and make sure that I don't touch Vista at all.

Open your terminal and issue the command below: 

```
fdisk -l
```

or if that does not work, include sudo (that small letter L in "l")

```
sudo fdisk -l
```

Output can be like this:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         124      995998+  82  Linux swap / Solaris
/dev/sda2            2551        9729    57665317+   7  HPFS/NTFS
/dev/sda3   *         125         914     6345675   83  Linux
/dev/sda4             915        2550    13141170   83  Linux

```

HPFS/NTFS means you have your vista partitions.

---

### Post by S3loth on 2008-06-26
Ok, so I tell Ubuntu to overwrite everything except the HPFS/NTFS. btw here's the print out.

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18457   148255821    7  HPFS/NTFS
/dev/sda2           18458       29255    86734935   83  Linux
/dev/sda3           29585       30401     6554520    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           29256       29584     2642692+   5  Extended
/dev/sda5           29256       29584     2642661   82  Linux swap / Solaris

---

### Post by iaculallad on 2008-06-26
> **S3loth said:**
> Ok, so I tell Ubuntu to overwrite everything except the HPFS/NTFS. btw here's the print out.

 Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18457   148255821    7  HPFS/NTFS
/dev/sda2           18458       29255    86734935   83  Linux
/dev/sda3           29585       30401     6554520    7  HPFS/NTFS
Partition 3 does not end on cylinder boundary.
/dev/sda4           29256       29584     2642692+   5  Extended
/dev/sda5           29256       29584     2642661   82  Linux swap / Solaris

Do you choose the option of loading an OS on vista menu?

---

### Post by S3loth on 2008-06-26
I pick it between Ubuntu and Vista on the GRUB menu

---

### Post by iaculallad on 2008-06-26
Just to be safe, try to browse the /dev/sda1 and /dev/sda3 partitions using your LiveCD. Look for anything that points to your vista OS (such as Program Files, Documents and Settings, or Windows folder) then that would be your vista drive, otherwise, that could be your data drive since you got 2 NTFS partitions.

When you're sure that you located your vista partition, then, start your Ubuntu installation w/o touching vista's. 

*You might be needing supergrub later*

---

