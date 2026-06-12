---
title: "Changing login resolution"
date: 2004-11-15
forum: General Help
---

### Post by hndrcks on 2004-11-15
I brought my home box to work to do the initial updates (T3 is nice for that) but the monitor I used for the install here at work was a little nicer than my home one - when I got my PC back home I was able to set the desktop resolution; but I can't figure out where the login screen resolution is set (it is currently set too high for my home monitor). Anyone know where the initial resolution setting is?

---

### Post by zenwhen on 2004-11-15
I would actually also like to see an answer to this.

---

### Post by ynef on 2004-11-15
To find out what config file gdm uses (the standard X config file, most likely) you need to go to /var/log/gdm and cat the latest one (which is called :0.log -- the others you have there are backups, if any). Let's suppose that it is /etc/X11/XF86Config-4 since that's what it is for me.

Right, now the X server will try to use the first display mode that you have listed in the "Screen" section in the depth that is set to be the default. So look at your line that says "DefaultDepth". Now go to the "Display" subsection that sets that particular depth. You will see a line of modes, listing them in some order. The first one is the one X will try first, and so on.

I guess that gnome, if you use the resolution switcher thing, does some non-standard thing to bypass this setting, since the XF86Config-4 is not writable by regular users. Please note that I don't know what the resolution switcher does, since I've never used it.

Anyway, try the steps I outlined above! Good luck.

---

### Post by hndrcks on 2004-11-15
That got it! /etc/X11/XF86Config-4 was mine too.

---

