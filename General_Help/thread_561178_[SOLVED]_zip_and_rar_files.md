---
title: "[SOLVED] zip and rar files"
date: 2007-09-27
forum: General Help
---

### Post by d_iane1954 on 2007-09-27
i do know that the archive manager handles rar and zip files but what i need to know is when sending theses files to a thumb drive after un-zipping them is there a way in fiesty fawn to format the thumb drive first before sending the file to fat-32 format?thanks for all replys its great having this form as a service in getting questions answered! thanks!!!!!!!!!!!!!!

---

### Post by notwen on 2007-09-27
Linux has no issues reading/writing to a FAT32 file system.  What issues are you having w/ your archives relating to your thumb drive?

---

### Post by madoracle on 2007-09-27
You could just format it yourself before moving the folder(s), otherwise you could write a simple bash script to first format the drive and then cp <file> <drive>

---

### Post by d_iane1954 on 2007-09-27
the formatting of the thumb drive,i was wondering how you do this in ubuntu in windows you right click the drive and the formatting option is there,in ubuntu i am lost as to how to accomplish this formatting procedure?thanks to you people for your speedy replys!!!!!!!!

---

### Post by madoracle on 2007-09-27
Your search-fu is weak.

[http://ubuntuforums.org/showthread.php?t=296219](http://ubuntuforums.org/showthread.php?t=296219)

The above thread on this forum answers this question in about six different ways. Enjoy.

---

### Post by notwen on 2007-09-27
I would recommend formatting the USB drive and using the FAT32 file system as it is readable/writable from both Windows and Linux.

---

