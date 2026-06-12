---
title: "[SOLVED] Strangest things with Ubuntu"
date: 2007-10-27
forum: General Help
---

### Post by Lockheed on 2007-10-27
I installed 7.10 few days ago and so far I like it a lot.
Sometimes strange things happen. Occasionally NTFS windows partitions are not mounted on start or wireless connection is not enabled but all what I need to fix it is to start windows and then boot ubuntu again (in case of NTFS) or just reboot (wifi). 

However, today morning I started my Ubuntu and the wireless network I usually connect to was not visible:
[IMG]http://www1.zetosa.com.pl/telkom/wlanL.jpg[/IMG]

but when I boot to windows it is detected instantly:
[IMG]http://www1.zetosa.com.pl/telkom/wlanW.jpg[/IMG]

This situation continues ever since.
What's going on?

---

### Post by skymera on 2007-10-27
mine dosent appear sometimes, i have to reload network managaer.

sudo network-manager

and finally it shows up, just fiddle.
perhaps a bug?

---

### Post by Lockheed on 2007-10-27
I get "no such command" when I type it.
Anyway, it is not a random thing since it happens all the time since this morning.
The day before there was no such problem.

---

### Post by PelleK on 2007-10-27
You can *also* use the PrtScrn-button to take screen shots instead of using your camera.

---

### Post by Lockheed on 2007-10-28
Help... 
I really want to use Ubuntu but I am stuck to windows because of this strange situation.
Does enyone have an idea how to fix it? I lost 4 days for configuring the system to get it where it is now and I don't want to lose it.
I don't know if it has any relevance but the day before it stoped working I installed VMware with network connection bridget to wireless.

---

### Post by Crafty Kisses on 2007-10-28
That's super weird, I'll look into it.

---

### Post by Lockheed on 2008-02-11
I was perfecting my Ubuntu 7.10 installation using broadcom wireless card with ndiswrapper, however one time after boot up the window asking for key ring password didn't come up and on the taskbar there was only option of Manual Connection (before there was always Wifi symbol). I clicked it and moved the "tick" from wired connection to wireless. 
After next restart, wireless disappeared and I only have wired connection option.

I'm not sure what can I do next.

I like Ubuntu a lot, especially since I moved most of my programs from windows on it, but I observe that while XP often goes nuts for no apparent reason, also Ubuntu is not free from erratic behaviour.

EDIT:
Well, I seem to have fixed that with going through partial ndiswrapper setup process again.
I did  "sudo modprobe ndiswrapper " and reedited "/etc/network/interfaces" which changed its content since the last time I set it up.


As for the original issue stated in the first post, I did not find the solution. It just started working again after few days.

---

### Post by jan quark on 2008-02-12
please mark solved threads as solved :)

---

