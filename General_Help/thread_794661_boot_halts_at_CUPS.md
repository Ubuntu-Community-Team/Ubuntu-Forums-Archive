---
title: "boot halts at CUPS"
date: 2008-05-14
forum: General Help
---

### Post by noogs on 2008-05-14
Hi I am fairly new to ubuntu but know a bit. I am dual booting vista and ubuntu 8.04. I can start my computer get to GRUB and choose ubuntu but as it boots it stops about 75% of the way through and my computer reboots. When I choose to see whats going on behind the splash it seems that my computer stops booting when it tries to load CUPS and then it reboots. I can boot in to windows without difficulty. PLEASE HELP I hate using windows for everything!!!!

Recently I have tried uninstalling the CUPS package from the root shell. After this I could boot into ubuntu with no problem but because I need CUPS I tried to reinstall it. Half way through the install my computer rebooted. When i tried to boot into the root shell again to uninstall it again it got to the root shell but when I tell it to uninstall CUPS it tells me I have to run "dpkg --configure -a." When I try to run this it tries to start CUPS so that it can finish the installation i presume, but as you know starting CUPS is the problem so during this my computer reboots. I am still very confused. Any ideas will help. I think it may be a bad package but I cant uninstall the old one to put the new one in synaptic.

---

### Post by noogs on 2008-05-16
does anyone have any ideas i'm really deperate and have done everything i can think of.

---

### Post by noogs on 2008-05-16
i figured it out on my own. if you cant boot into the GUI and just the root shell type in 'dpkg --remove cupsys' then you should boot easily. once booted go into the synaptic package manager and completely remove cupsys. then once removed install it again and all is well.

---

