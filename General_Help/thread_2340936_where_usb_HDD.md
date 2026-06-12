---
title: "where usb HDD?"
date: 2016-10-23
forum: General Help
---

### Post by Matrix01 on 2016-10-23
how to find usb HDD in Xfe?

---

### Post by ajgreeny on 2016-10-23
Do you mean xfce4 Desktop Environment of Xubuntu; I don't know what you mean by xfe?

If this is xfce4 or Xubuntu there will be an icon on your desktop normally for a USB disk that is attached, and if not there it will show in the left hand pane of the file-manager, thunar, if Xubuntu.

---

### Post by oldos2er on 2016-10-23
xfe is a file manager ("X File Explorer). 

Look in /media or possibly /mnt

---

### Post by ajgreeny on 2016-10-23
Well there you are !!!

Sorry I missed that; I'm learning something new every day.

As it's just a file manager the USB, unless included in your fstab file with some other mountpoint, will automount in **/media/*username***

I see **xfe** does not have a shortcut pane to the left but is a twin panel manager like **gnome-commander** so you will need to navigate down to the /media/username folder and see the contents of the disk there.

---

### Post by Matrix01 on 2016-10-23
> **oldos2er said:**
> xfe is a file manager ("X File Explorer). 

Look in /media or possibly /mnt

found it,

---

