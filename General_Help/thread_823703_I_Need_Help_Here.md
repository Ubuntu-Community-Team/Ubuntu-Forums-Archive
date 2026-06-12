---
title: "I Need Help Here"
date: 2008-06-09
forum: General Help
---

### Post by kayslay on 2008-06-09
****I just partitioned my hard disk,i have installed windows  on the first partition which is 40 Gigabyte and the second partition is 75 Gigabyte,i want to install ubuntu on the second partition,how  will i do it?:(

---

### Post by Titan8990 on 2008-06-09
You will boot to the Ubuntu Live CD. Post back if you need further instructions on how to do so. Double click on the Install icon on the desktop to begin installation.

When you get to the part where it asks you about partitions you will want to select "manual". Select your empty 75GB partition. You will need to break that 75GB partition down some more.

Ubuntu requires that you have a "SWAP" partition. It is recommended that this is approx double the size of your RAM and a minimum of 2GB. Create that SWAP partition from your empty 75GB.

Use your remaining space to format in EXT3 and set the mount point to /.

Thats it. After installation GRUB should pick up on your Windows install and you are ready to dual boot.

Good luck.

---

