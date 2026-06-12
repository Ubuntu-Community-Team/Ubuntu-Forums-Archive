---
title: "Deleted Ubuntu partition and now it wont boot"
date: 2013-12-23
forum: General Help
---

### Post by kmmurphy84 on 2013-12-23
So i dual boot windows xp and ubuntu but deleted my Ubuntu partition to make more room. But now I cant boot windows. I figured out I needed the grub so i tried to install ubuntu but i couldnt. So instead I used the Untangled (router os) cd just to see if it worked. It installed but when i went to boot windows from it i did not see it (like when i had ubuntu). So is there anyway i can boot windows again i don't care if i have to completely erase my drive.

---

### Post by Hodevah on 2013-12-23
Yes you can use the rescatux cd or the ubuntu remix to load up your mbr  again. You use those via usb. Go to Pendrive Linux, download version  1.9.9.9 (latest version) and download/install either rescatux or  ubuntu-remix. 
Or to go directly to the Ubuntu-remix page go here:
[http://www.ubuntu-rescue-remix.org/](http://www.ubuntu-rescue-remix.org/)

The tool that you'll be using is on the Unity dashboard. Look for it to re-install your mbr.

Mind you, you need another working computer to download/install all of those before you can actually do anything with them. If not, you'll just have to find another way or re-install everything from scratch.

---

### Post by Impavidus on 2013-12-24
[Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) should be able to fix this. You can use the live disk that you used to install Ubuntu.

The problem is caused by the fact that grub, the bootloader, has to read some files from the Ubuntu partition. With the Ubuntu partition gone, grub doesn't know what to do. Boot-Repair can fix this by installing a bootloader that can load Windows.

---

