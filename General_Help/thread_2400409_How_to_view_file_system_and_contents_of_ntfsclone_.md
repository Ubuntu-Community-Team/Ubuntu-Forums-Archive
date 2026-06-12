---
title: "How to view file system and contents of ntfsclone image"
date: 2018-09-05
forum: General Help
---

### Post by Rehaan_Raja on 2018-09-05
I created an image of my partition with "ntfsclone"

Man page: [https://linux.die.net/man/8/ntfsclone](https://linux.die.net/man/8/ntfsclone)

The result was an image file or .img file.

I right clicked and mounted it with Disk Image Mounter in Ubuntu Budgie.

In the program gnome-disks (to install it type "sudo apt-get install gnome-disk-utility"), the image shows up as mounted under /dev/ as "Loop3". Unfortunately the program does not detect that it is an ntfs partition and instead says it has an "Unknown" file system.

How can I get the program to recognise the ntfs file system so that I can view the files?

---

### Post by yancek on 2018-09-05
Don't use ".img" files or Disk Image Mounter but you might try to manually mount it.  First create a mount point, as an example:  sudo mkdir /mnt/fileimg
Then try to loop mount it:  sudo mount -o loop nameoffile.img /mnt/fileimg.  Obviously replace the name with the actual name.

---

