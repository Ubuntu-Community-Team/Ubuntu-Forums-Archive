---
title: "Xorg / Resuce"
date: 2006-12-08
forum: General Help
---

### Post by Zeek00 on 2006-12-08
I have dual booted my computer. Windows XP and Ubuntu Edgy Eft. Upon playing around with the windows themes my Ubuntu screen resolution changed from 1024x768 to 640x480 upon rebooting.

Now when I put a different monitor on my computer, a newer flat screen, the screen resolution returns to 1024x768. And upon booting with the flat screen on my computer then switching out to the older monitor the screen res. stays the same. Any help on this one?

Finally, I was playing around with my xorg.conf file. I managed to erase my video driver setting. It was "nvidia" and I erased it, save it and closed out. When I rebooted, obviously, X-windows wouldn't start up. How do I get into just a command line with no graphics just to restore my xorg.conf file with a backup?

Thanks,

Zeek

---

### Post by taurus on 2006-12-08
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Zeek00 on 2006-12-08
yes that would be a wonderful solution, just need to solve getting into a terminal to do it. I can't start up ubuntu with a graphical nor non-graphical interface. i get the X-server error message, a chance to view the diagnostic and then nothing. 

So how do I get into a terminal to fix my problem?

---

### Post by yabbadabbadont on 2006-12-08
Try hitting ctrl-alt-F1.  If the machine hasn't locked up, that should drop you to the first text console where you can login.

---

### Post by taurus on 2006-12-08
Boot into recovery mode from GRUB menu and at the prompt, type

```
dpkg-reconfigure -phigh xserver-xorg
startx
```
If startx works, then reboot into normal mode with

```
shutdown -r now
```

---

### Post by Zeek00 on 2006-12-08
Gracias

---

