---
title: "Removable drive unmountable"
date: 2007-03-04
forum: General Help
---

### Post by random lazy guy on 2007-03-04
Whenever I insert my USB key and go to the file browser, and click on the USB drive in the little menu on the left, a popup window appears saying "Unable to mount the selected volume." When I click "show more details," it says, "mount: only root can mount /dev/sda1 on /media/sda1." This is a problem, because I can't use my USB key at all... and... it would be sweet, you know, if I could. Any ideas?

---

### Post by fdrake on 2007-03-04
you need to use sudo 
open the terminal and type:
sudo mount /dev/sda1  /media/sda1
let me know..

---

### Post by random lazy guy on 2007-03-04
Worked. Heh. Thanks for helping a newbie.

---

### Post by fdrake on 2007-03-04
you welcome

---

### Post by Incie83 on 2007-03-11
Obviously, this is no long term solution since it requires you to open a terminal window everytime you want to use your USB key.

A better solution would be to modify /etc/fstab, which you do by opening a terminal window and entering:

```
sudo gedit /etc/fstab
```

and add a line like this (I recommend some background reading on 'permissions' and 'mounting' to any newbie, for properly understanding this operation):

```
/dev/sda1 /media/sda1 vfat user,auto,utf8,umask=000 0 0
```

This gets to the root (no pun intended) of the problem, because it allows different users to automount the partition. This solves the following problem (indicated by the nautilus error message you quoted): mounting under root when you start up your pc with your USB key plugged in, then refusing to automount when you unplug and plugin the device in the same session.

---

