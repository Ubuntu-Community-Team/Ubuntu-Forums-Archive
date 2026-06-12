---
title: "joint windows/linux access"
date: 2008-05-30
forum: General Help
---

### Post by kam.samji on 2008-05-30
hi i've got a dual boot system with ubuntu and vista (for essential non linux software). It would just be handy to have my music folder easily accessible from whichever system I'm booted into. Can someone advise me how to?

I read somewhere that FAT32 is readable by both OS's, so is it enough to create a folder in FAT32 format and put my music in that?

Thanks,

kam

---

### Post by doorman on 2008-05-30
actually, you should be able to "see" your ntfs partition from ubuntu, so you can put your music there (meaning, on the vista parition)

---

### Post by bla on 2008-05-30
I am new to linux and ubuntu but have read up on this.
Most info on  net is outdated bya decade.

You do not need fat32 for this.  Use NTFS.  There are several drivers for linux.

Also you can use ext3 or ext2 if you wish as XP can read that perfectly once the driver is installed.

I would recommend you hit wikipedia and do some research on partition formats
as the decision is not easy.  I am assuming that you don't want corrupt files... so no FAT32 (primitive and slow).

THE REAL ISSUE is would files get corrupt due to being edited on both windows and linux?
If you have a text or a word file and you edit this file on both systems...say a report that you are working on
over a week...would each os handle and save it in a compatibel way...mark the end of file the same way....etc...
that....is the real issue.  I doubt we'll get an answer for this though as I think few know these things.

---

### Post by housam on 2008-05-30
Ntfs is better than Fat32 and accessible from both systems
[[COLOR="Red"]_this driver_[/COLOR]]("http://www.fs-driver.org/") is allowing you to access ubuntu partitions through windows

---

