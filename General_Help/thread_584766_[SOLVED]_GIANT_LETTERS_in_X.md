---
title: "[SOLVED] GIANT LETTERS in X"
date: 2007-10-21
forum: General Help
---

### Post by mali2297 on 2007-10-21
Hi.

I made fresh installs of Xubuntu 7.10 i386 and Ubuntu 7.10 AMD64 yesterday. Both greeted me with giant letters when logging in through GDM. I can't see what I type in the small box and when XFCE starts, the menus, windows et cetera are unusable since they are gigantic. My 15'' screen can only show parts.

Besides GDM, I tried WDM but that didn't solve the problem. **If I start the X session with startx instead, all is normal** and I'm back in business. Therefore, I have simply removed the display manager. 

However, I would be interested to know where the problem is located. Has anyone got an idea? Am I the only one that has experienced this with Gutsy?

---

### Post by FTA on 2008-01-09
I have the same problem.

I ran: sudo dpkg-reconfigure xserver-xorg 

to set a new configuration, it works partially. I go back to the WDM and it still works BUT...it DOESN'T WORK if a reboot the system.

any suggestion?

---

### Post by mali2297 on 2008-01-10
It seems like we are not the only ones, see [this thread]("http://ubuntuforums.org/showthread.php?p=3609621"). There are some workarounds posted that you can try.

This problem together with the more serious issue of a buggy suspend to ram made me go back to Feisty. Perhaps I will make another trial in the days to come...

---

### Post by mali2297 on 2008-01-14
OK, my solution was to change driver for my ati graphics card, from the open source to the proprietary driver. If you have an ati card, you can try this.

Press ctrl+alt+f2 and login to the terminal. Type
```

sudo dpkg-reconfigure xserver-xorg

```
Change the driver to **vesa**. When you're done, press ctrl+alt+f7 to get back to graphical mode and then ctrl+alt+backspace to reset the X server (so your changes can take effect). 

Hopefully, you now have a graphical interface that you can work from (albeit ugly). Then open the restricted manager to install the proprietary driver for the graphics card. Restart X once again and you are done.

---

