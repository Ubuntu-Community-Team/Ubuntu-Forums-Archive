---
title: "Unable to see anything after enabling Nvidia drivers."
date: 2008-03-14
forum: General Help
---

### Post by Arcor on 2008-03-14
I installed Ubuntu 7.10, and Vista Ultimate (Dual Booting).
Of course the first thing you do when you install a new OS is to make it look how you want it to, so i was going through graphical settins until i stumbled on Desktop Effects, which were turned off.

I turned it on, it asked if i wanted to enable some Nvidia Drivers, i clicked yes, told me i needed to restart for the change to take effect.
Since then, every time i try to boot into Ubuntu, my screen goes black and my monitor displays the message "Out of Range 68.6 / 85 Hz".
I can't see anything, as far as i know Ubuntu is running fine in the background, but presumably due to these drivers, my monitor/graphics card can't display it to me.

My graphics card is a NVidia Gefore 6200 LE, approx total memory: 314mb.
I'm checking this info out in Windows Vista's DXdiag, not sure if that woud mean some is inaccurate or not useful.

Thanks in advance for any help.

---

### Post by kpkeerthi on 2008-03-14
From grub, boot into 'Recovery Mode' and then type
```

dpkg-reconfigure -phigh xserver-xorg
```
Choose nvidia for driver and the resolutions that your monitor supports.
Reboot and start in normal mode

If you continue to experience the problem, boot in Recovery mode again and type
```

dpkg-reconfigure xserver-xorg
```
Carefully choose the options, leaving the rest to default.
Reboot in normal mode.

---

### Post by Arcor on 2008-03-14
Thanks for such a quick, and helpful, response. First one worked great, and i'm now posting this from within Ubuntu.

---

