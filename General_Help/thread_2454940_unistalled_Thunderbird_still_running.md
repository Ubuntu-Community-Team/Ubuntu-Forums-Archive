---
title: "unistalled Thunderbird still running"
date: 2020-12-09
forum: General Help
---

### Post by diffie-hellman on 2020-12-09
Hi Forum,

When I launched Thunderbird on Ubuntu 20.04 lately, i wasn't able to click anything within the window. I was able to close the window by a mouse-click on the "x" in the upper right, but when I started Thunderbird again, I experienced the same over and over. So I uninstalled (and re-installed several times) the application using

[LIST]
[*]the software center 
[*]```
apt remove thunderbird
``` 
[*]```
apt remove --purge thunderbird
``` 
[*]```
apt remove --auto-remove thunderbird
``` 
[/LIST]
and did several restarts, but nothing changed.

After uninstalling I looked for ```
ps -aux | grep thunderbird
``` and ```
john_doe     34973  0.0  0.0   9412   732 pts/0    S+   12:04   0:00 grep --color=auto thunderbird
``` was returned.

I wanna get rid of that phantom process and do a clean install of Thunderbird.

What should I do?


Thanks in advance.

---

### Post by vanadium on 2020-12-09
This is not a phantom process. It is you executing the ps ax command.

Move your own thunderbird profile out of the way: find the hidden folder .thunderbird in your home folder, and rename it to .thunderbird_old. Then restart thunderbird. It will start with factory default settings and you will need to set up your accounts again. If the problem is gone, you know it was due to a problem in your user configuration. If not, the problem indeed is somewhere in the system itself.

---

### Post by CatKiller on 2020-12-09
> **diffie-hellman said:**
> I wanna get rid of that phantom process and do a clean install of Thunderbird.

That result doesn't show Thunderbird running, it shows grep running.

---

### Post by diffie-hellman on 2020-12-09
> **CatKiller said:**
> That result doesn't show Thunderbird running, it shows grep running.

> **vanadium said:**
> This is not a phantom process. It is you executing the ps ax command.

Thx, sounds plausible.

Problem solved by moving my > **vanadium said:**
>  thunderbird profile out of the way .

---

