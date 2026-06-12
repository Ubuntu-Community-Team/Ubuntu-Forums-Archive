---
title: "Grub 15 error"
date: 2008-05-30
forum: General Help
---

### Post by illbashu on 2008-05-30
i restarted my comp and i got this error, tell me there is a way i can get it back up and running i have like 40gb of media files that i dont want to loose! :(

btw my cd drive craped out on me resantly so i dont have a cd drive, i still have a floppy and i should be getting a cd drive soon though...

but i dont have floppy on any other comps :(

just tell me what i sould do and i will do it when i get a cd-drive.

---

### Post by quelx on 2008-05-30
[http://ubuntuforums.org/showthread.php?t=811442&highlight=error+15](http://ubuntuforums.org/showthread.php?t=811442&highlight=error+15)

---

### Post by illbashu on 2008-05-30
will this do the trick?
```
Backup, Repairing and Reinstalling GRUB

To make a backup a copy of the existing menu.lst file use: 

cp /boot/grub/menu.lst /boot/grub/menu.lst.old 

You can try re-installing the grub using the Ubuntu Live CD, in two different ways. 
GUI

Boot your computer up with Ubuntu CD 

Go through all the process until you reach "[!!!] Disk Partition" 

Select Manual Partition 

Mount your appropriate linux partions 
 /
 /boot
 swap
 ..... 

DO NOT FORMAT THEM. 

Finish the manual partition 

Say "Yes" when it asks you to save the changes 

It will give you errors saying that "the system couldn't install ....." after that 

Ignore them, keep select "continue" until you get back to the Ubuntu installation menu 

Jump to "Install Grub ...." 

Once it is finished, just restart your computer
```

---

### Post by quelx on 2008-05-30
that should do it, but like it says make sure you

> **DO NOT FORMAT THEM.**

---

### Post by wolfen69 on 2008-05-30
just remember, in a pinch you can always put in a live cd and save stuff to a flash drive or whatever.

---

