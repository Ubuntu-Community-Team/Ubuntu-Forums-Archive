---
title: "NTFS Filename Restrictions"
date: 2015-06-06
forum: General Help
---

### Post by gr8 on 2015-06-06
I formatted my external hard drive as NTFS so it'll work on Ubuntu and Windows. What are the filename restrictions I need to be aware of?

---

### Post by Bucky Ball on 2015-06-06
Try Wikipedia> Filenames> Comparison of filename limitations> NTFS.

---

### Post by oldfred on 2015-06-06
Info on mounting partitions:

 [https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)


Important part of above:

 For ntfs UUID shown is example only see below:
UUID=XXXXXXXXXXX   /media/WinD ntfs defaults,nls=utf8,umask=000,uid=1000,windows_names 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20) 
uid=1000 should fix the trash problems as well:

---

