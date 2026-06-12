---
title: "Cannot write to External drive (NTFS)"
date: 2007-11-07
forum: General Help
---

### Post by tepegoz on 2007-11-07
Hi all,
I am using an external disk with NTFS partition.  Gutsy enables ntfs support by default, however some of the data cannot be written to the disk.  
Let me tell again. I copy, let's say, 5 folders to the external drive.  Copying process finalizes without any error, and those folders are seen on the external drive.  Then I unmount and remount the drive.  What I see is only 4 of those 5 folders are copied.  One folder is not copied.  

I copied using nautilus, mc, shell, all same.  There is no error log or something.

any suggestions?

---

### Post by namanbagga on 2007-11-07
You can try using this-
```
sudo apt-get install ntfs-config
```

I hope you use the eject option and safely remove your external drive:popcorn:

---

### Post by tepegoz on 2007-11-15
Yeah, I did it before and enabled ntfs, but nothing changed.  
Sure, I safely remove the drive.

I think that error could be a temporary one, I don't get such weirdness these days.

---

