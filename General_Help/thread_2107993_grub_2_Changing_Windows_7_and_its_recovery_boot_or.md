---
title: "grub 2 Changing Windows 7 and its recovery boot order"
date: 2013-01-23
forum: General Help
---

### Post by Claudio Bogado Pompa on 2013-01-23
Hello.
It is possible to put in the boot menu first Windows 7 and after Windows 7 recovery?
I changed the order renaming the /etc/grub.d directory.
It seams that the os-prober script includes both Windows 7 and its recovery partition.
How do I have to change the os-prober script to have Windows 7 over Windows 7 recovery in the grub2 startup menu?
Greetings from Paraguay.
Claudio Bogado Pompa.

---

### Post by oldfred on 2013-01-23
Most now use grub customizer as it is a gui and works. But you can do it manually by copying entries into 40_custom and turning off os-prober. Then you custom entries can be in any order with any description you want.

       New Grub Customizer works with 12.10
[http://www.webupd8.org/2012/09/grub-customizer-30-released.html](http://www.webupd8.org/2012/09/grub-customizer-30-released.html)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

    
       The Grub 2 Guide - drs305 also link to grub customizer
Ubuntu Community Documentation site
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by Claudio Bogado Pompa on 2013-01-24
Thank you very much!
grub-customizer works great!

---

