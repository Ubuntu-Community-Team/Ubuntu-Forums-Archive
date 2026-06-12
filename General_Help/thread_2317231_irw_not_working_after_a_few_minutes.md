---
title: "irw not working after a few minutes"
date: 2016-03-14
forum: General Help
---

### Post by aurel130492 on 2016-03-14
Hi,

I have a PC with ubuntu server (with Gnome Shell).  I control this with a IR remote and irexec start on boot.

But, I have a problem with irexec. When my PC start, irexec works. But I doesn't work after many hours for example. I must reboot my PC for use irexec.

It's as if irexec stops after a countdown ...

irexec start on boot with "Software on boot" GUI of Gnome Shell.

Thanks you in advance

---

### Post by aurel130492 on 2016-03-16
Hi,

Yesterday, I left on my Ubuntu with Kodi started but inactive while 5 hours and irexec remained active (kodi use lirc).
 
irexec must have a delay but I can't found who change this setting ...

Thanks you

---

### Post by HermanAB on 2016-03-16
Well, until you figured it out, you could restart it periodically from /etc/cron.hourly.  

Just make a three line script:
#! /bin/bash
killall irexec
irexec

---

