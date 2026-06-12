---
title: "Data recovery tool recommendations please."
date: 2013-08-30
forum: General Help
---

### Post by Paul_Stinerck on 2013-08-30
Some weeks ago I moved some data from my Ubuntu 11.10 box to my Mint 14 box. I used a pendrive (small usb drive)  to do so and my method was copy-paste to the pendrive from the Ubuntu 11.10 box and cut paste to the Mint 14 box from the pendrive. Now, this was the first phase of project to synchronise my key documents and make them availabe from both machines. This had a small failure  which resulted in a series of files being lost from both computers, which was compounded by a backup issue.

Now today it has occured to me that there may be a way to get the files back from the usb drive that was used during the transportation of the files between boxes. I am basically looking for recomendations from the community as to a suitable tool for going into the usb drive and digging around in what is left after the cut operation.

If anyone can recommend a tool or application that can do this then I will be very happy. I do not have it with me as I write, but I think the usb pendrive was formatted to the format of Linux, not the NTFS format. When I can I will confirm this.

So please, if anyone can make a recommendation I will be very obliged.

Thank you.

---

### Post by Paul_Stinerck on 2013-08-30
As no one has answered I will answr er myself
- Tried foremost. This does not find any of the deleted files
- Tried extundelete. This does not really function as described here [http://extundelete.sourceforge.net/](http://extundelete.sourceforge.net/)

There is no implicit critiscism of either product. It took me over a month to notice I had lost my data, and all this time I was using the USB

---

### Post by dragonfly41 on 2013-08-30
I would recommend testdisk ...

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

You might read some cases in the testdisk forum to get an idea of usage.

testdiskcan be installed via Ubuntu Software Centre but better to download the latest version.

---

### Post by Paul_Stinerck on 2013-08-30
Oh, I thought I had this USB drive partitioned to ext4 but it is NTFS. This explains why foremost & extundelete did not work.

---

### Post by Paul_Stinerck on 2013-08-30
Hello Dragonfly. I have looked at TestDisk, but I cannot see that it is for my circumstances which is to look for files that I cut <ctrl><x> perfectly legally about a month ago. From what I can see, TestDisk is about attemping to recover data from a damaged or corrupted media. Maybe I haven't understood it properly. Basically because I have lost some backups, and I know that the files were temporarily on this pendrive, I am looking to have a look around the pendrive. But apart from that the pendrive is not broken or corrupted in any way.

Thanks for the recommendation though.

---

### Post by Paul_Stinerck on 2013-08-30
This is now solved. Does anyone know how you add the [SOLVED] tag to a post? I have looked everywhere for instructions.

Reason for solution - I have now found a valid backup and there is no need for data recovery.

---

### Post by Paul_Stinerck on 2013-08-30
Solved. No need for data recovery

---

### Post by dragonfly41 on 2013-08-30
<ctrl>+<x> or "cut" is simply "copy to clip board & then delete".

Testdisk would have recovered cut files .. provided that the drive had not been used in the interim for writing new files. 
Might be worth experimenting on your pen drive for future reference.

More here .. [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

To mark thread as solved go to "thread tools".

---

