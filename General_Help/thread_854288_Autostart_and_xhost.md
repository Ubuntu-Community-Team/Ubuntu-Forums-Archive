---
title: "Autostart and xhost"
date: 2008-07-09
forum: General Help
---

### Post by amba on 2008-07-09
Hi,
i'm running Boinc client ([seti@home project]("http://setiathome.berkeley.edu")) as user boinc:boinc in background. The GUI to manage works runs as my own user and connects to the engine. Everything works fine, except when i want to see the graphs (like the 3d screensaver under windows). The popup window runs as user boinc, so i must to give that command in shell:
```

xhost +

```

I would like to do it automatically at start. Folder /etc/init.d doesn't help me because this command should be given after X starts. 
I've seen that (K)ubuntu Hardy has a folder named Autostart in my home folder. I put there a bash script with "xhost +", i set the executable flag up, but it doesn't automatically run. I thought it is similar to /etc/init.d folder!

1) How does that Autostart directory work?
(interesting also for further scripts)
2) X provides a specific config file in my home for xhost options?
(the clean solution)

---

### Post by amba on 2008-07-09
duh i'm dumb.
Autostart works! The executable script in there get running properly when i log into kde, i didn't notice because my xhost directive was wrong (xhost +boinc@laptop adds a network entry, now edited with xhost +"local:boinc@").

First question is solved, now just curious if there is a config file specific for xhost directives!
:)

---

