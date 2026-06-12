---
title: "file copy from EXT3 to FAT32 problems"
date: 2007-11-07
forum: General Help
---

### Post by pierre2mars on 2007-11-07
Hi,
I have issues on files copying from EXT3 partition to FAT32 external disk:
If the file name is made of caps and nocaps (like FOOtest.txt), it is correctly copied, the name is the same.
BUT if it is all caps (like FOO) it is copied in nocaps (foo)...

It is all the more strange that, if I try to overwrite this copy (foo), in the alert popup, the file name is in caps...
It is done under Konqueror on Kunbuntu gusty.

Does anyone has any idea about what is going on?


regards,

Pierre

---

### Post by mpierce on 2007-11-07
Using gutsy.

I quickly touched footest.txt as user; cp it to my usb 250Gb fat32 HD connected to an XP notebook. I used samba protocol to open the folder on the fat32 drive, e.g., smb://dellbook/F$

The file was fine when checked using konqueror. File permissions were 744 owned by root.root which is normal.

I then cut file and pasted it back in my home dir; file permissions were 744 owned by user.user who created file.

---

### Post by pierre2mars on 2007-11-07
Ok, thanks, and have you tried with caps in the file name? Does it copy correctly, or do you loose caps too?


Pierre

---

### Post by ofb on 2007-11-07
> **pierre2mars said:**
> It is all the more strange that, if I try to overwrite this copy (foo), in the alert popup, the file name is in caps...

Yup, but once you overwrite, or rename, it gets switched to foo or foo1. You're seeing it as FOO in the konq popup because you're still running under EXT3 rules.

Welcome to FAT32 - it's older and just can't do as much as EXT3. The other thing you'll run into is errors when you try to copy files with characters like ':' and '>' in the filename. If you're going to move a lot of files back and forth, you'll have to get into the habit of using the old limits.

IIRC, in Windows Explorer you used to have to change a setting to be allowed to make filenames in all caps. So while you may remember being able to do it, it wasn't a default ability of FAT32.

---

