---
title: "Installed a new windows after my recovery broke. Can't boot to ubuntu."
date: 2014-10-11
forum: General Help
---

### Post by bigt2 on 2014-10-11
I installed ubuntu on a new partition, everything went fine untill my windows broke. Had to download windows 7 home premium again because my recovery partition failed. After that I just installed windows from a bootable USB instead of telling linux to install it next to itself. I lost my purple bootmenu, and when I press F8 during the boot it only recognises the drive not the partitions. Shouldn't be such a big deal if it wasn't for all the work I did on my Linux partition wich I can't back up from windows, so reinstalling is not an option. 

How can I get a complete bootmenu, when both linux and windows 7 are on the same drive? This is quite annoying because of a closing deadline :/

---

### Post by sudodus on 2014-10-11
Welcome to the Ubuntu Forums :-)

I don't know how much Windows destroyed: Only the bootloader or the whole Ubuntu partition(s). I think and hope that the Ubuntu partitions are untouched by Windows. In that case you ***boot a live session of Ubuntu*** from a DVD or USB drive (made from the Ubuntu desktop iso file). You can do most things in that session, including reading and writing files in the Ubuntu partition(s) of the internal drive.

From the live session you can also try to re-install the grub bootloader according to this link

[https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2](https://help.ubuntu.com/community/Grub2/Installing#Reinstalling_GRUB_2)

---

### Post by coffeecat on 2014-10-11
As this is really an Ubuntu question - recovering Ubuntu after installing Windows - I've moved this out of the Other OS section.

*Thread moved to **General Help**.*

Good luck!

---

### Post by bigt2 on 2014-10-17
I forgot to thank you for your quick response, did not yet succeed in installing the bootloader. Will try harder once I have more time.

---

### Post by sudodus on 2014-10-18
Good luck, and please come back for more help if necessary :-)

---

