---
title: "Root partition not seeing expanded disk"
date: 2016-03-23
forum: General Help
---

### Post by dean.stickells@gmail.com on 2016-03-23
Hi,

I have a virtual Ubuntu 14.04 LTS server installation and clearly underestimated the required disk space for my needs.  I have expanded the volume in VMware, used gparted to move the existing /sda5 partition back and then extend the sda1 partition adequately.  I can see from fdisk that the resize was successful but now I am stuck and simply cannot work out how to reflect the new space to the root partition itself (which is 99% full)  I'm guessing that I have missed something simple because I cant find any other posts along these lines.


[ATTACH=CONFIG]267963[/ATTACH][ATTACH=CONFIG]267962[/ATTACH][ATTACH=CONFIG]267961[/ATTACH]

Thanks in advance !

---

### Post by oldfred on 2016-03-23
I do not know LVM.
But sda1 is your /boot partition which is outside the LVM.
And / is inside your LVM as /dev/mapper/.....root.

You have to use LVM tools to resize partitions inside the LVM, not gparted.
       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[URL="http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html"]http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html
[http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html](http://tldp.org/HOWTO/LVM-HOWTO/extendlv.html)

[/URL]

---

### Post by dean.stickells@gmail.com on 2016-03-24
Aha,  that kinda makes sense..  And explains why I couldn't see the mount point.

The install was a next, next, next install so assumed that the posts I found would be appropriate - clearly not!

Thank you so very much for the links,  I will give them a try!!

---

### Post by dean.stickells@gmail.com on 2016-03-27
Sorted! - Thanks again for the pointer,  the following commands did the trick :)

**Expand the logical volume to use all the available partition**
sudo lvextend -l +100%FREE /dev/mapper/mhfvzbx01--vg-root

**Resize the file system to fill the logical volume**
resize2fs /dev/mapper/mhfvzbx01--vg-root

a df then shows the disk 94% full rather than 100% :)

---

