---
title: "Hard disk partion name dissapeared"
date: 2007-02-16
forum: General Help
---

### Post by hoagie on 2007-02-16
Hello community,
Since yesterday that I booted into Ubuntu the /dev/sda2 partition that I have mounted on /media/Data appears as _PNG instead of Data. I can't understand why this happens. Can anyone help me fix this?

---

### Post by hoagie on 2007-02-17
Come on none knows about this?

---

### Post by roland on 2007-02-17
What kind of disk is /dev/sda2? Is it a (S-ATA) harddisk, or an USB-device? If it is an USB-device for removable storage, then hotplug will automagically mount it on /media/name-of-device. So if it is an usb-stick (for example) called _PNG, then it will be mounted on /media/_PNG.

---

### Post by hoagie on 2007-02-17
It's a sata disk, and it's mounted on /media/Data

---

### Post by roland on 2007-02-17
What is the entry for /dev/sda2 in the /etc/fstab file? I'm wondering whether you mounted the disk by yourself (i.e. by using sudo mount), or not. the strange _PNG should be somewhere, hopefully in /etc/fstab, those names are not generated randomly. You can retrieve the contents of it by typing gedit /etc/fstab in a terminal.

---

