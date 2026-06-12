---
title: "[SOLVED] Can't see program title bars and console is just a blank white"
date: 2007-06-05
forum: General Help
---

### Post by jawinterton on 2007-06-05
I am really new to using Ubuntu (Feisty Fawn) and I'm running GNOME.  I was told to run these commands to add my widescreen resolution:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg

when I reconfigured I think I messed something up to cause this problem I'm experiencing (Can't see program title bars and console is just a blank white).  I also have Beryl running but don't think that is causing the problem because it was working for me just fine before I did this.  Please give me your advice.

---

### Post by aldeby on 2007-06-06
jawinterton,
if title bars are missing it could be a window manager problem, you can try lounching **gnomewm** from the shell or add **exec gnomewm** to .xinitrc file in your home directory to ensure it is running at every logon.

However notice you use are using beryl as a window decorator, which I don't (having an ATi video card :-( ). I don't know if this applies to you, however it should be safe to try.
Cheers

---

### Post by jawinterton on 2007-06-13
I have restored my backup of the xorg.conf file.  Now I can see the title bars and console is no longer just a blank white.  I think this would suggest that it is not a windows manager that is causing these problems.  I'm wondering now if it's my video card driver that doesn't want to do the 1440x900 resolution correctly.  --Very bizarre to me. How do I find out what kind of video driver I have running?

BTW... I have an **XFX GeForce 6800XT **video card.  My monitor is a **Viewsonic VA1912wb**.  

Thank you so much for your help.  :D

---

