---
title: "Best file system to use between Linux, Windows and OSX."
date: 2018-10-02
forum: General Help
---

### Post by 1488-based on 2018-10-02
May i know what the best file system is to use for an external hard drive (3TB) that I can safely use between Linux, Windows and OSX?

Linux is what i mainly use on my computers but sometimes I may need to connect to Windows and Apple.

The drive has nothing but Blu-Ray copies on it that are about 40Gb to 60Gb each file. The files are all .mkv files.

---

### Post by SagaciousKJB on 2018-10-02
I would use NTFS.  You can mount the drive read-only in OSX, or install NTFS-3g if you want write support--but it sounds like you just want to watch your movies.  Meanwhile, Windows and Ubuntu will support full read/write access by default.

HFS+ would be another option as its the native file system for OSX, but you'd need to install 3rd party software on both Ubuntu and Windows to use it, and I can't say how great the support for either is.

NTFS is a pretty matured file system, has a lot of support and will allow you to use large files like that.  I'm guessing you're already aware of the 4GB file-size limitation of FAT32

---

### Post by 1488-based on 2018-10-02
Cheers for that. I was aware if the file size limit with FAT32 so I tried exFAT but found it was more trouble than it was worth.

I will go with NTFS.

Cheers.

---

