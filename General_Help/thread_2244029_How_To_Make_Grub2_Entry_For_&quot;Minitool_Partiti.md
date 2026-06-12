---
title: "How To Make Grub2 Entry For &quot;Minitool Partition Wizard Home Edition ISO&quot;"
date: 2014-09-13
forum: General Help
---

### Post by randy12 on 2014-09-13
hi guys i want to make grub2 custom entry for minitool partition wizard home edition iso plz help me......thnkx in advance

---

### Post by yancek on 2014-09-13
Burn it as an image to a CD/DVD, or use whatever windows software you have to put it on a flash drive if you can.  It is windows software and I doubt you will get it to boot from a Grub entry with it on your system somewhere.  Good luck.

---

### Post by randy12 on 2014-09-14
bro i knw i can boot it from cd/dvd or from usb but i want it to boot  from grub without using cd/dvd/usb jst like i did with clonezilla i put  its iso in grub.d iso folder and made its custom entry in grub so now i  can boot into clonezilla without a usb or dvd or cd similarly i want a  solution that how can i make a grub entry for minitool partition wizard .

---

### Post by yancek on 2014-09-14
Clonezilla is Linux software, your Mini Partition wizard is windows software.  
Grub2 is capable of booting an iso but it is not capable of booting any iso.

---

### Post by oldfred on 2014-09-14
ISO must be configured to boot with grub2's loopmount.

If you want partitioning tools to boot directly use gparted's ISO or partedmagic's ISO. I have both of those booting from grub.

Link to examples shows both gparted & partedmagic.

 This will boot an ISO from a hard drive or any second drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by randy12 on 2014-09-14
oh i dint knew tht sorry bro u can delete this post thnks for yr help

---

### Post by randy12 on 2014-09-14
hey bro i went through the links but there un example i cant find for my minitool partition wizard iso plz bro can u make me a custom entry plzzzzzzzzzzzzzz plzzzzzzzzzzzz the iso name is pwhe811.iso and its is stored in 'hd0,msdos6'  its folder is etc/grub.d/iso/pwhe811.iso

---

