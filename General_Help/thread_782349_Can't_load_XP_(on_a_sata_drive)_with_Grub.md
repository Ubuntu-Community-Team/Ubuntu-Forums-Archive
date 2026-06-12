---
title: "Can't load XP (on a sata drive) with Grub"
date: 2008-05-04
forum: General Help
---

### Post by Straw_Dog on 2008-05-04
I installed 8.04 Hardy Heron and I am trying to configure Grub to allow a dual boot of Ubuntu and Windows. I did not have the windows drive connected during my Ubuntu installation.

I have 3 drives; 2 IDE and 1 Sata

Heron is on the Primary IDE and I have Windows XP on my Sata drive. The third drive (an IDE) is a secondary slave and contains only data.

Currently: I have my boot sequence set to load the Primary IDE first and the Sata second and the other IDE last.

I've been poking around in the forums and reading topics similar to my problem. I have used: *sudo gedit /boot/grub/menu.lst* to edit grub. One forum post instructed I paste the following to the end of the text but I've since done some tweaking to it because I thought perhaps it was looking at the wrong hd.

It currently looks like this...

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hd2
title Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

------------------
The title (Windows XP Professional) does show up in the Grub menu but selecting it gives me that scary windows message "NTRLD is Missing" (Windows loads fine if I change the boot order in the BIOS). Should the map entries say hd2? Can someone help me with the grub edit so that I can load Windows on my Sata drive? Thanks.

---

