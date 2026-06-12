---
title: "CTRL+ALT+F1 broken?"
date: 2012-11-21
forum: General Help
---

### Post by matemargo on 2012-11-21
Every time I need to upgrade the NVIDIA driver, I'll do the following:

1. CTRL+ALT+F1
2. sudo service lightdm stop
3. install it

But now, after the latest kernel upgrades, every time I do the CTRL+ALT+F! thingy, the screen is completly black, without the loging prompt.

Is there any log file that I could post to help with this?
Anyone else is having this problem?

PS: The video card is a Geforce 310m
Ubuntu Version: 12.04 32bits
Kernel: 3.2.0-33

---

### Post by Wim Sturkenboom on 2012-11-22
I assume that <ctrl><alt><F2> .. <ctrl><alt><F6> also don't work. A workaround below

Make that grub displays the grub menu; it's standard in dual boot, else press <shift> while booting.

Press 'e' to edit the grub menu entry, find the line that contains 'quiet splash' and change 'quiet splash' to 'quiet splash text'. Press <ctrl>X to boot; this way the system will not start the graphical environment and you will end with a console.

---

### Post by CaptainMark on 2012-11-22
or add nomodeset to the end of this line, this has often got me out of a pickle in the past with Nvidia drivers

---

### Post by steeldriver on 2012-11-22
fwiw the CTRL-ALT-F1..6 switching on my NVIDIA-based laptop showed the same behavior - I had to comment out the nvidiafb framebuffer entry in /etc/modprobe.d/blacklist-framebuffer.conf file to get VTs to work - you may need to do the same if you want to enable VTs going forward instead of actually booting into a console mode every time

---

