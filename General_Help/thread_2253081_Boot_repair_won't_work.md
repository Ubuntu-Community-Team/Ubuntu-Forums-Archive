---
title: "Boot repair won't work"
date: 2014-11-17
forum: General Help
---

### Post by hop5uk on 2014-11-17
When i try to use Yannubuntus boot repair from live CD in order to fix my Ubuntu 12.04 installation it does not work. It appears to go through the process and then comes up with the message "GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as GParted. Then try again." I try and open GParted but it won't let me create anything. Can anybody help?

---

### Post by ajgreeny on 2014-11-17
You must make sure the partitions or hard disk is completely unmounted when you try to change or make any new partitions with gparted.

Right click on all partitions showing in gparted and choose **unmount**, or for swap choose **swapoff**.  You should then be able to edit partitions and make the required small partition (minimum of 1MB) and using the Partition menu Manage flags, give it the bios_grub flag that it needs.

---

### Post by hop5uk on 2014-11-17
Thanks ajgreeny. But my operating system is on a pair of Raid 1 disks and therefore i have to install mdadm before i start the boot-repair. I think that means that the disks are automatically mounted.

---

### Post by ajgreeny on 2014-11-18
Sorry, but I know nothing of raid, so will have to leave you to others.

---

