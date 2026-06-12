---
title: "usb fat32 harddrive"
date: 2005-10-10
forum: General Help
---

### Post by chenyw on 2005-10-10
Hi everyone! I just converted from fedora linux. I have one problem here. I hotplug a usb harddrive. my ubuntu5.10 detected it. I can read and execute the contents but cannot write on it.
Is there anyway to write on the harddrive?

hope someone can help me.

Thank you 

chenyw

---

### Post by jasmuz on 2005-10-10
Hello there, 
you should open your /etc/fstab list, to see if your USB HD is listed as /dev/sda1 and next to it should say its filesystem type, like this

/dev/sda1       /media/Windows  vfat    user,umask=0222     0       0

It must say "user&#168; in order to give you the rights to write to it.

---

