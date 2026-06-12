---
title: "How do I re-format an NTFS drive to a Linux FS?"
date: 2007-12-16
forum: General Help
---

### Post by tuproxy on 2007-12-16
I have an NTFS drive mounted and it is being read by a module that I installed.  I want to write to the drive, but don't trust the modules that write on NTFS drives.  I want to re-format the drive to some FS that works well with Linux.

The drive is a 500GB SATAII drive.  It will probably be used mainly for storage and maybe host a VMware system.  

What FS would be best?  ext3, ext4?  Are there any drawbacks to ext4?  Is it very stable?

Thanks  :)

---

### Post by taurus on 2007-12-16
I would format it to ext3.  And before you can format it, you first need to unmount it if you have already mounted it.  Then, you have an option to either format it to ext3 from a terminal or you can do that with gparted in System -> Administration (install it if you haven't).

---

