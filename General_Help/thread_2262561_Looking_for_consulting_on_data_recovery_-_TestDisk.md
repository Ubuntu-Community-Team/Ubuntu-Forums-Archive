---
title: "Looking for consulting on data recovery - TestDisk, PhotoRec"
date: 2015-01-25
forum: General Help
---

### Post by chad_b2 on 2015-01-25
Hello All,

I'm looking for active help in recovery of a (former) Ubuntu installation on a Samsung 1TB HDD with four partitions - three as ext4 w/ one containing Ubuntu OS, fourth as swap space. Due to irresolvable Java issues, I attempted to install Linux Lite from a LiveUSB to the partition containing the Ubuntu distro, so as to overwrite only that partition, but misinterpretation of wording in the wizard (which appears to be a change of wording within the last few releases of Ubuntu) caused me to proceed to format the entire drive, removing all partitions. I haven't installed any other software or moved data to the drive since; I understand that some data is lost due to the LL install.

I made brief attempt using Ubuntu Rescue Remix on liveUSB (Testdisk, Photorec) to copy disk image to another drive...mostly, can't figure out how to set the destination drive to anything other than the liveUSB (I've got a 1TB USB external HDD intended for destination). That is, the screen of PhotoRec like seen here (taken from [http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2):](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_ext2):)
[IMG]http://www.cgsecurity.org/mw/images/Ext2_undelete_copy.png[/IMG]

...I don't see where to navigate to a separate drive.

Also, certain files sought for recovery on drive have formats that are not recognized by Photorec by default - .nxc, .odw, .ods, (etc..)

Worst case, I may resort to GRC's SpinRite software which claims to work with Linux fine, although I'm sure the building blocks of such are similar to or based on TestDisk/DDRescue/other.


Any advice/help is greatly appreciated.

---

### Post by tgalati4 on 2015-01-25
First use *testdisk* to repair the partition and file directory table.  If this is successful, then you are done.  You should then be able to navigate to all your folders and then backup up your important files using Nautilus to drag and drop to your external drive.

If *testdisk* fails, then you have no other option but to use *photorec* to recover individual files--with useless names and 500 files to a directory.  And yes, all of those strange formats will get set to *.txt, but many will get recognized, so don't sweat it.

To specifiy a recovery directory, use the /d switch with *photorec*:

```
man photorec
```

---

