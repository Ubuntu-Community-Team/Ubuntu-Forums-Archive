---
title: "[SOLVED] sabayon overwrote grub"
date: 2007-11-06
forum: General Help
---

### Post by mick222 on 2007-11-06
Disk /dev/sda: 81 GB, 81956689920 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System 
/dev/sda1   *           1        2092    16803958   83  Linux
/dev/sda3            2093        4720    21101377   83  Linux
/dev/sda4            4721        9777    40612320   83  Linux
/dev/sda2            9778        9964     1494045    5  Extended
/dev/sda5            9778        9964     1494045   82  Linux swap
hi this is my hdd setup 
/dev/sda1 is ubuntu gutsy
/dev/sda3 is sabayon 3.4e
i can boot from grub to ubuntu but don't know how to add sabayon to the grub menu any help would be greatly appreciated.
ps is the setup ok and sorry i know similar questions have been asked 
 i ran sudo gedit menu1st in terminal but only got a blank page

---

### Post by Maestro23 on 2007-11-06
It's **/boot/grub/menu.lst (lower case L)**

---

