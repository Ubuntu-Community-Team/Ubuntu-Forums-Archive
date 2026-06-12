---
title: "Hdd"
date: 2015-11-22
forum: General Help
---

### Post by ray37 on 2015-11-22
Recently ( today ) i bought a server that was advertised as a 2tb HDD so i bought it but then it came with 4 x 500GB is there anyway / guide that i can use the /home dir to use the full 2tb any help will be really appreciated not sure as im new to ubuntu 

thanks

---

### Post by khelben1979 on 2015-11-22
If you have 4 hard drives, it is smarter (in my opinion) to use each of these hard drives as separate partitions. Here you got some basic documentation about partitioning the harddrive:  [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)  Make sure you read it through to get some basic knowledge what this is all about to prevent yourself from a current or future data loss working with these things.

However... if you really want to use all the harddrives mounted as one big partition ( /home ), it is possible! I would recommend against it, though. All harddrives are going to use the same mountpoint: /home to get this to work but you might want to add some labelling such as home1, home2, home3 and home4.

---

### Post by oldfred on 2015-11-22
I keep /home inside my / (root) and / is only 25GB,  and use /mnt/data partition(s) on my desktop.

If you really want one large partition you can use LVM, but if any drive fails, you will lose all data.
       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
[http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html](http://www.tutonics.com/2012/11/ubuntu-lvm-guide-part-1.html)

---

