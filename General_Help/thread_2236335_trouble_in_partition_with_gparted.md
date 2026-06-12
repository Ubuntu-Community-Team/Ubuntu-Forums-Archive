---
title: "trouble in partition with gparted"
date: 2014-07-26
forum: General Help
---

### Post by giri3 on 2014-07-26
Hello!

        I am newly installed ubuntu on my windows 8 pc through usb . The whole hard disk is converted to single drive and
windows 8 is deleted. i want to make partitions to drives to make as primary second drive . i used gparted but it is unable to 
perform the operation to make the new drive. please help me to create new partition.

---

### Post by ajgreeny on 2014-07-26
You really should not call these partitions "drives"; drives are the separate physical disks and the nomenclature used by Microsoft is a constant source of confusion that Windows users suffer from when describing their hardware after moving to Linux.

However, to your query; gparted will not change or edit any partitions that are mounted, so installing gparted on your new Ubuntu OS will never work to change any of its partitions.  You need to boot to the DVD or USB that you used to install the system, as the live OS already has gparted available.  It is likely that the live system will have found and be using the swap partition from your installed OS so you will have to right click on swap and click "Swapoff" in order to go further.  You should then be able to edit the partitions as you want, but be warned it, can take a very long time, depending on what you want to do.

Make sure you have backups of any personal files, just in case everything goes wrong!

---

