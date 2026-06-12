---
title: "error loading os after using gparted live"
date: 2007-11-15
forum: General Help
---

### Post by dave37 on 2007-11-15
Have 2 hdd in this machine, hda has winbloze, hdb has Ubuntu dapper desktop. hdb is the boot drive. Used gparted live cd to delete hdb1 and then increase hdb2 size to take up the empty space.  hdb2 was always the bootable drive.  Ever since I get a bios error of "error loading os".  If I boot with the ubuntu dapper alternate dvd and select "boot from first hard drive" my system loads fine.  Grub comes up, I have my os selections and off I go.  I find it strange that ubuntu is still calling the boot partition hdb2.

However, nothing I have tried works.  It probably isn't a gparted issue but I wondered if anyone had any ideas?

---

### Post by meierfra on 2007-11-15
You need to reinstall grub and edit the file /boot/grub/menu.lst.

Open a terminal (Applications->Accessories->Terminal) and post the output of the commands

```
sudo fdisk -l
```

and

```
cat /boot/grub/menu.lst
```

(all l are lower case L, not ones)

---

### Post by dave37 on 2007-11-16
Using the method noted in this post for if grub doesn't detect your root partition when trying to restore in terminal, [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351) , and editing the /boot/grub/menu.lst to read root (hd1,0) instead of (hd1,1) it worked flawlessly and I'm back up and running.

---

