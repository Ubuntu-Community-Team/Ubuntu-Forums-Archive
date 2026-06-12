---
title: "Ubuntu 18.04, want to enhance partition .."
date: 2018-10-16
forum: General Help
---

### Post by fantasio1980 on 2018-10-16
Hi,
i successfully Setup Ubuntu 18.04 but i don't know how to enhance my Primary Partition, i attached a pic from my drives. Who can help me how to enhance this Partition? There is 150gb unused space that i want to add to "Dateisystem Partition 1". Thanks in advance!

---

### Post by oldfred on 2018-10-16
I cannot tell if MBR or gpt partitioning. You can use either but MBR is now 35 years old and gpt has some improvements.
If only installing Ubuntu on a drive, you can use gpt whether install is UEFI or BIOS if you have correct supporting partitions.
One advantage of gpt is all partitions are primary, so you do not have the 4 primary partition limit and have a backup partition table.

My normal install is into a 25 to 30GB  / (root) partition with separate data partition. But a bit more complex for a new user as you have to create partition, format partition, give yourself ownership & permissions and link data folders back into /home.
Most newer users find creating a separate /home partition during install as much easier as all the settings are done as part of the install. But a /home should not be shared across different installs (unless upgrading same flavor).

You can reinstall if brand new install and not configured, but have to use Something Else install option. And choose (change button ) to have one partition as / (root) and one as /home. You can partition in advance or during install.

If you have done a lot of configuration, you can move /home to a partition. Details:
       To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Older version, but install still the same:
[https://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](https://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
 
      
 GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by dino99 on 2018-10-16
To make change on a partition, that one need to be unmounted (inactive).
So boot on a livecd (liveusb), then use gparted.
You also can download gparted live to a usb key to get and use directly that tool   [https://gparted.org/livecd.php](https://gparted.org/livecd.php)

---

