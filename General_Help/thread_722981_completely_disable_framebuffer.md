---
title: "completely disable framebuffer"
date: 2008-03-13
forum: General Help
---

### Post by jakbeatz on 2008-03-13
i just installed 7.10 desktop on a brand new IBM x3550.  this machine has an ati rn50/es1000 which gave me no end of issues during the install (had to install in safe graphics mode).

i think now i'm having framebuffer issues, but i'm not entirely sure.  i haven't enabled anything specifically since the install (nothing added to /etc/initramfs-tools/modules or /etc/modprobe.d/blacklist-framebuffer and nothing added to menu.lst) and i've stopped gdm from starting on bootup, because i don't want it to boot into x (even though i need x installed (because this machine is going to be a vmware host so i need x to be able to run vmware-server-console from ssh -X).  What's happening is when it boots, after the grub screen, the screen goes completely black and i can't see a cursor but the display is on.  when i press enter, the screen comes back to life, but the test resolution is really weird looking - the font is really big and the resolution is all messed up (it's like text and the positioning of the text is set for a 1024x768 resolution, but the screen is only 640x480).

not sure if this makes any sense, but all i want is to have a proper 80x24 terminal.  the other reason why i don't want fb and i want a regular console is because i'm going to be doing serial console access to this machine, so i don't want fb or this wonky resolution to get in the way.

running startx turns on xorg and it looks fine.

any help is greatly appreciated.

---

