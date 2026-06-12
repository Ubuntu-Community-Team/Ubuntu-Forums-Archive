---
title: "Computer Hangs when Gnome Desktop Loads"
date: 2007-02-24
forum: General Help
---

### Post by tonester on 2007-02-24
I was tinkering with the themes and icons in Edgy under preferences when nautilus quit. I tried to reboot when the desktop icons did not reappear. 

When I did reboot, everything loads fine until I get to the gnome splashsceen, where the computer hangs. The icons that loaded in the splashscreen itself do not even show up now (I believe one of them was metacity?)

Is there a command that I can use during recovery mode to reset the desktop?

Thanks in advance!

---

### Post by tonester on 2007-02-24
This article answered my question:

[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

Just have to re-customize again....  :)

---

### Post by zombiepkx on 2007-02-24
That happened to me the other day,

just try 

```
sudo dpkg-reconfigure xserver-xorg
```


Go through the whole thing, usually works.

---

### Post by tonester on 2007-02-24
Thanks for the tip - that's probably an easier way to solve the problem.  I'll have to try that the next time I botch up my desktop.

It seems to happen when I selected the "neutral" icon set under theme > themes details >icons. Perhaps the set is corrupt/not installed...

---

