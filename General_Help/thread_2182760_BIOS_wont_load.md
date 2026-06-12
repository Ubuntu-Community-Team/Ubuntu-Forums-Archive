---
title: "BIOS wont load"
date: 2013-10-22
forum: General Help
---

### Post by HectorFromArgentina on 2013-10-22
Hi, this is really annoying for me, i tried to install ubuntu on my computer, and now i cant get ride of the system, looks like ubuntu and grub take over my pc.
I will try to explain what happens, and why im saying this...
About my computer:

Samsumg Ultrabook 530U3C
I have NO cd reader or dvd reader, i only have USB ports on my notebook.
My notebook have 2 hdds primary 500gb, secondary 24gb SDD.
By default the sistem ONLY uses the 500gb hdd.
It comes by default in 2 partitions, primary, and backup setted with samsung configuration recovery system...
It comes with windows 7. I installed on windows a lot of things, so i decided to format the pc, and have 2 os... ubuntu and windows 8...
The point was... without cd or dvd i only could use usb or the same HDD for install ubuntu.
What i did then? i formatted the samsung configuration recovery partition (30gb) and i installed on that partition the ubuntu iso CD downloaded from the website (12.04 LT). I reboot my PC, and i started the ubuntu installer, when it appears, i installed the ubuntu system at the SSD (24gb) partition. Then... i notice that pushing F2 the bios doesnt open anymore. Why? why cant i acceed to my bios for change the boot order and try to boot from usb? Now i cant use the bios, it doesnt work... Before i installed ubuntu, when i pushed F2 the bios worked fine.. now it doesnt appear, it only appears the grub, and i cant format or boot my pc for windows, and i need windows for a lot of things that i cant be able to do on linux (adobe, and developer tools).
This is a big problem for me, i tryed a lot of things, but it doesnt work, i trying holding F2 pushing it many times, try with f4, f10, f12, del, supr... everything but the bios gone... I tried to open the notebook, removing the hdd but the hdd i can remove is the 500gb looks like the 24gb ssd cant ve removed from the notebook, please help, i just want to format my pc with windows 8 and then, reinstall ubuntu or debian on the 24gb ssd. hope somebody can help me with this, thanks you a lot for read.

---

### Post by oldfred on 2013-10-22
You may have one of the buggy Samsungs. Orginally thought to be Linux, and Linux created a work around, but then found that Windows also causes it eventually.

 [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557) 

      
 UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
[http://mjg59.dreamwidth.org/25091.html](http://mjg59.dreamwidth.org/25091.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.
[http://mjg59.dreamwidth.org/23554.html](http://mjg59.dreamwidth.org/23554.html)

---

### Post by david98 on 2013-10-22
You must of installed ubuntu with UEFI enabled which has caused this problem. On the plus side this happened to me and my laptop was bricked so was unable to switch on never mind boot into bios. use the patch developed by matthew garratt this might work if not contact samsung directly that's what i did they made me send my laptop by courier and sent me a new laptop. I live in the uk and had a full warranty with my product. i would give them a ring and see what they say.

---

### Post by HectorFromArgentina on 2013-10-22
Well, i can do another thing... if you guys help me... i made a copy of Windows 8 at the 500gb disk... so if i can do a boot from grub of the 500gb i maybe can be able to install windows, and destroy the ubuntu partition, can i do it? i research but didnt found anything... look oldfred, can i give you my root and password, and you can connect remotely and do it¿ i just not good enough on ubuntu... and i need the pc for work... Anyway ubuntu works great, really fast, the problem is that i need a few things from adobe i dont have on ubuntu...

---

### Post by oldfred on 2013-10-22
No idea about remote, think that requires a working system. 

But if you cannot get into UEFI/BIOS that is a major issue. Have not followed recent changes, but in beginning some sent systems back to Samsung as Samsung had no solution.
Can you remove hard drive, and plug it into another system. Then you may be able to fix drive, but it still depends on what boot mode system defaults into?

Grub did add an entry to boot into UEFI/BIOS. It is the last one on the grub menu, if in UEFI mode, but is not added with all versions.

---

