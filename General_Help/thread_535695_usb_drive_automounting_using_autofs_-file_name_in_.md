---
title: "usb drive automounting using autofs -file name in captial letters"
date: 2007-08-26
forum: General Help
---

### Post by lvgandhi on 2007-08-26
I used autofs to mount my usb pendrive to get a specific mount point so that whenever I do sync with unison in linux, I need not change folder name each time.
In /etc/auto.removable, I have
flash   -fstype=vfat,rw,uid=1000,umask=022,posix,shortname=winnt       :/dev/flash
ehd     -fstype=vfat,rw,uid=1000,umask=022,posix,shortname=winnt         :/dev/ehd
for mounting options. In debian etch, with this setup, files with name in all capital letters are copied as  all capital letters names. But in kubuntu, all letters in all capial letterfilenames changed to all lowercase letters. Any solutions? Should I need to give any more info?

---

### Post by eudemus on 2008-03-17
Did you get this solved?
I have this exact same issue.

Is there a way of using a "character set"-based hack?

Cheers
Eudemus

---

### Post by wieman01 on 2008-03-18
> **eudemus said:**
> Did you get this solved?
I have this exact same issue.

Is there a way of using a "character set"-based hack?

Cheers
Eudemus
Check this out:

[http://ubuntuforums.org/showthread.php?t=727331]("http://ubuntuforums.org/showthread.php?t=727331")

---

