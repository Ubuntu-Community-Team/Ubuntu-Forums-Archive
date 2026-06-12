---
title: "Mounting existing raid 0"
date: 2006-12-02
forum: General Help
---

### Post by rothnic on 2006-12-02
Hi, im using this guide [http://ubuntuforums.org/archive/index.php/t-2557.html](http://ubuntuforums.org/archive/index.php/t-2557.html)
to mount my raid 0, and every time i do ./configure then sudo make install in the untarred device mapper folder, the /dev/mapper directory never exists. So im guessing that its not installing it.

---

### Post by rothnic on 2006-12-02
Ok, well i used synaptic to to install dmraid, and when i do ls /etc/mapper all i get is, CONTROL. What am i doing wrong where im not seeing the device names?

---

### Post by rothnic on 2006-12-02
this is what i get...

nick@nick-desktop:~$ sudo dmraid -r
/dev/sda: nvidia, "nvidia_djbacaib", stripe, ok, 488397166 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_djbacaib", stripe, ok, 488397166 sectors, data@ 0
nick@nick-desktop:~$ sudo dmraid -ay -v
nick@nick-desktop:~$ ls /dev/mapper
control
nick@nick-desktop:~$ 

Any help is appreciated

---

