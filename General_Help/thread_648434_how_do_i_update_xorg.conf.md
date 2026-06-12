---
title: "how do i update xorg.conf?"
date: 2007-12-23
forum: General Help
---

### Post by Matsurosuka on 2007-12-23
im trying to update xorg.conf to use my touchscreen monitor, but i cant get the settings to stick. i update it using sudu gedit /etc/X11/xorg.conf and then running sudo dpkg-reconfigure -phigh xserver-xorg but it keeps reverting back to default. help!
thanks much
-Matt

---

### Post by Craigus on 2007-12-23
> i update it using sudu gedit /etc/X11/xorg.conf 

This will save your changes

> and then running sudo dpkg-reconfigure -phigh xserver-xorg but it keeps reverting back to default. help!

And then doing this will set everything back to default. Just don't do the second step - it isn't required.

---

### Post by oscarsfriend on 2007-12-23
I've not tried it myself, but I believe the "dpkg-reconfigure xserver-xorg" is used to write a new xorg.conf from scratch.  If I understand you correctly you are manually editing xorg.conf, then running this command, which overwrites the file you manually edited with an automatically generated xorg.conf.  Usually you run the command to generate a xorg.conf, **then** edit the file to tweak it (if necessary).

EDIT: Beat me to it! :)

---

### Post by Matsurosuka on 2007-12-23
wow, i feel stupid, i knew it wasnt that difficult last time i did it >.<
thanks much!

---

