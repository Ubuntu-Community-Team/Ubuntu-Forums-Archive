---
title: "remove grub"
date: 2006-11-07
forum: General Help
---

### Post by Green_Star on 2006-11-07
Hi all,

I installed ubuntu in my laptop, dual boot with xp. Now I got a new desktop, so i installed with ubuntu in that. now i want to remove ubuntu from my laptop, because i really want that 10gb ubuntu space for xp. now i am little afraid to format that ubuntu partition because i am not sure where grub is loaded. if it is loaded in ubuntu partition then i can not boot xp after formating ubuntu. can some one please help me how i can know where grub is loaded and how can i completely remove grub and ubuntu from my laptop. i can paste screenshot of required information if you need any... i am still learner to linux, so please explain in detail with commands.

thanks in advance.

---

### Post by dbott67 on 2006-11-07
Boot from your Windows XP CD and select 'Recovery Console'.

From the command line type:
```
fixmbr
```

This will repair the master boot record for Windows

---

### Post by Green_Star on 2006-11-08
Thanks dbott67.

---

### Post by dbott67 on 2006-11-08
You're welcome.

-Dave

---

### Post by cyberkid9839 on 2006-11-09
> **dbott67 said:**
> Boot from your Windows XP CD and select 'Recovery Console'.

From the command line type:
```
fixmbr
```

This will repair the master boot record for Windows

Hi dbott67,
did you mean that I delete the partitions first and then use Windows XP CD to fix the master boot record?
Thanks!
--cyberkid9839

---

### Post by dbott67 on 2006-11-09
You don't have to delete the partition first.  After running 'fixmbr' your computer will only boot into Windows.  From there, you could go into Disk Administration and delete the ext3 partition.  With the new empty space, you can create a new partition (NTFS, FAT32, etc) to store data, etc.

-Dave

---

### Post by henk_z on 2006-11-13
Hello, i also want to remove GRUB from my system but i only have Windows CDs for my laptop. These are preprogrammed Windows disks for my configuration so i can only use the recovery disc for reinstalling the Windows 'image' that has been provided for my laptop (and it's settings). Is there another way to remove the GRUB loader?

---

### Post by dbott67 on 2006-11-13
If you still have a 3.5" floppy drive, you can make a Windows boot disk (in Windows, right-click 3.5" A: drive & select 'Format'.  Then place a check in 'Create MS-DOS startup disk').

The one thing I'm not sure of is whether or not the 'fixmbr' is copied to the floppy.

Anyhow, boot off of the floppy and type:
```
fixmbr
```

Note: fixmbr may be part of command.com (much like the commands dir, copy, etc.) or you may have to search for it & copy it over.  You could also use the program fdisk --- the command would be 'fdisk /mbr')

-Dave

---

### Post by henk_z on 2006-11-13
Thank you. It worked for me with the 'fdisk /mbr' command.

---

### Post by dbott67 on 2006-11-13
Great! :)

-Dave

---

### Post by VividHazE on 2006-12-04
Hey Guys,

I'm in the same position where I want to remove GRUB, but I have an image Windows CD, not real XP CD for my Laptop, and I don't have a Floppy Drive, is there any other way to remove GRUB?

---

### Post by Infiltraitor on 2006-12-04
So that "fdisk /mbr" thing worked with that floppy disc?

---

### Post by dbott67 on 2006-12-04
> **VividHazE said:**
> Hey Guys,

I'm in the same position where I want to remove GRUB, but I have an image Windows CD, not real XP CD for my Laptop, and I don't have a Floppy Drive, is there any other way to remove GRUB?

Can you beg/borrow/burn a copy from a friend?  As long as you don't use their key, you're not violating any copyright laws.

---

