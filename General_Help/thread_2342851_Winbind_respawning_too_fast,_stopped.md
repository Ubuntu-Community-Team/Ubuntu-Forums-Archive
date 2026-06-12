---
title: "Winbind respawning too fast, stopped"
date: 2016-11-10
forum: General Help
---

### Post by cscj01 on 2016-11-10
I am running Ubuntu 14.04.5 x64.  For a good while now, each time I have a kernel upgrade, the new kernel will not reboot, and I get a series of messages (too fast to read), the last of which is "Winbind respawning too fast, stopped."  I then have to drop back to my previous kernel.  After running on the older kernel for a period of time, I can reboot with the newer kernel.  I did a search on Google and found some folks having the same issue that was related to Samba.  Here is what I get with dmesg```
 dmesg | grep winbind
[   37.658588] init: winbind main process (2189) terminated with status 1
[   37.658597] init: winbind main process ended, respawning
[   37.682837] init: winbind main process (2220) terminated with status 1
[   37.682846] init: winbind main process ended, respawning
[   37.706653] init: winbind main process (2226) terminated with status 1
[   37.706661] init: winbind main process ended, respawning
[   37.730453] init: winbind main process (2232) terminated with status 1
[   37.730462] init: winbind main process ended, respawning
[   37.753899] init: winbind main process (2238) terminated with status 1
[   37.753908] init: winbind main process ended, respawning
[   37.780157] init: winbind main process (2244) terminated with status 1
[   37.780166] init: winbind main process ended, respawning
[   37.803454] init: winbind main process (2250) terminated with status 1
[   37.803463] init: winbind main process ended, respawning
[   37.827721] init: winbind main process (2256) terminated with status 1
[   37.827730] init: winbind main process ended, respawning
[   37.851113] init: winbind main process (2262) terminated with status 1
[   37.851123] init: winbind main process ended, respawning
[   37.874178] init: winbind main process (2269) terminated with status 1
[   37.874187] init: winbind main process ended, respawning
[   37.897302] init: winbind main process (2275) terminated with status 1
[   37.897311] init: winbind respawning too fast, stopped
```I do not use Samba for my LAN; I use NSF.  However I do have two instances of Windows running in VirtualBox where I have a shared folder that is my data disk on my computer.  I am not sure whether the VirtualBox shared folder uses Samba.  My question is, could I safely remove Samba from my system ?  If not, is there a solution to the respawing issue?

---

### Post by cscj01 on 2016-11-11
Well, I decided to remove Samba with```
sudo apt-get purge samba
sudo apt-get update
sudo apt-get autoremove
```The purge took care of the complete removal, so there was nothing in the last two commands.  The messages no longer appear.  Perhaps someone needs to fix something with Samba V4.

---

