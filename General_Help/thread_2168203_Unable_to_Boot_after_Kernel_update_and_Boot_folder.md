---
title: "Unable to Boot after Kernel update and Boot folder cleanups (12.10)"
date: 2013-08-16
forum: General Help
---

### Post by paulikjuraj on 2013-08-16
Hello

I was trying to resolve some small issues with hanging old Kernels and doing some general cleanup of BOOT folder but it seems I did something more serious that that. After I have restarted I cannot boot the system anymore.

I can boot from USB only and see my Hard Drive with all the data but as I am so new to this environment I cannot fix it. I have googled a lot and tried several things with reinstalling GRUB but it seems that the system doesn`t know where to find the partitions and what to boot. Please if you have any idea I would very appreciate any help.

Please see the photo of the screen: [https://dl.dropboxusercontent.com/u/7422588/20130816_200438.jpg](https://dl.dropboxusercontent.com/u/7422588/20130816_200438.jpg)

Many thanks!

---

### Post by Boab1993 on 2013-08-16
Hi paulikjuraj,

Tried boot repair yet?

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by chkneater on 2013-08-16
If the previous answer didn't help, you can try using a Live CD to get gparted to make a partition and install a new system there without overwriting your data.  You then should be able to get to your data files and all the junk you may have and move it to the new install.  Might be worth a try if noone can come up with something better.  Hopefully your entire drive isn't partitioned for that one install, then you might lose some info when partitioning.  Good Luck!

---

