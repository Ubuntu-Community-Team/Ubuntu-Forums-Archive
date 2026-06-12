---
title: "How Do I Set A Default Session In Slim?"
date: 2008-06-20
forum: General Help
---

### Post by Mark76 on 2008-06-20
At the moment I'm using WDM; because it remembers my last session. Slim doesn't and unless I choose it from the options I get logged into Gnome.

So how do I set a new default in Slim?

---

### Post by murchball on 2008-11-25
I've just started playing with slim and really like it, but this bug is bit annoying. The bug has been documented here: [https://bugs.launchpad.net/ubuntu/+source/slim/+bug/240101/](https://bugs.launchpad.net/ubuntu/+source/slim/+bug/240101/)
I tried the workaround that is listed but I haven't been able to get it to work. FWIW You can choose which session you want to start by pressing F1. The choices for this are in /etc/slim.conf

---

### Post by julakali on 2008-11-27
> **murchball said:**
> I've just started playing with slim and really like it, but this bug is bit annoying. The bug has been documented here: [https://bugs.launchpad.net/ubuntu/+source/slim/+bug/240101/](https://bugs.launchpad.net/ubuntu/+source/slim/+bug/240101/)
I tried the workaround that is listed but I haven't been able to get it to work. FWIW You can choose which session you want to start by pressing F1. The choices for this are in /etc/slim.conf


The workaround is:
Change the "login_cmd" line in /etc/slim.conf to:
```
login_cmd   exec /bin/bash -login ~/.xinitrc 
```

Create ~/.xinitrc with content 
```
#!/bin/sh
exec startfluxbox
```

Or similar ;)
(think its gnome-session for gnome)

---

### Post by kerryhall on 2012-04-20
Workaround works for me. I have this same issue. Still, after four years you would think this bug would get fixed. First one to fix it gets $10 paypaled to them from me. Will only paypal once, show me your commit, and I want it to work out of the box with whatever ubuntu distro is current after an apt-get upgrade. (debian too would be nice, does this issue exist with debian too? will check on that)

thanks!

---

