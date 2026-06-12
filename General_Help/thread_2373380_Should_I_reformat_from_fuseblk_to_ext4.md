---
title: "Should I reformat from fuseblk to ext4?"
date: 2017-10-05
forum: General Help
---

### Post by peridian on 2017-10-05
Hi,

I have a USB drive that when plugged in mounts as you would expect, and appears to be usable.  I thought they'd have formatted it by default for Windows NTFS and so I figured the first thing to do is reformat to ext4.

Although fdisk reports "Microsoft basic data" as the file system, the 'df' command says that the drive is formatted using fuseblk.

Should I reformat the drive to ext4?  Is the default format suitable for long term use with Linux systems only?

Regards,
Rob.

---

### Post by Autodave on 2017-10-05
You could, but keep a couple things in mind. Ext4 will not be recognized by anything other than Linux. NTFS is pretty much recognized by everything. Also, and someone will correct me if I am wrong, formatting it to ext4 will require you to mount the drive in order to be able to write to it or delete anything on it.

---

### Post by ian-weisser on 2017-10-05
'fuseblk' is not a format (like FAT32, NTFS, ext4, etc.)
'fuseblk' means that an Ubuntu root service (FUSE - File System in Userspace) is making the data available to your user. All hardware is otherwise owned by root - before FUSE, accessing a USB stick was more challenging.

Use a tool like 'fdisk' or 'parted' to see the real format and/or partitioning.

---

### Post by peridian on 2017-10-15
Brilliant, thanks for the advice.

Regards,
Rob.

---

