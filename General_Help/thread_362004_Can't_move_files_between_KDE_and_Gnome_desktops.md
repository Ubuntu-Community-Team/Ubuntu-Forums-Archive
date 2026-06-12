---
title: "Can't move files between KDE and Gnome desktops"
date: 2007-02-15
forum: General Help
---

### Post by kljsdfuiowerm,help on 2007-02-15
Hi out there,

I have been using ubuntu, (both, Gnome and KDE versions) I have a problem.

On my computer, I have both Gnome Ubuntu and KDE Kubuntu, at bootup I chose from the Grub menu which version to loadup. 

I use Kubuntu for certain things and Gnome Ubuntu for others. My problem is I do not know how to share, move, or find files between the two systems.

Example:

Download file in Kubuntu to desktop. Then log out of Kubuntu and restart computer. Then load up Ubuntu from Grub menu, Log into desktop and can't find, search, copy, move, or open file that was downloaded onto Kubuntu destop.

Any help of suggestions would be nice, thank you.

---

### Post by pay on 2007-02-15
Firstly you can install kde and gnome in the same installation. Theres no need for two installations. Back to your question. There are two partitions with the different installations on them. To mount them you need to add a line to /etc/fstab. You will need to add a line like this one```
/dev/hda3        /mnt/hda3       ext3    defaults                0 0
```But first you'll need to create a mount point```
sudo mkdir /mnt/hda3
```Obviously though, you'll need to change hda3 to your partition and ext3 to your format type.

---

### Post by kljsdfuiowerm,help on 2007-02-15
Thanks I'll work on it, bye for now.:KS [http://ubuntuforums.org/images/smilies/star.png](http://ubuntuforums.org/images/smilies/star.png)

---

### Post by kljsdfuiowerm,help on 2007-02-15
Thanks it worked, now I can move on to other fun stuff.

---

