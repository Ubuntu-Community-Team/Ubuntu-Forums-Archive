---
title: "mbmon : This program needs &quot;setuid root&quot; ?"
date: 2006-11-12
forum: General Help
---

### Post by Littleweseth on 2006-11-12
G'day folks;

I'm trying to get the CPU-temperature plugin for gnome/perlpanel to work with mbmon. I installed mbmon, but the plugin always reads 0 deg C - not something I'd mind, but obviously incorrect.

On running mbmon from a terminal, I get
lws@daedalus:~$ mbmon
InitMBInfo: Operation not permitted
This program needs "setuid root"!!

When run as root, the program works normally.

lws@daedalus:~$ sudo mbmon
Password: [$$$$$$]

Temp.= 36.0, 35.0, 41.5; Rot.= 2960, 2636,    0
Vcore = 1.66, 1.70; Volt. = 3.26, 5.13, 12.34, -12.04, -5.30

What's the least kludgy way to fix this problem?

Cheers;
-lws

---

### Post by Littleweseth on 2006-11-12
Oops, never mind. Deep probing of a thread I found on a BSD mailing list suggested sudo chmod +s /usr/bin/mbmon, which worked a treat.

---

