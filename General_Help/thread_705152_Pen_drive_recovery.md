---
title: "Pen drive recovery"
date: 2008-02-23
forum: General Help
---

### Post by Tony_photoplus on 2008-02-23
Can anyone help.  I have a pen drive that I can't access and am looking for a free recovery software as I have important data on there.  So much for ensuring I have backup and the back up has gone.

Tony_photoplus

---

### Post by julian67 on 2008-02-26
You can try [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")

> PhotoRec is file data recovery software designed to recover lost files including video, documents and archives from Hard Disks and CDRom and lost pictures (thus, its 'Photo Recovery' name) from digital camera memory. PhotoRec ignores the filesystem and goes after the underlying data, so it will still work even if your media's filesystem has been severely damaged or re-formatted.

PhotoRec is free, this open source multi-platform application is distributed under GNU Public License. PhotoRec is a companion program to TestDisk, an app for recovering lost partitions on a wide variety of filesystems and making non-bootable disks bootable again. You can download them from this link.

For more safety, PhotoRec uses read-only access to handle the drive or memory support you are about to recover lost data from. Important: As soon as a pic or file is accidentally deleted, or you discover any missing, do NOT save any more pics or files to that memory device or hard disk drive; otherwise you may overwrite your lost data. This means that even using PhotoRec, you must not choose to write the recovered files to the same partition they were stored on..... 


......Photorec ignores the filesystem, this way it works even if the filesystem is severely damaged.
It can recover lost files at least from

    * FAT,
    * NTFS,
    * EXT2/EXT3 filesystem
    * HFS+ 

It works on all kinds of flash memory too:

> PhotoRec works with HardDisks, Cdrom, Compact Flash, Memory Stick, SecureDigital, SmartMedia, Microdrive, MMC, USB Memory Drives, DD raw image, EnCase E01 image...

---

### Post by az on 2008-02-26
> **Tony_photoplus said:**
> Can anyone help.  I have a pen drive that I can't access and am looking for a free recovery software as I have important data on there.  

[http://help.ubuntu.com/DataRecovery](http://help.ubuntu.com/DataRecovery)

Photorec is fine, but it sometimes is easier to image the device first and then data carve the files out from there.

First off, though, what happens when you plug in the drive?  What errors show up?  Open up the log tool, and check out /var/log/messages.  What is displayed when you plug in the device?  Post the output.

> **Tony_photoplus said:**
> 
So much for ensuring I have backup and the back up has gone.

Tony_photoplus

You backed something onto the pen drive, deleted it from the original source and the pen drive died?  It may be possible to recover some if not all of the data from the original source.  Post some details.

---

### Post by julian67 on 2008-02-26
> **az said:**
> [http://help.ubuntu.com/DataRecovery](http://help.ubuntu.com/DataRecovery)


links to dead/empty page

this one works [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

