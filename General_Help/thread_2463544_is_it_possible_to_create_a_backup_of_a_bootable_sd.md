---
title: "is it possible to create a backup of a bootable sd card that will fit smaller cards?"
date: 2021-06-13
forum: General Help
---

### Post by rebeltaz on 2021-06-13
What I mean is, I have a couple of servers running raspberry pis. I need to be able to create backups of their SD cards (using my Ubuntu laptop - hence my posting here). The problem is that not all SD cards are created equal. I have created backups in the past using dd, but then, if the target card happens to be a few bytes smaller, dd refuses to perform the restore operation. What I need is a way to backup the card, retaining it's bootability, and I guess ignoring any empty sectors, reducing the size of the image, so that if I need to install that image on a card that isn't byte for byte exact, it'll work.

---

### Post by Impavidus on 2021-06-14
Leave unallocated space at the end of the sd card, so that the allocated part is not larger than the smallest card. dd can be instructed to copy a certain number of bytes instead of the whole device.

---

### Post by sudodus on 2021-06-14
Another method is to use [**Clonezilla**](https://clonezilla.org) to create a compressed image (not a clone). This image can be expected to be much smaller than the original card size, but when you restore it, you must have a card that is at least as big as the original one unless you use the method explained by Impavidus in the previous post (to leave some unallocated drive space near the tail end of the drive. For example, I often use 7.8 GB on a card which is nominally 8 GB).

This would work both with direct cloning and when restoring from a compressed image, when there is an MSDOS partition table. But if there is a GUID partition table, GPT, you must also repair the backup partition table, that should be at the tail end of the drive. You can do that with [SIZE=3][FONT=Courier New]**gdisk**[/FONT][/SIZE], or easier with the shellscript [**gpt-fix**](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix).

---

### Post by rebeltaz on 2021-08-08
> **Impavidus said:**
> Leave unallocated space at the end of the sd card, so that the allocated part is not larger than the smallest card. dd can be instructed to copy a certain number of bytes instead of the whole device.

> **sudodus said:**
> Another method is to use [**Clonezilla**](https://clonezilla.org) to create a compressed image (not a clone). This image can be expected to be much smaller than the original card size, but when you restore it, you must have a card that is at least as big as the original one unless you use the method explained by Impavidus in the previous post (to leave some unallocated drive space near the tail end of the drive. For example, I often use 7.8 GB on a card which is nominally 8 GB).

This would work both with direct cloning and when restoring from a compressed image, when there is an MSDOS partition table. But if there is a GUID partition table, GPT, you must also repair the backup partition table, that should be at the tail end of the drive. You can do that with [SIZE=3][FONT=Courier New]**gdisk**[/FONT][/SIZE], or easier with the shellscript [**gpt-fix**](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative#gpt-fix).

I am sorry. I never got any notification that this was replied to. 

So what y'all are saying is to create the partition slightly smaller than the card size? I guess I could use gparted to slightly shrink a current partition for this to work, right? 

Thank you both. I appreciate the help!

---

### Post by TheFu on 2021-08-08
**fsarchiver** is another tool that can restore to smaller disks, with a few caveats.
I always found clonezilla much to complicated.

---

### Post by monkeybrain20122 on 2021-08-08
fsarchiver.  Clonezella requires the target to be at least as big as the source even though the source may be mostly empty. [https://www.fsarchiver.org/](https://www.fsarchiver.org/)

---

### Post by rebeltaz on 2021-08-08
> **TheFu said:**
> **fsarchiver** is another tool that can restore to smaller disks, with a few caveats.
I always found clonezilla much to complicated.

> **monkeybrain20122 said:**
> fsarchiver.  Clonezella requires the target to be at least as big as the source even though the source may be mostly empty. [https://www.fsarchiver.org/](https://www.fsarchiver.org/)

Awesome. I will read up on that. Thanks!

---

