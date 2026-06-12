---
title: "Beaglebone crashed - restarted -can login via ssh but some commands don't work..."
date: 2016-09-05
forum: General Help
---

### Post by JimLS on 2016-09-05
Beaglebone black with:
Ubuntu 14.04.5 LTS (GNU/Linux 3.14.37-ti-r57 armv7l)
crashed.  Trying to figure out why.  I can ssh in (headless system) and do some things including access a drive on another box I had setup.  I can't connect via Filezilla which worked before.  Tried to copy log files to the remote drive but the command just hangs.  Some commands seem to do the same.  For example, I tried to shutdown thinking I could copy the sd card for further examination and the shutdown command hung.  I could ctrl-C to get the prompt back.  Any ideas of what to look at?  I am a newbie on digging through log files.  Not sure if the sd card is dying or some other issue.  If it is the sd card I need to figure out why it only lasts a month - this has happened several times.
Base image is from:   [http://beaglebone-asterisk.raspbx.org/](http://beaglebone-asterisk.raspbx.org/)
with updates after boot.

---

### Post by JimLS on 2016-09-05
I pulled the card and put in a fresh one.  Meanwhile, I am looking at the card from the crashed system.  It looks like the card is full or nearly full.  The syslog file is 2Meg and is filled mostly with serial issues:\\

Sep  2 06:39:14 raspbx kernel: [87778.132735] init: serial main process ended, respawning
Sep  2 06:39:24 raspbx kernel: [87788.246689] init: serial main process (12816) terminated with status 1
Sep  2 06:39:24 raspbx kernel: [87788.246929] init: serial main process ended, respawning
Sep  2 06:39:35 raspbx kernel: [87798.384834] init: serial main process (12818) terminated with status 1
Sep  2 06:39:35 raspbx kernel: [87798.385122] init: serial main process ended, respawning
Sep  2 06:39:45 raspbx kernel: [87808.501405] init: serial main process (12820) terminated with status 1
Sep  2 06:39:45 raspbx kernel: [87808.501649] init: serial main process ended, respawning
Sep  2 06:39:55 raspbx kernel: [87818.657450] init: serial main process (12822) terminated with status 1
Sep  2 06:39:55 raspbx kernel: [87818.659163] init: serial main process ended, respawning

I have an arduino Uno connected by USB and am sending some short messages back and forth but they are VERY infrequent.

---

