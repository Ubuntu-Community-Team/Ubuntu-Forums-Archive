---
title: "Borked xorg.conf - how do i edit from livecd?"
date: 2007-02-05
forum: General Help
---

### Post by DrAwesomePhD on 2007-02-05
Hi, the title basically says it all... i borked my xorg.conf and would like to fix it from the livecd.  Does anyone know how to do this?  I cant see my harddrives ( i dont think) and if i can i dont know where to look -.- ...

---

### Post by taurus on 2007-02-05
Applications -> Accessories -> Terminal
```
sudo mkdir /mnt/ubuntu
sudo mount -t ext3 /dev/hda1 /mnt/ubuntu
(assuming your Ubuntu is on /dev/hda1...)
sudo cp /etc/X11/xorg.conf /mnt/ubuntu/etc/X11/xorg.conf
```
Reboot.

---

### Post by DrAwesomePhD on 2007-02-05
much appreciated :)

---

### Post by Omnios on 2007-02-05
You can also boot into recovery "text mode" and use 

```
sudo dpkg-reconfigure xserver-xorg
```

 command which is a turtle like graphics type program for configing and autoconfiging xserver.

---

