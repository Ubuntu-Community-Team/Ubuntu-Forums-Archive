---
title: "Can't install grub"
date: 2006-12-26
forum: General Help
---

### Post by commodore on 2006-12-26
If I try "grub-install hd0,0" I get this error:
"Could not find device for /boot: Not found or not a block device." I can type anything to replace the "hd0,0" but it still doesn't work. I have two harddrives. I installed Ubuntu on the slave and then Windows on the master. Of course Windows f****d up my MBR so I put in the live cd and tried to grub-install but nothing helps.

---

### Post by bulldog on 2006-12-26
Can you give the output of ```
sudo fdisk -l ( l as in like)
```

You should be aware there are different ways to boot your computer with windows and ubuntu.

[http://www.ubuntuforums.org/showthread.php?t=275728](http://www.ubuntuforums.org/showthread.php?t=275728)

---

### Post by commodore on 2006-12-26
Ok I managed to install grub to the second harddrive with "grub" instead of "grub-install". I then used fdisk (for the first time :P) to remove the boot flag from the windows partition and add it to the partition with GRUB. Now I found another error I made earlier :P but it's not connected with this problem any more.

---

### Post by bulldog on 2006-12-26
You should make the ubuntu drive master boot device and install GRUB on this one.
Make the windows disk the slave and make some modifications to your menu.lst.

Now you can boot windows and ubuntu from GRUB and in case of disaster you can boot windows with is own boot loader.

Just some advice,you should do it as you like of course.:D

---

### Post by commodore on 2006-12-27
I don't want to open my case and stuff :)

---

