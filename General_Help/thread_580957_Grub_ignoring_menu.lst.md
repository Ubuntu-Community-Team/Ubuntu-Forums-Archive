---
title: "Grub ignoring menu.lst"
date: 2007-10-19
forum: General Help
---

### Post by LeGollemux on 2007-10-19
I am running Ubuntu Server 7.04 with KDE as desktop. I have edited the menu.lst file under /boot/grub/ to get the correct kernel to load. 

But it seems that the changes are ignored and the original menu list is displayed. Anyone know why this is?

---

### Post by geirha on 2007-10-19
If you've changed any of the options starting with #, you need to run "sudo update-grub" after editing the menu.lst. (It's a good idea to always run that command after editing the menu.lst)

---

### Post by anaconda on 2007-10-19
Have you got more than one linux installed?

Maybe grub uses a menu.lst file from some other partition?

---

### Post by LeGollemux on 2007-10-19
I tried "sudo update-grup" but that wasnt it. I then then booted into the kernel that is being listed first in the menu and to see it was being used I changed the menu colours. 

Bingo. its reading the menu.lst file from a later install ( I was testing stuff ).

how do I fix this?  Somehow get rid of the later install??

---

### Post by forestpixie on 2007-10-19
I had that when I had feisty and gutsy - I used [supergrub]("http://supergrub.forjamari.linex.org/") - download it, burn as an iso and boot with it. It should find you're installations - you tell it which one you want.

---

### Post by LeGollemux on 2007-10-19
ok, problem solved for now. I just edited the menu.lst on the other partition and the machine now boots correctly.

Thanks for all the help.

---

