---
title: "How to access ISO file. Help the nub."
date: 2008-05-20
forum: General Help
---

### Post by revival440 on 2008-05-20
Well long story short, my XP got totally corrupted so I installed Ubuntu. I have been happy with it but am unable to play any games I normally play on it. My friend made an XP iso for me to reinstall XP, its like 650mb and its on my desktop. I can already "mount" it, but mounting it only allows me to go inside the directory. Autorun.inf + setup.exe etc are in there. Is there anyway I can start the CD like it was a legit cd? Like how can I install XP again with this ISO without burning a disc (burners broken). Thanks :( I love ubuntu and am gonna be installing it on my older laptop but I built this rig for gaming and sadly game devs just don't <3 linux.


using feisty fawn btw

---

### Post by maddog39 on 2008-05-20
Yes. All you have to do is insert a blank CD and drag the ISO file into your blank disk and it will ask whether you want to burn it as an image or a file. Choose as an image and off you go. Simple as that.

---

### Post by revival440 on 2008-05-20
> **maddog39 said:**
> Yes. All you have to do is insert a blank CD and drag the ISO file into your blank disk and it will ask whether you want to burn it as an image or a file. Choose as an image and off you go. Simple as that.

:( I have no burner though :( is there anyway to do this without even burning or no.

---

### Post by Zach_the_Lizard on 2008-05-20
There is a way to do it for sure for Linux ISOs, but I am not sure exactly how it would be done for XP.

I know the general procedure would go something like this:

Mount the ISO with something like:

$ mount -o loop -t iso9660 /location/of.iso  ~/your_mountpoint

Then you'd copy the boot files to /boot (use sudo to copy it to /boot) and then edit /boot/grub/menu.lst to add the XP install option.

---

