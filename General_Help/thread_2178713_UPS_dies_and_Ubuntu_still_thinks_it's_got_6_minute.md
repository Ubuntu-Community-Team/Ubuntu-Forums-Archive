---
title: "UPS dies and Ubuntu still thinks it's got 6 minutes"
date: 2013-10-04
forum: General Help
---

### Post by Fuzzplug Jones on 2013-10-04
New Ubuntu 13.04, updated after install, new APC Back-UPS Pro 1000 with the USB cable connected.

I have hacked on headless Linux boxes for years, I'm trying to learn how to do things the "right" way on the desktop this time. I'm aware I can install apcupsd and hack it from the command line, but I'd like to know why the following happens:

After plugging in the USB cable between the UPS and the computer, Ubuntu now shows "On Battery" settings and a status area showing the UPS battery level and whether it's on AC or not. A laptop-like battery icon appears in the menu bar.

I unplug the UPS from AC power. I notice that only occasionally does the time remaining on Ubuntu match the time remaining on the UPS. Seems like Ubuntu only updates the number every ten minutes or so. At one point the UPS said 14 minutes remaining, Ubuntu said 23. It appears - though I have no evidence - that Ubuntu isn't polling the UPS frequently enough to keep on top of the battery situation. Most modern PCs will fluctuate on the amount of power they're using, if something suddenly wakes up a hard drive or maxes out the CPU for a minute, so I figured Ubuntu would be watching the remaining time like a hawk.

When the UPS got to "0 minutes" remaining, Ubuntu still said 6. I had selected "Shutdown" in the Power options for what to do for a "critically low" battery, but Ubuntu just said "Low Battery - 6 minutes remaining." A few seconds later, the UPS ran out of juice and the Ubuntu box lost power.

I've been Googling for an hour now and all I keep getting is posts instructing me on how to install apcupsd on Ubuntu 8. I know I can do that, but I'm curious as to why the built-in UPS support doesn't work. Why include anything at all when I have to install apcupsd anyway?

---

### Post by tgalati4 on 2013-10-04
Normally you would only allow your PC to remain on battery for 1 minute or so then shut down immediately.  This will prevent shutdowns for minor power fluctuations and shut down the computer when power is off for a minute.  Anything else is risky because your batteries decline in capacity with age.  I've always used apcupsd and it polls every minute or whatever interval that you set.  I'm not sure how the current, built-in UPS framework works.

This is an older post, but it may have some information:  [http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/](http://blog.shadypixel.com/monitoring-a-ups-with-nut-on-debian-or-ubuntu-linux/)

If you have a server with a SMART UPS running on the same LAN, you can install apcupsd and set the server to Master and the other computers to Slave and then they will receive shutdown commands through the LAN.  Of course your switchgear would need to be on the UPS as well and the Master needs to stay up long enough so that all of the slaves get the shutdown message.

---

### Post by Fuzzplug Jones on 2013-10-06
That's all well and good, but how do I disable the UPS "support" in gnome-power-manager? Both apcupsd and NUT refuse to connect to the UPS because this built-in, broken POS grabs it automatically when the USB cable is plugged in.

---

### Post by JKyleOKC on 2013-10-06
I'm running Xubuntu so don't have the gnome-power-manager program to deal with, but you may find an answer to your problem by researching the **udev** rules; these rules get applied when devices connect/disconnect from the system (I use them to force multiple PICs to have consistent interface names but they apply to all devices). It's possible that a rule is present that forces the connection; in that case you could simply rename the rule to something that never gets applied (by adding "x" to the start of its filename, preventing udev from implementing it). If not, you can create a rule of your own to release the USB device from the original daemon and connect it to the one of your choice.

---

