---
title: "Using Ubuntu as a NAS"
date: 2013-04-01
forum: General Help
---

### Post by ultraloveninja on 2013-04-01
So, I've constructed a NAS box and I've installed Ubuntu on it.

I've got a 3TB HDD that I've already formatted and I've got Samba up and running on it as well.

I got VNC going and I'm using Chicken of the VNC to remote into it, if I need to.

However, if I reboot with out a monitor on the new NAS box, there's some sort of resolution check that it goes through before it comes online.

Is there anything I can do to disable that? Also are there any other suggestions/options that I should be doing to make this a efficient NAS box? Thanks!

FYI - It's been a while since I've used Ubuntu. The last version I messed around with was Hardy.

---

### Post by tgalati4 on 2013-04-01
You could probably create a /etc/X11/xorg.conf file with a single, correct resolution and the system will attempt to use that.  Without a monitor, the xorg server will try to guess the resolution, but with no monitor attached, it will have a hard time.  There might be a "headless" switch.  

I removed the graphics card on an old freenas server that I set up.  It has a web-based administration page, so you don't need a monitor.  Unless you have trouble booting after a power outage--then a monitor becomes necessary.

A lot has changed since Hardy.

---

### Post by ultraloveninja on 2013-04-01
Yeah, there have been A LOT of changes since Hardy.

Anyways...I'll try to see if I can mess around with the xorg file. Or do you think I should just start over and use FreeNAS instead? I was thinking about it, but now that I look at it, I might go down that route.

---

### Post by Lars Noodén on 2013-04-01
FreeNAS has gotten really heavy of late.  You're probably better off with Ubuntu.  If you can, I'd recommend uninstalling the graphical bits and using the shell.  The shell is much more powerful, fast  and flexible once you are used to it.  It is well worth the small effort.

---

### Post by tgalati4 on 2013-04-01
If you want the lightweight version of freenas then use the fork:  [http://nas4free.org](http://nas4free.org).  I've been running it for years.

---

