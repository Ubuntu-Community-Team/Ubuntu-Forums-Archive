---
title: "xorg.conf and live CD issue"
date: 2014-12-14
forum: General Help
---

### Post by xeriouxi on 2014-12-14
Hi!

I've got a mouse that requires some modification in the xorg.conf file before it can be used, as the mouse clicks don't register correctly. The problem I have is that I need to install Ubuntu before I can edit this file, as the problem is present when using the live session. Does anyone know how I'd alter the xorg.conf file in a live environment to allow me to install Ubuntu?

Many thanks! =)

---

### Post by carlwsnyder on 2014-12-14
Unless you want to do your own re-spin of Ubuntu for the Live disk, you probably want to use the Minimal CD [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD) or Server media [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server) , neither of which uses a GUI to install Ubuntu, so that you can create an xorg.conf prior to starting X.

---

### Post by ajgreeny on 2014-12-14
Are you simply trying to install ubuntu or do you want to use it for some other purpose?  If the latter you will have to write a new /etc/X11/xorg.conf file when you have booted into the live session.

If you already have a copy of the file you need, put it onto a USB drive, boot to your live system, and if using the GUI is not possible, hit Ctrl+Alt+F1 to get to a command line, then with command line move the xorg.conf file to /etc/X11.

Then logout, (don't reboot or you will lose the new xorg.conf file and be back where you started) and then, using this new xorg.conf file you should be able to boot to a working mouse.  If you want or need to be able to shutdown and keep that xorg.conf file it might be possible by making a live system with persistence, but I'm not sure if system files you have added will remain or if it is just files in the live system's own /home.

---

