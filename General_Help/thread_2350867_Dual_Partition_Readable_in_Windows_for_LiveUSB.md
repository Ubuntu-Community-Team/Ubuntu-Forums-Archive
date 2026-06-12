---
title: "Dual Partition Readable in Windows for LiveUSB"
date: 2017-01-28
forum: General Help
---

### Post by renny2125 on 2017-01-28
Hi there!

I'm trying to get my removable USB drive (testing on a Lexar USB 3.0, 16GB drive) to be bootable AND have both partitions show up in Windows, so that I can access certain files on the drive in the bootable environment and on Windows.

---

### Post by gdesilva on 2017-01-28
If you have Ubuntu installed on the USB and trying to read the contents from Windows (which I think is the question - ignore this if it is not) then you would need additional software on the Windows to be able to do this. Check [this]("http://www.howtogeek.com/112888/3-ways-to-access-your-linux-partitions-from-windows/") out.

---

### Post by yancek on 2017-01-28
The drive you are using is a pendrive/flash drive and windows will only recognize the first partition on the drive.  It doesn't matter if you have an ntfs/vfat or other windows filesystem on the partition on the flash drive.  This is a business decision by microsoft and there is nothing anyone here or any Ubuntu/Linux developers can do about it.  If you have an actual hard drive connected by usb, you can create as  many partitions as you want and access them from windows, that is, if they have windows filesystems on them.  The link below at the windows10 forums discusses the issue.

 [https://www.tenforums.com/drivers-hardware/27018-possible-create-multiple-partitions-usb-flash-drive.html](https://www.tenforums.com/drivers-hardware/27018-possible-create-multiple-partitions-usb-flash-drive.html)

You can create and access any number of partitions on a flash drive with Linux and access them regardless of whether they are Linux or windows filesystems.

If you are willing to start over with the usb, you can use the mkusb software which will create an ntfs partition as the first partition and install Ubuntu or a derivative to another partition.  See the link below for details.

 [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

