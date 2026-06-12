---
title: "Update frozen when &quot;Configuring linux-firmware (amd64)&quot;"
date: 2017-02-09
forum: General Help
---

### Post by Kelley_Green on 2017-02-09
Help! 

I ran todays updates and on one one laptop it ran fine (Intel i5 CPU) but on the other, with an AMD CPU, it stopped while "Configuring linux-firmware (amd64)". 
Both are LXDE 16.04

This is where it's been frozen for about 5 hours:
Setting up linux-firmware (1.157.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic

I don't want to power it down in case I mess something up. 

Thank you for any help

Kelley Green

---

### Post by Kelley_Green on 2017-02-09
I got some help elsewhere but no matter what it always got stuck here:

update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic

---

### Post by ben2talk on 2017-04-16
Maybe end of the line. 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

Entering 'Sudo dpkg --configure -a'I now gives 'dpkg: error: parsing file '/var/lib/dpkg/updates/0011' near line 0:
 newline in field name '#padding'' so I can't

---

