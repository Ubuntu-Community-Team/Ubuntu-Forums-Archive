---
title: "Grub On Extended Partitions"
date: 2008-03-02
forum: General Help
---

### Post by danielcc on 2008-03-02
i was moving around my partitions setting up my new hd tonight and i have seemed to of messed up grub and am not sure how to fix it... my partitions are:[an extended partition containing my ubuntu partition(/dev/sda5) and my swap(dev/sda6)] a [primary partition with my windows stuff(dev/sda2)] and a [fat32 primary partition(/dev/sda3)]... so my questions are how would i fix my grub to point to ubuntu and then windows, and i thought that sda was reserved for a removable devices so why why do my partitions say sda?... i have also tried the super grub tool, and it didn't work for me :(

any help would be would be much appreciated!!!!

---

### Post by danielcc on 2008-03-02
never mind yaw i figured it out... what i did was go into grub on startup and figure out what my ubuntu partition hda thingy was with the command "find /boot/grub/menu.lst"... i was having trouble changing the file stuff so i then found another way to edit the menu in grub, and changed (hd0,0) to (hd0,4) and then hit b for boot... for some reason it was reset every time on startup so i went to good oll terminal and typed sudo gedit /boot/grub/menu.lst then changed the (hd0,4) there, where i also saw an example for windows and added in my xp partition... i think where i went wrong was my (hd#,#)'s which turned out to be one less than the end so sda5 would be (hd0,4) since it is the first hd(and only hd i have).... so yeah good times good times lol

---

