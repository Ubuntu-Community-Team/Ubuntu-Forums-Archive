---
title: "Free Storage on Live USB Not Equal to USB's Capacity"
date: 2016-11-16
forum: General Help
---

### Post by mteverett on 2016-11-16
[COLOR=#111111][FONT=Ubuntu]I created a live USB by downloading Ubuntu for desktop and then used Rufus to make the USB bootable. When I plug the USB into my computer while running Windows, the USB says that there is 27.2 GB of free space out of 28.6 GB. However, when I boot Ubuntu and click properties, it tells me that there is only 5.9 GB of free space left. Can someone please explain this to me or offer a way to fix it?[/FONT][/COLOR]

---

### Post by Bucky Ball on 2016-11-16
Welcome. Sure. I can have a go. Windows probably has no idea what the USB is as it may now be formatted as an EXT4 filesystem partition. Windows doesn't know what that is.

If you have a look in Disk Management, or whatever it is, in Win and see what type of filesystem it considers the partition to be. It may just say 'healthy' or it may give something else. 

Boot to Ubuntu and use Gparted to have a look at the partitions on the USB there. Is there a large EXT* partition there?

---

