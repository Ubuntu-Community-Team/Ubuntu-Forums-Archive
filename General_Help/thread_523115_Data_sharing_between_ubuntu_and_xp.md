---
title: "Data sharing between ubuntu and xp"
date: 2007-08-11
forum: General Help
---

### Post by Mysterchr on 2007-08-11
Does anyone know what the differences between using FAT32 or ext2 or ext3 are???

---

### Post by apetresc on 2007-08-11
Yes, there are a lot.

ext3 is journalled, meaning it is much less vulnerable to data loss than FAT32 in the case of things like power outages
fat32 has some stupid limitations, like no file may be greater than 4GB in size (bad for DVD images)
fat32 does not support basic features like symlink
ext3 is faster
Many more, but almost all of them are bad for FAT32.

In short: USE EXT3. There is no good reason to use FAT32 over Ext3 for a shared partition now that the windows ext3 driver exists: [www.fs-driver.org/](www.fs-driver.org/)

---

### Post by Scunizi on 2007-08-11
Fat32 is a somewhat universal format that can be used by windows, linux and I think mac.  It does have file size limitations in windows to about 4 gig.  ext3 is ext2 with journaling giving you better performance in regards to data safety.  If you're running a dual boot machine and using an external HD, I format with ext3 which linux can read natively.  On XP you'll have to load/install an ext3 driver for access.  Once done though, it's as seemless at ntfs or fat32.

---

### Post by Mysterchr on 2007-08-11
So ext3 is the best to be able to save files that can be accessed from both OS'S correct...?

---

### Post by apetresc on 2007-08-11
> **Mysterchr said:**
> So ext3 is the best to be able to save files that can be accessed from both OS'S correct...?

Correct. Linux can read/write ext3 natively by default, and for Windows all you have to do is install the program I linked to in my first post, and it will do the same.

It will work flawlessly :)

---

### Post by Mysterchr on 2007-08-11
even for future installations of other OS?

---

### Post by apetresc on 2007-08-11
> **Mysterchr said:**
> even for future installations of other OS?
Yes. Any OS, future or present, that can read ext3 (that's all of them) will be able to access that partition fully.

---

### Post by Scunizi on 2007-08-11
Yep.. The only draw back would be if you were to take an external drive to a friends.  You'll have to install the driver for ext3 on his windows system.

---

### Post by Mysterchr on 2007-08-11
I'm sorry I know this continous posting must get annoying I just don't want to screw my system up...but the link you added sent me to the drivers for ext2 I thought I needed the ones for ext3???

---

### Post by apetresc on 2007-08-11
> **Mysterchr said:**
> I'm sorry I know this continous posting must get annoying I just don't want to screw my system up...but the link you added sent me to the drivers for ext2 I thought I needed the ones for ext3???

It will work just fine. Ext2 is forwards-compatible with ext3. The only difference is a journal at the head of the partition.

Short version: That driver supports ext3 just fine.

But I totally understand your caution before making a big change, and it's a good thing :)

---

### Post by merlinus on 2007-08-11
It works on both ext2 and ext3 with no problems.

-merlin

---

### Post by Mysterchr on 2007-08-11
Well thanks a lot man you've been a lot of help.

---

### Post by Bheegerji on 2007-11-01
> **Scunizi said:**
> Yep.. The only draw back would be if you were to take an external drive to a friends.  You'll have to install the driver for ext3 on his windows system.


Then what happens if files on a Linux system (ext3 formatted) are copied onto a pen drive or burnt on a dvd or cd  and accessed on a NTFS formatted Windows system? Will the Windows system be able to access these contents?

---

### Post by eldragon on 2007-11-01
only the file gets copied.....not the medium where it lies...
the filesystem only tells the operating system how things are stored. :)


so. if you copy my_doc.odf to a pendrive, every computer that can read that pendrive will be able to access my_doc.odf

hope its clear enough.

back when i did dualboot, i installed the driver in question in winxp to be able to access my shared data partition (ext3) between linux and ubuntu (i even had my thunderbird/firefox profiles there), so no matter where i was, i could read my mail and have my bookmarks / extensions in firefox :) 
i didnt trust ntfs writing in linux :D

---

