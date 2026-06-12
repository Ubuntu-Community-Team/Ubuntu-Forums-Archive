---
title: "Is there a safe mode with Ubuntu?"
date: 2008-06-13
forum: General Help
---

### Post by grs on 2008-06-13
I installed Ubuntu Studio on a Pc with an LCD monitor and set the graphics to the highest setting, since then I have moved the PC and changed the monitor to one of lesser quality. When I turn it on the mobo starts up fine but the once the OS kicks in the image stops because the monitor can't handle it.
Can I start Ubunut in a safe mode with reduced graphic settings so I adjust the setting for the second monitor?

---

### Post by reesje on 2008-06-13
Hi,

I don't know if you can call it safe mode, but you can hit CTRL+ALT+F2 and get a non graphical login. You can the login and edit your /etc/xorg.conf or restore any backup copy you may have (whatever app you used for setting your resolution may make such a copy automatically). You can use vi to edit your xorg.conf file.

BR,
René

---

### Post by aysiu on 2008-06-13
Just to piggyback on what René said: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
sudo /etc/init.d/gdm restart
```

---

