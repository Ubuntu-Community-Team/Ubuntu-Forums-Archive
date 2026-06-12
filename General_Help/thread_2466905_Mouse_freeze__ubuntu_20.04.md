---
title: "Mouse freeze : ubuntu 20.04"
date: 2021-09-09
forum: General Help
---

### Post by akshaymalige on 2021-09-09
The mouse cursor freezes when I try to move it, dissappears on a key stroke and is later released only until i try to move it again. This is happening in multiple systems (3 PC's of mine) to be specific. It is bad enough that i have to ask for help using my phone. I have no problems with the keyboard, or playing some video. The system is not busy, has plenty of memory and no other background user applications. 
I have tried restarting the gnome and resetting the dconf, turning off the fractional scaling but no luck. 

Thanks in advance

---

### Post by monkeybrain20122 on 2021-09-09
Most likely because of kernel bug, there are multiple reports of upgrading to kernel version 5.11.0-34 breaks touchpad and/or mouse (happened to one of my machines). So reboot, when it boots, hit the ESC key (if it is uefi) or hold the left shift key (if bios) to bring up the grub menu, choose the advanced option, then choose the previous kernel (there should be at least 2 if you haven't deleted the previous one), boot into it. Check that your mouse cursor is moving ok. Then you can either use the command line or synaptic to remove the new, defective kernel. Then don't upgrade the kernel next time until there is a fix, or you can temporarily [pin the kernel version]("https://askubuntu.com/questions/999529/pin-kernel-version") and remove the pin when a fixed kernel is available

---

### Post by Raygreen on 2021-10-18
After I upgraded to 21.04 my pointer froze and would only work with an external mouse attached. I did find a fix. First I ran sudo modprobe -r psmouse && sudo modprobe psmouse proto=imps and that unfroze the cursor. To make it permanent I ended up updating GRUB by adding psmouse.proto=imps after quiet splash and saved it and rebooted and now my trackpad works.

---

