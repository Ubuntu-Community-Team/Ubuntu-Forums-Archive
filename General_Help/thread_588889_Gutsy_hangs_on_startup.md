---
title: "Gutsy hangs on startup"
date: 2007-10-23
forum: General Help
---

### Post by rudlavibizon on 2007-10-23
**This post could be related to an Ubuntu bug filed at**: startup hangs help gutsy serious cannot boot  [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I re-installed gutsy today and it worked fine and when I rebooted it just hanged. I tried recovery mode, same thing. I tried several times and it always hangs at a different place. Please help, does anyone have the same problem since today, it worked fine the last couple of days. I reinstalled it for this same reason but I thought at that time it had something to do with the low latency kernel for which I had to reboot.

---

### Post by rudlavibizon on 2007-10-23
I went out for a few minutes and when I came back it was in this sort of shell (forgive my noobishness) called Busy Box (intramfs). What is going on?????? :confused:

---

### Post by rudlavibizon on 2007-10-23
OK, now I waited in recovery mode and here is what it shows :

Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev

ALERT! /dev/disk/by-uuid/d90037......347 (shortened, i'm typing this on my laptop) does not exist. Droping to a shell!


BusyBox v.1.1.3......bla bla bla

---

### Post by benmoreassynt on 2007-10-23
It's not recognising/mounting your hard drive. I had a similar thing (not connected to installing Gutsy, but a failing hard drive).

It could be a serious hard drive issue (it was for me). Try using the Ubuntu live cd to boot, and then see if you can mount the hard drive. Alternatively, you can try the same thing with the Knoppix live cd, which is a bit more set up for disk recovery.

Busy Box (intramfs) is a sort of pre-boot shell where you can do some things - including trying to mount the hard disk, if you're confident enough to try.

If you can get it mounted I'd immediately back up any un-backed-up files onto a thumb-drive or something. Trying to reinstall Ubuntu might be the best option.

Others may know better than me about ways to recover, but that was my recent experience.

---

### Post by rudlavibizon on 2007-10-23
So its the hard drive with ubuntu (I have four), right? Do you think that it is a hardware issue or just something with partitioning?

edit: I dual boot with win XP and everything is fine with it.

---

### Post by rudlavibizon on 2007-10-23
I'm in a live cd session now backing up data. How come live cd mounts it fine?

---

