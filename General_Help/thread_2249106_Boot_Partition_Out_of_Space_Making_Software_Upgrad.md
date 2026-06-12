---
title: "Boot Partition Out of Space Making Software Upgrades Impossible"
date: 2014-10-19
forum: General Help
---

### Post by biglesca on 2014-10-19
Hello all,

I use a computer in which I previously had a dual boot WinXP/Ubuntu setup.  I have since transitioned to Ubuntu only by installing the OS over the existing WinXP installation.  This may have been a newb mistake because now I'm getting warnings that the boot partition is out of space and I should make more room to continue with the software update.

Is there a way to increase the current boot partition size without having to reinstall Ubuntu or, will I have to reformat the HDD to remove the boot partition and then reinstall Ubuntu and specify the boot partition size on installation?

Ubuntu 14.04.1
HDD size 160 GB

Thanks in advance for your reply.

---

### Post by Bas_Kooijman on 2014-10-19
Do you have installed GNOME disks during the installation? With this program you should be able to expand your boot partition if you have space on your harddisk.

---

### Post by Impavidus on 2014-10-19
No need to change any partitions, just remove some old kernels. Running```
sudo apt-get autoremove
```should remove the old kernels. Else find the packages manually and remove them one by one. There is also a nice oneliner to remove them all, mentioned many times on the forum. You can also use a graphical package manager.

Don't simply delete files from /boot.

---

### Post by O9aIevckc0 on 2014-10-19
first download the attached script

then to make it executable run 
chmod +x kernclean.sh

then sudo ./kernclean.sh

this should remove any old kernels that are no longer in use and free up some space on /boot for the updates


if this solves your problem please mark this thread as solved

---

### Post by biglesca on 2014-10-19
No GNOME disks of which I'm aware.  I tried GPARTED but I can't resize using that package, either.

I'll try the solution(s) suggested in the other posts on this thread.

Thanks for the help.

---

### Post by biglesca on 2014-10-19
> **Impavidus said:**
> No need to change any partitions, just remove some old kernels. Running```
sudo apt-get autoremove
```should remove the old kernels. Else find the packages manually and remove them one by one. There is also a nice oneliner to remove them all, mentioned many times on the forum. You can also use a graphical package manager.

Don't simply delete files from /boot.



Thank you! This resolved my problem and I was able to update the computer.

---

