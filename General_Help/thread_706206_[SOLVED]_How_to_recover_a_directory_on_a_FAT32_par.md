---
title: "[SOLVED] How to recover a directory on a FAT32 parition?"
date: 2008-02-24
forum: General Help
---

### Post by stephantom on 2008-02-24
Hello everyone,

I've got myself some nice FAT32 file system corruption.
Watch what happens if I try to list the files on that partition:

```
~$ ls
ls: cannot access (directory name here): Input/output error
(correct display of all other files/directories)
```

So I suspect that either me or truecrypt (this is a TC partition) managed to damage something related to that directory entry in the FAT.
I tried using testdisk on the unmounted volume and I am able to browse the files in that particular directory, so they still seem to be there. However, extraction does not seem possible (testdisk does not support that).

As the files are NOT deleted I had no luck with foremost/dls.
I guess what I'd need would be a way to either make the directory reable again or extract the contents of that directory directly from the device file.

I also tried dosfsck, I suggests to unlink all files within that particular directory from the FAT. I don't think I want to be doing that.

Any help on that matter is really really appreciated!

---

### Post by pregister on 2008-02-24
Pretty green myself on ubuntu and linux,however have found super grub to be extremley effective.Simply google super grub.Download ,should fix whatever problem if you just want fat 32 again. Also will get you out of jambs with various linux distros,Unfournately I know this! Have agreat day.
                                                                                pregister

---

### Post by stephantom on 2008-03-29
For reference, the latest version for [testdisk](http://www.cgsecurity.org/wiki/TestDisk_Download) supports copying files from a found partition. It worked for me that way and recovered about three gigabyte of data.

---

