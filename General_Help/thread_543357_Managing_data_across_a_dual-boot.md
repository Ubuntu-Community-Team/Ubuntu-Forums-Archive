---
title: "Managing data across a dual-boot"
date: 2007-09-05
forum: General Help
---

### Post by DishBreak on 2007-09-05
My computer has 3 partitions:[LIST]
[*]1 EXT3 for Ubuntu
[*]1 NTFS for XP
[*]1 FAT32 for my data
[/LIST]

I recently started using evolution in both OS's to manage my personal data. I was wondering if anybody knew an easy way to share the data between the two Evolution programs without constantly importing/exporting. 

Also, I use Illustrator and Photoshop CS3, and let's just say I don't have the install CDs for them, so I can't do it on wine. I do, however, have a valid install CD for XP. Is it worth my while to ditch the dual-boot altogether and use a virtual machine within Ubuntu? I don't use XP for any hardware specifically.

---

### Post by softtower on 2007-09-05
Do your research and find out where Evolution stores your data. Perhaps it is even configurable. I use web-based gmail/calendar so I don't have those problems. Once you find where Evolution data is stored, you can configure Windows and Linux instances of it to point to the same location, although it may be dangerous. Not always Win/Linux versions of the same software are binary compatible. I probably would back things up.

However, you would need to convert FAT32 to NTFS and use ntfs-3g. I am not sure if this solution will work fine with FAT32 partition.

Graphics will be dog slow under VMWare. I would not use Photoshop under VMware although I have not tried. I use 2nd PC with XP on it for photoshop work.

---

### Post by somedamfool on 2007-09-05
Dishbreak,
Most any Windows app that is self contained (all required files are in the apps folder and subfolders), will run under wine just by copying the folder (s) to your Linux drive and making a shortcut to the exe file. The exception is applications that install files all over Windows, eg in Windows, Windows/System32, etc.

Softtower is right; NTFS will give you a lot less problems than Fat32. Also check out Gimp. It has a steep learning curve but there is nothing you can do in photoshop that you can't do in Gimp.

---

### Post by DishBreak on 2007-09-05
Thanks a lot for your responses.

I have been a GIMP user for awhile, and i use it whenever i'm in ubuntu. That will not change, of course.

I'll probably not mess with the contacts/calendar, and try syncing through google calendar or something of that nature. 

Good call on the virtual machine. I'll stay away from that.

thanks, and cheers!

---

