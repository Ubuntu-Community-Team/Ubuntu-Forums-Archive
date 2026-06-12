---
title: "upstart:  application (nemo) started when login; how to disable it."
date: 2016-10-08
forum: General Help
---

### Post by deragon on 2016-10-08
Greetings,

As you can see, nemo is started by upstart everytime I log in.  I want to disable it, but fail to find how.

```
USER       PID  PPID S %MEM %CPU COMMAND
hans      2494  2194 S  0.0  0.0 /sbin/upstart --user
hans      3090  2494 S  1.0  0.0 /usr/bin/nemo --no-default-window
```

I want to keep nemo on my system, but nautilus and nemo start upon login and there is a conflict between them regarding the handling of the icons found on the desktop.  I looked under /etc, ~/.local, ~/.config and other places I do not remember , searching for anything that would start nemo, to no vail.

Can someone explain how to debug upstart and where it reads it configuration?  I would like to disable nemo.

Best regards,
Hans Deragon

---

### Post by steeldriver on 2016-10-08
User upstart jobs would usually live in ~/.init I think - have you looked there?

---

### Post by deragon on 2016-10-08
Hi have no ~/.init.  Never heard of that directory.

---

### Post by deadflowr on 2016-10-08
It's actually starting through dconf:
to disable simply run
```
gsettings set org.nemo.desktop show-desktop-icons false
```

---

### Post by deragon on 2016-10-13
> **deadflowr said:**
> ```
gsettings set org.nemo.desktop show-desktop-icons false
```

That is it!  You solved my problem.  Thank you deadflowr.

---

