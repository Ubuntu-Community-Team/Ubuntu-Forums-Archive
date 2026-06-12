---
title: "Resize LVM and format to NTFS"
date: 2015-10-23
forum: General Help
---

### Post by katharez on 2015-10-23
I want to go back to Windows and I need to create NTFS space on my hard drive. Yet I have a hard time understanding why there's no free space (only 4MB).
[http://cs628424.vk.me/v628424733/21831/kKXgqLUdHo8.jpg](http://cs628424.vk.me/v628424733/21831/kKXgqLUdHo8.jpg)

And you can see this space is free.
[http://cs628424.vk.me/v628424733/21827/GJlwKOtQEB8.jpg](http://cs628424.vk.me/v628424733/21827/GJlwKOtQEB8.jpg)

How can I resize LVM so later I can unmount the partition and format it to NTFS?

---

### Post by SeijiSensei on 2015-10-23
Why bother?  If you simply want to convert back to Windows, let the Windows installer partition and format the hard drive.  Or do you want to keep the Linux installation as well?

---

### Post by katharez on 2015-10-23
> **SeijiSensei said:**
> Why bother?  If you simply want to convert back to Windows, let the Windows installer partition and format the hard drive.  Or do you want to keep the Linux installation as well?

I've tried to install Windows and failed. Windows can't read the ext3 ext4 file system thats why I need NTFS partition.

---

### Post by SeijiSensei on 2015-10-23
I thought Windows just blithely overwrote the partitions and made them all its own.  Are you sure there's no option to tell Windows to repartition the drive?

If you have to do it in advance of installing Windows, you can boot from an Ubuntu installation CD or DVD and choose "Try Ubuntu."  Then run the gparted utility, point it at the hard drive, and tell it to delete all existing partitions.  If you want you can create a new partition spanning some or all of the disk and mark it for Windows.  I'd let the Windows installer create the NTFS filesystem.

---

### Post by yancek on 2015-10-23
> I've tried to install Windows and failed. Windows can't read the ext3 ext4 file system thats why I need NTFS partition

Windows doesn't need  to read the ext3 or ext4 partitions.  Generally it will just format the whole disk and install although newer releases of windows allow you to select a partition to install to.  You must get some kind of error message when trying to install.  If you could post that or give a little more detail someone might be able to help.

---

