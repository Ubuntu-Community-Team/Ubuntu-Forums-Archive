---
title: "Ubuntu server 12.04 terminal only using half the monitor?"
date: 2013-05-09
forum: General Help
---

### Post by roseysdaddy on 2013-05-09
I have no gui installed on this system, its all terminal.

Ive tried adding

GRUB_CMDLINE_LINUX_DEFAULT=”vga=789&#8243;
GRUB_GFXMODE=800x600

to grub and updating, and the monitor tells me that the resolution is infact 800x600 while booting grub ( and the text uses the entire screen), but once the "kernel" loads and all of the services start to load and say [ok]  thats when the monitor reverts back to 1600x900 and the output is once again back to only using about half the screen.  Any help would be massively appreciated.

---

### Post by dino99 on 2013-05-09
you should let the kernel doing its own job : 
- the vga= thing is deprecated (remove it)
- if you does not have gui, why then using gfxmode ? (comment it out)
- be sure to have that /etc/default/grub line uncommented : GRUB_TERMINAL=console

and end up with:
sudo update-grub

---

### Post by roseysdaddy on 2013-05-09
thank you for the reply. 

ok, i did everything you said, and now im back to square one.  Big monitor with little tiny words, and it only uses half to two thirds of the screen.  Its fine when its booting, but once it "loads" thats when the screen changes.

---

### Post by roseysdaddy on 2013-05-09
this machine is a laptop that the screen was broken on.  ive removed the screen and the cables.  i wonder if this issue is because ubuntu is picking this up and only outputting the resolution that the internal screen could view?

---

