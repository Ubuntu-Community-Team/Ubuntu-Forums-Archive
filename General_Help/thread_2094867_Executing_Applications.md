---
title: "Executing Applications"
date: 2012-12-15
forum: General Help
---

### Post by MTariq on 2012-12-15
I want to execute an application i.e. android emulator in a non-system drive i.e. /media/ubuntu/Data where drive name is Data.

Is there any way to do that?
I tried to change the permission by using the following command

sudo chmod 777 emulator

but the permission is still not changing. It is still in read/ write only mode.

---

### Post by bhaveshnande on 2012-12-15
Linux file permissions won't work if your USB is formatted to FAT32 or NTFS.
In such a case this might help you :)

[http://askubuntu.com/questions/49392/how-to-mark-allow-executing-file-as-program-on-an-external-drive](http://askubuntu.com/questions/49392/how-to-mark-allow-executing-file-as-program-on-an-external-drive)

---

