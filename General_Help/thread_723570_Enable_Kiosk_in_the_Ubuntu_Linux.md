---
title: "Enable Kiosk in the Ubuntu Linux"
date: 2008-03-13
forum: General Help
---

### Post by ubuntoexpert on 2008-03-13
hello,

I want configure my linux machine ( ubuntu linux - debian based ) for a "kiosk machine" using rdesktop as main application - after boot, starts xserver and run rdesktop only.

The XServer installed is Gnome.


In the past, i do this configuration in the RedHat linux, and now, i don't know do it on the debian environment.

Tanks

---

### Post by sumguy231 on 2008-03-13
I've never done anything like that, but I imagine the first thing you will want to do is disable GDM and add an upstart script which starts the X server with startx on bootup. You will probably want to add the DontZap option to your /etc/X11/xorg.conf, which will prevent X.org from quitting when Ctrl+Alt+Backspace is hit. Then you will need to place rdesktop in your .xinitrc or .Xsession script (I don't remember which one, make one a symlink to the other); it should look something like this:
```
#!/bin/sh
rdesktop

```

Then I suppose it comes down to locking down rdesktop. There's probably a nice utility out here to do all this for you, but I guess that will do the job.

---

### Post by aysiu on 2008-03-13
I don't know much about it, but Pessulus is what you're looking for.

---

### Post by ubuntoexpert on 2008-03-15
> **sumguy231 said:**
> I've never done anything like that, but I imagine the first thing you will want to do is disable GDM and add an upstart script which starts the X server with startx on bootup. You will probably want to add the DontZap option to your /etc/X11/xorg.conf, which will prevent X.org from quitting when Ctrl+Alt+Backspace is hit. Then you will need to place rdesktop in your .xinitrc or .Xsession script (I don't remember which one, make one a symlink to the other); it should look something like this:
```
#!/bin/sh
rdesktop

```

Then I suppose it comes down to locking down rdesktop. There's probably a nice utility out here to do all this for you, but I guess that will do the job.
Thanks for ur answer.

---

