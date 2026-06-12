---
title: "Renaming hard Drives"
date: 2007-01-10
forum: General Help
---

### Post by Imsati on 2007-01-10
Hello everyone. I've always been able to rename my Hanrd drives on my secondary disk (with XP). Now, however, they're reverted back to hdb1/2/3. Before the partitions were labeled 'XP OS', "XP Software', and 'Jason'. I've tried changing them back, but for some reason it won't accept the changes.

Also, when I open Storage Media, I no longer see 'Root' and 'Home'. I don't think I changed any settings, but I may have inadvertently. How do I go about being able to see Root and Home again, as well as change my other partition names?

Thanks a bunch!

Jay

---

### Post by sleeper414 on 2008-01-28
hi, im  having the same problem.
im kind of surprised...in XP, which sucks compared to ubuntu its simple.
go figure.

go to youtube and type relabel hard drice ubuntu.

maybe that will help....

---

### Post by noynac on 2008-01-28
The utility ntfslabel might be of help. It's part of ntfsprogs and is in the repo's. The purpose of this utility is to "display/change the label on an ntfs file system." The man page is at:

[http://man.linux-ntfs.org/ntfslabel.8.html](http://man.linux-ntfs.org/ntfslabel.8.html) 

I've used this utility on external hard drives with success. Messing around with partitions on a dual boot is always a bit risky, so proceed at your own risk. 

The following howto deals with USB drives, but it also might be of help:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by bodhi.zazen on 2008-01-29
See this thread : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

In the first (long) post, scroll down to the "how to label" section ;)

---

