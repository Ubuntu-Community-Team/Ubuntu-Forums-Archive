---
title: "Newbie Questions"
date: 2006-12-13
forum: General Help
---

### Post by TimberWolf on 2006-12-13
I'm new to both Ubuntu and the Linux operating system and the change from Windows is quite bewildering. My brother walked me through most of the installation and introduced me to Automatix, which installed a ton of common apps. It showed installation for Nvidia drivers, but i can't help but feel that they aren't up to snuff with the functionality of my Windows drivers. 

For one, i can't raise my resolution to the max 1280x1024. Also, graphics seem to be handled slower than they should. Google Earth is choppy and some menus are slow. I've tried downloading both sets of linux drivers directly from nvidia.com but they fail to run. I've searched Google, the Ubuntuforums, and Wiki help files exhaustively but the results are confusing. Any help on this would be appreciated. 

Secondly, i was extremely impressed with Ubuntu's partition management during installation. I'd like to access this tool again to tinker with my partitions some more but i can't find it anywhere. Documentation on it is also eluding me. 

Thanks in advance.

---

### Post by pay on 2006-12-13
Here;s a guide on how to install the nvidia drivers
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by TimberWolf on 2006-12-13
It says that i already have the latest version. Still can't up my resolution, though.

---

### Post by aysiu on 2006-12-13
This is the best guide I've seen to tweaking screen resolution:
[http://ubuntuforums.org/showpost.php?p=129379&postcount=21](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

And to get the partitioning tool back up again, just boot the live CD. You could install the program on your installed Ubuntu, but you probably wouldn't be able to use it for much, since you can't resize partitions that are mounted or in use.

---

### Post by celsofaf on 2006-12-13
Anyway, you could however want the partition program to play with non-Ubuntu partitions, or partition USB flash drives if needed. It is called GParted, but there is also QTParted (for Kubuntu). If you need it, just simply go to a terminal:

**sudo aptitude install gparted** (or qtparted)

---

### Post by NumberOne on 2006-12-13
As far as the partition software, search the forums for "gpartd",  there is a version that will installed with a live cd version of linux so you can run it on your current Linux install.  I just used it a few days ago and it worked flawlessly.

---

