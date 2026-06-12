---
title: "Pen drive doesn't show up after trying to format it :("
date: 2008-01-12
forum: General Help
---

### Post by Ripfox on 2008-01-12
Erm, I don't quite have much experience with this pen drive formatting stuff, I finally bought a 2 gig thumbdrive and tried to format it to fat32...now all that shows up when I plug it in is U3System on my desktop. I tried to format it to ext3 first thinking that would get rid of U3...heheheh, RIGHT. I tried to use wine to uninstall U3. It said no device found (but it ran the uninstaller!)

Any help here please *ugh*

---

### Post by Ripfox on 2008-01-12
NM I rebooted and it's there...but is there ANY way to uninstall this freakin U3 crap without a windows box?? :confused:

---

### Post by twright on 2008-01-12
in gparted when the usb stick is selected, click device and click set device label then select msdos

that will wipe all of the U3 stuff off the disk, then you can format it to ext3 :)

---

### Post by avik on 2008-01-12
> **twright said:**
> that will wipe all of the U3 stuff off the disk, then you can format it to ext3 :)

Just plain reformat it in gparted (you might have to install it, and you'll find it under System->Administration->Partition Editor.

Format it to FAT32.  Ext3 isn't readable by a Windows machine without some workarounds.  FAT32 is pretty much guaranteed to work anywhere.

---

### Post by Ripfox on 2008-01-15
Formatting it to fat 32 does NOT erase the U3 stuff.

---

### Post by twright on 2008-01-16
set disklabel will totally remove the u3 stuff

---

### Post by Ripfox on 2008-01-16
Well at this point, gparted just spins it's wheels even with the disk unmounted. I haven't been able to make gparted work worth a crap for awhile now...:(

---

### Post by warrior24 on 2008-01-16
I am having a similar problem formated my 512 to ext3 but it wont show up any more not even in gparted.

---

### Post by Ripfox on 2008-01-17
Setting Disk Label did not destroy U3. I followed your advice to the letter.

Anyone else?

---

### Post by twright on 2008-01-18
if that won't do it nothing will except windows, it looks like it is locked on

---

