---
title: "Immediate help needed! Unable to bypass Minimal GNU Grub screen."
date: 2015-05-14
forum: General Help
---

### Post by jacob69 on 2015-05-14
Hey all,
Need a bit of help. 
I was following a guide on how to uninstall Ubuntu from windows, involving deleting the HD partition Ubuntu was installed on.
I must have done something wrong because on reset i have been presented with the Minimal BASH grub terminal screen. 
Is there anyway to bypass this to boot back into windows? 

Was running Ubuntu 14

Thanks!

---

### Post by iojedaperez on 2015-05-14
You give few info for such a hurry help needed. It seems you deleted /boot/grub.cfg where it has the info for grub to call the menu and select the OS you want to boot. Thats why its recomended to have a separate partition for /boot and /, i soupouse you had a single partition for linux now you have 2 options recovering your disk MBR and make windows partition active or repairing grub with a live CD.

---

### Post by yancek on 2015-05-14
The information you posted indicates that you were using Grub from Ubuntu to boot both Ubuntu/windows.  Almost all the files necessary to boot with Grub are on the partition on which you had Ubuntu, the partition which you deleted.  The correct process if you wanted to remove Ubuntu would be to first install windows code to the master boot record and test to see if it successfully reboots.  After that, you could then format the Ubuntu partition with a windows filesystem such as ntfs.  If you have a windows installation disk or a recovery disk, try the Repair option to get windows code in the master boot record.  There are numerous sites explaining the process such as the one bwlow.



 [http://blog.danielburrowes.com/2012/02/repair-windows-7-after-removing-linux.html](http://blog.danielburrowes.com/2012/02/repair-windows-7-after-removing-linux.html)

---

