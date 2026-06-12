---
title: "Resize Ubuntu OS Partition use gparted from usb boot not work"
date: 2018-02-18
forum: General Help
---

### Post by longvu183 on 2018-02-18
please help me
i am newbie
i ca'nt use gparted resize ubuntu os partition from usb ubuntu boot
i try deactive partition and resize but it does not work can not resize os partition.


please help me thank a lot 
[IMG]https://imageshack.com/a/img924/5703/8j3j6d.jpg[/IMG]

---

### Post by oldfred on 2018-02-18
You have used the advanced LVM partitioning system which is intended to use entire drive.
You need to use LVM tools to modify partitions inside the LVM.

If wanting to install Windows with Ubuntu probably better not to use LVM.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)

---

