---
title: "menu"
date: 2007-12-03
forum: General Help
---

### Post by irshan on 2007-12-03
before install ubuntu i hav installed fedora and windows, after installation of ubuntu fedora not appear in the menu but other os are available. so is there any way to get fedora again without reinstall.

---

### Post by Schalken on 2007-12-03
there are many ways to do this. one way is described below.

install "gparted" via synaptic (system > admin > synaptic) or via apt-get (apt-get install gparted). then start it (system > admin > gnome partition editor), then identify which device is the partition containing fedora, such as /dev/sda1 or /dev/hdc3 or /dev/hdb2 etc etc

then do:

```
sudo mkdir /media/fedora #make a directory to mount the partition to
sudo mount /dev/whateveritwas /media/fedora #mount the partition to said directory

sudo cat /media/fedora/boot/grub/menu.list #get the contents of fedora's grub menu

sudo umount /dev/whateveritwas #unmount the partition
sudo rmdir /media/fedora # get rid of the directory we mounted the partition to
```

make sure you replace /dev/whateveritwas with the partition containing fedora which you found with gparted, and *post the output of the third command*.

you should then be able to take the menu entries out of fedora's grub menu (the entries that boot fedora) and put them in ubuntu's grub menu. you can edit ubuntu's grub menu by doing ```
 sudo gedit /boot/grub/menu.list 
``` then add the sections that start with "title Fedora..."

---

### Post by ajgreeny on 2007-12-03
Fedora used to install into logical volumes by default.  I don't know if it still does, but that may explain what the problem is as the normal mounting commands don't work with LVs and you must make sure you have the appropriate packages installed such as lvm2, I think.  Others may have more info than I do.

---

### Post by irshan on 2007-12-03
imay o know what is the reason bihind this for dissapear fedora menu.bcoz im not familiar with cat,umount etc...

---

