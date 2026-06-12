---
title: "HELP!! Resolution messed up.."
date: 2008-04-12
forum: General Help
---

### Post by jhyland87 on 2008-04-12
ok so I tried to enable dual monitors  following these instructions:
[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)

and I restarted X, I got  an error saying ubuntu was running in low graphics mode, so I restarted, went to recovery, and typed this.

sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf

then restarted, still got the same error.. I removed the graphics card, and Still got the error.

I then just went into the low graphics mode, and changed my resolution to 1680 x 1050 just as it should be, and chose nvidia glx as my graphics card, hit ok, and it said I need to logoff to activate this, I did so.. and it worked! then just to make sure it worked, I restarted the computer to see if it kept the settings, and now when I go into the generic ubuntu... its all static, only not moving static, its like a screen shot of static snow on a TV...

anyone know how I can reset all my settings to like a month ago or something???!!

---

### Post by russo.mic on 2008-04-12
sudo dpkg-reconfigure -phigh xserver-xorg

That'll rebuild your xorg.conf.

May I recommend you backup your xorg.conf next time?

Russo

---

