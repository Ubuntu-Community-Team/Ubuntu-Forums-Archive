---
title: "[SOLVED] where does nautilus get partition names from? trying to change"
date: 2007-11-08
forum: General Help
---

### Post by jay767 on 2007-11-08
Hi, i use the disk mounter application in my toolbar quite a bit, at first just to mount/open/unmount an ntfs partition. I recently snipped off 30 gb at the end of my / partition for use as a separate /home folder and divided the 200 gb left in half and installed Debian.

The only one of the three partitions to have a name is the ntfs partition, which had been named when it was in use as a second drive in windows. The 30 gb partition has a mount point /media/home and functions normally, but the diskmounter calls it "30.0 GB Volume (mounted)" and Places->Computer calls it "30 GB Volume:home" (apparently partition name:mount point?)

How can I change "30 GB Volume" to home and "100 GB Volume" to debian? I've tried changed the names in the file browser but apparently can't even as root. The drives have no label in fstab (in fact the 100 GB isn't listed there at all since I don't want it to mount automatically). It *IS* possible to change the partition's labels isn't it?

---

### Post by dcstar on 2007-11-08
> **jay767 said:**
> Hi, i use the disk mounter application in my toolbar quite a bit, at first just to mount/open/unmount an ntfs partition. I recently snipped off 30 gb at the end of my / partition for use as a separate /home folder and divided the 200 gb left in half and installed Debian.

The only one of the three partitions to have a name is the ntfs partition, which had been named when it was in use as a second drive in windows. The 30 gb partition has a mount point /media/home and functions normally, but the diskmounter calls it "30.0 GB Volume (mounted)" and Places->Computer calls it "30 GB Volume:home" (apparently partition name:mount point?)

How can I change "30 GB Volume" to home and "100 GB Volume" to debian? I've tried changed the names in the file browser but apparently can't even as root. The drives have no label in fstab (in fact the 100 GB isn't listed there at all since I don't want it to mount automatically). It *IS* possible to change the partition's labels isn't it?

```
man e2label
```

---

### Post by noynac on 2007-11-08
The following document is entitled "Editing ext2/ext3/ReiserFS/FAT32/NTFS Partition Labels." It's a bit outdated but worked for me:

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

or

[http://tinyurl.com/2sqnv6](http://tinyurl.com/2sqnv6)

---

### Post by jay767 on 2007-11-10
Hey thanks guys. I actually tried sudo e2label /media/home but since it didn't tell me "30 GB Volume" (actually it was blank) I kept looking. Seems Nautilus got or made up a default if there's no label because after I did sudo e2label /media/home home it changed it. Something else to write into my Big Book of CLI Commands.

---

