---
title: "boot loader woes"
date: 2008-05-29
forum: General Help
---

### Post by DThorne on 2008-05-29
I'm trying to get truecrypt to work on my dual boot acer 4720Z laptop.

I've gotten to the point where truecrypt calls boot.ini which loads GRUB but it fails with error 18.

I can still get to the Ubuntu partition by removing the truecrypt bootloader, the system loads GRUB with all of my OS's visible (Ubuntu/XP)

My disk is partitioned into 3 primary partitions (XP 25gb/ Ubuntu swap3gb/ Ubuntu 25gb)and 2 logical drives (25gb ntfs/80 gb FAT32)

I've read [ Combine TrueCrypt bootloader and GRUB]("http://ubuntuforums.org/showthread.php?t=689579") here and tried mrsteveman1's directions but my first partition is ntfs so no luck.  s0larian's directions are (close) to what I did(was done for me) GRUB is on hda0,3

I could really use some guidance on where to go from here, can I fix the GRUB error 18 some how or am I stuck swapping the xp + Ubuntu partitions to put GRUB closer to the start of the drive?

THX 

-M

---

### Post by DThorne on 2008-05-29
wow 53 mins to fall off the front page

---

### Post by DThorne on 2008-05-29
23 min that time

sigh ...

---

### Post by DThorne on 2008-05-29
I guess this isn't a general help kind of problem...

---

