---
title: "non-graphical login"
date: 2007-02-25
forum: General Help
---

### Post by danielsbrewer on 2007-02-25
Hi,

I would like to change the runtime so that it starts with a command line login as I am running my machine headless.  I would normally run /etc/inittab, but that does not seem to be present as Ubuntu uses "Upstart".  Does anyone know how to do this?  If possible it would be useful if I could do it without connecting the box up to a monitor and didn't have to uninstall gdm.  Thanks

---

### Post by taurus on 2007-02-25
A quick and dirty way is to remove gdm.

```
sudo aptitude remove gdm
```
Reboot and see if it drops you directly into a console.

---

### Post by danielsbrewer on 2007-02-26
The problem with that approach is what do I do if I want to start up a graphical login?  Thanks for the reply anyhow.  Anyone else got any ideas?

---

### Post by golfing22 on 2007-03-05
[URL="http://ubuntuforums.org/showthread.php?t=349517"]http://ubuntuforums.org/showthread.php?t=349517
[/URL]
I just followed that article and it works great except for once I manually start gdm, I don't know how to shut it back down.

---

