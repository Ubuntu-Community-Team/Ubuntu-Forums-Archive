---
title: "Disk check NTFS drive"
date: 2008-03-20
forum: General Help
---

### Post by 5circles on 2008-03-20
Is it possible to do a disk check of an NTFS partition from Ubuntu?  I'm having a problem with a Windows partition, and the disk check from Windows seems to be creating more issues.

I'm running Gutsy on this system.  I can see ntfs (not ntfs-3g) as the partition type in /etc/fstab.

Thanks
MIke

---

### Post by Herman on 2008-03-21
:) Hello Mike,
Sure we can run a file system check on an NTFS file system from Ubuntu. In fact, we can do almost anything you can think of with NTFS, if we install a package called 'ntfsprogs'.
```
sudo apt-get install ntfsprogs
```Once you have ntfsprogs installed, you will be able to see all the new commands you will now have available to you for working on NTFS by running 'man ntfsprogs'
```
man ntfsprogs
```To run a file system check on an NTFS partition from the command line in Ubuntu,
```
sudo ntfsfix /dev/hda1
```Where: '/dev/hda1' is the partition containing the ntfs file system you want to fix or take care of. Feel free to use a different partition number if your ntfs partition is not /dev/hda1. Look with a partition editor first to verify.

Regards, Herman :)

---

