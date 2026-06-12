---
title: "I deleted a file from my USB flash drive the ubuntu way and want my file back!"
date: 2007-12-08
forum: General Help
---

### Post by s3a on 2007-12-08
Is there a GUI way to get back my file?? Or at least a terminal one?

*edit* I read you can't get back files if its an ext3 file system but you can on an ext2...well I'm using fat16, I think (it's a 2 GB drive...the maximum of FAT16's abilities)

---

### Post by danwood76 on 2007-12-08
to be able to get the file back you will need to have not written any data to the disk since the delete.
If you have it will have overwritten the blocks that were taken up previosly by your file.

Ext3 deletes the Inodes of the files so you will have to unmount the drive and grep for parts of the file.
I doubt there is a gui for it as most people dont delete stuff they need.

Good luck with it.
regards,
Danny

---

### Post by Nem1976 on 2007-12-08
Have you looked on the drive for a .trash folder?  I know with my firefly (usb drive) i have a .trash folder in there that has all the files I just deleted .  I can go in and copy the files back out and I'm good to go.  You will most likely need to show hidden files and folders to see it.

---

### Post by s3a on 2007-12-08
If there was a .trash folder then the deleted stuff would appear in the trash can...but thanks for trying!

---

### Post by Nem1976 on 2007-12-08
> **s3a said:**
> If there was a .trash folder then the deleted stuff would appear in the trash can...but thanks for trying!


Well in my situation my flashdrive doesn't show up in my normal trash can.  Not sure if it's because I don't use the gnome panel trashcan applet or not.  Using the AWN applet when delete something from my flash drive it doesn't show up in my trashcan I normally just browse to that folder and delete it.

---

