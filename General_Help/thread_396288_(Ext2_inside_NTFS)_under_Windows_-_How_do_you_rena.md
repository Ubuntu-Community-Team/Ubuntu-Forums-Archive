---
title: "(Ext2 inside NTFS) under Windows - How do you rename invalid char?"
date: 2007-03-29
forum: General Help
---

### Post by bluntu on 2007-03-29
I wrote a folder with the name 'ThisIsMyFolder?' (with the question mark at the end) and now I want to copy that folder to another harddrive under Windows and it doesn't allow because NTFS doesn't support the letter '?' in its name.

I don't have access to my Ubuntu at the moment but would like to rename 'ThisIsMyFolder?' to 'ThisIsMyFolder' so I can read it because any file/folder with the '?' in it will appears as an empty file/folder under Windows (NTFS).

---

### Post by taurus on 2007-03-29
Maybe

```
mv  'ThisIsMyFolder?'  ThisIsMyFolder
```

---

### Post by bluntu on 2007-03-29
My HDD is NTFS and I mounted it in Ubuntu and write stuff there. Future version of ntfs-3 should prevents user from typing in ```
\ / : * ? " < >|
``` into their filenames because under Windows you can't access them and that's the problem I'm having right now.

I have tried many ext2 readers for XP and it's pointless because my hdd is actually NTFS (and not Ext2 so these readers bypass). The problem with my hdd NTFS is that there are folders in there that contains invalid chars like the '?' 

I'm not sure if there is a special command for XP but so far I tried 'rename', 'move' and failed.

---

### Post by dcstar on 2007-03-29
> **bluntu said:**
> 
........
I'm not sure if there is a special command for XP but so far I tried 'rename', 'move' and failed.

You will have to use Linux to rename the folders/files.

---

