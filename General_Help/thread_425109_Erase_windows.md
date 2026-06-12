---
title: "Erase windows"
date: 2007-04-27
forum: General Help
---

### Post by artir on 2007-04-27
I have 4 partitions: /, swap, /media/Datos and /media/WIndows or /dev/hda1.
I don't need Windows anymore, I have copied anything important into Ubuntu. WIth gparted i can unmount and erase, but then what? i want to;
1.give that space to the Datos partition
2.Make windows disappear from GRUB
thnks

---

### Post by Hairy_Palms on 2007-04-27
in a terminal run "sudo gedit /boot/grub/menu.lst" and if you scroll to the bottom you should see an entry like

> title windowsxp
root hd(0,0)
chainloader +1

if you delete or comment that out you should not see it in grub anymore.

---

### Post by strabes on 2007-04-27
You'll have to do that with a live CD, because you can't operate on partitions while they're mounted. You can either use the gparted live CD (which I recommend), located at [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) or you can use the gparted program included with the live CD that you used to install. To stop windows from showing up in grub, you have to edit your menu.lst:

```
gksudo gedit /boot/grub/menu.lst
```

Delete the lines that look similar to these:

> 
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


---

### Post by lw5 on 2007-04-27
Unless you can backup the Datos partition and delete that as well, I would just reformat your old windows partition to a sensible format and mount that.

---

