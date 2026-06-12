---
title: "An easy way to edit /etc/X11/xorg.conf???"
date: 2005-10-23
forum: General Help
---

### Post by daller on 2005-10-23
Hi There,

I'm writing a guide, and I need to know about an easy way to change "nv" into "nvidia" (or "ati" into "fglrx")

...I don't want to guide people all the way through xorg.conf, and dpkg-reconfigure xserver-xorg is simply to complex!!!

Any suggestions?

---

### Post by Psquared on 2005-10-23
why not just "sudo gedit /etc/X11/xorg.conf"  ???

---

### Post by daller on 2005-10-23
...because then I have to write a whole essay about what to do...

A GUI-way would be the best thing - But I guess that's to much to ask for...

I'm thinking about something about:

sed s/"nv"/"nvidia"/g /etc/X11/xorg.conf > /etc/X11/xorg.conf

...but it's not working...

---

### Post by arcanistherogue on 2005-10-23
nvidia-config-enable 1?

something like that...

---

### Post by az on 2005-10-23
Instal nvidia-glx-config and run

sudo nvidia-glx-config enable


However, I do not understand why that is not run by default as a postintall script in the debian package. (like it could be a yes/no question that defaults to yes (all packages in main are installed with the "take the default" flag anyway.  There is absolutely no reason why you would want to instal that package without enabling gls anyway.

Removing the package runs the disable scritp AFAIK...

perhaps this should be a feature request.  I do not own the hardware, so I can't do it...

---

### Post by motin on 2008-01-26
Try Gutsy's Graphics setup dialogues and the application xorg-edit if that doesn't cut it.

---

