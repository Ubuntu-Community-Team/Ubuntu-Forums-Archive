---
title: "Deleting Ubuntu from an external USB drive?"
date: 2007-11-12
forum: General Help
---

### Post by Zerves on 2007-11-12
Hello,

A while ago I installed Ubuntu 7.10 on a Seagate 500gb external USB drive. Since then I decided to go back to just windows and use the drive for file storage. I got rid of grub but now when I plug in the external drive I cant access it. Is there some way to reset the drive to its original state?

---

### Post by expatCM on 2007-11-13
Could you not install gparted and then format the drive to the file system you want.  Or boot from the Live CD and then format the drive?

But if you are now using Windows why not just download the Seagate installation tool in Windows and use that to install and format the drive?

---

### Post by JasonF on 2007-11-13
In windows right click My Computer, select Management and select Disk Management in that window, delete the ubuntu partitions and create and format NTFS partitions.

---

### Post by datadrop on 2007-11-13
Im going to assume your using windows XP for this.

If  you go into Control Panel -- > Administrative Tools ---- > Computer Management 

In there Click on Disk Management.
You should see your 500GB drive in there while plugged in.

MAKE SURE IT IS NOT YOUR C DRIVE
You can then right click on it and delete the ext3 partition and then recreate it.  Make sure you format it too.

Feel free to msg me if you get stuck.

---

### Post by Zerves on 2007-11-13
Thanks so much, it is working perfectly now :)

---

