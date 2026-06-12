---
title: "ubuntu wont boot. (sudo dpkg-reconfigure xserver-xorg)"
date: 2008-01-29
forum: General Help
---

### Post by jareddlc on 2008-01-29
so i just install ubuntu and im dual booting with vista, worked great for 1st hour till my friend suggested to type that command in terminal so i did, it told me what drivers i should be using so then i went into effects and gfx and set the drivers manually, then it asked me to reboot after that it wouldnot start up with with give a microcode error and it has something to do with thr display since when i hit ctrl + alt + del it says shutting down gnome display manager.  any suggestions how i can boot back into ubuntu. im a big ubuntu n00b, but as far as pc's i am very knowledgable dont be afriad to try to explain am i fast learner

---

### Post by steevols on 2008-01-29
Don't hit CtrlAltDelete, but instead hit CtrlAlt F2. This should bring up a login screen.

Punch in your username and password, then type "sudo -s" and enter your password again. This will put you into superuser mode.

Then, type "cd /etc/X11/" to switch to your Xserver's configuration directory.

Type "cp xorg.conf xorg.conf.backup" to backup your configuration.

Type "nano xorg.conf" to open your X file for editing, then scroll down till you find the "Device" section. You should see line starting with "Driver". Switch it from whatever it is now to
```
Driver "vesa"
```

Then, press CTRL-X to exit Nano, say yes when it asks you to save or not, and then type "/etc/init.d/gdm stop", and then "/etc/init.d/gdm start".

If all goes well, X should start up in VESA graphics mode.

---

### Post by jareddlc on 2008-01-29
thx for the fast reply, didnot fix it, so here is my error code

[44.84000] bcm43xx: error: microcode "bcm43xx_microcode5.fw" not available or load fail.

any suggestions? it was under driver the i810 for intel do i need to rename anything else? i changed it to vesa, which was originally vesa when i just installed it but i changed it manually. any suggestions would be greatly aprpeaciated if u need more info let me know and i will follow directions

---

### Post by steevols on 2008-02-06
Sorry for the late reply, haven't checked in on the forums for a week. (oops!)

Unless I'm mistaken, that's a broadcom wireless driver!

---

