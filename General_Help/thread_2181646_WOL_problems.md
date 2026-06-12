---
title: "WOL problems"
date: 2013-10-18
forum: General Help
---

### Post by Bigfoot73 on 2013-10-18
I have some problems to get WOL working.

* It is enabled in bios
* sudo ethtool eth0 says "Wake-on: g"
* I have updated /etc/init.d/halt with "NETDOWN=no"

If I shut down the machine manually from the gui there is no broblem to wake it by sending a "magic packet".
But usually this machine is shut down automatically from a script that calls "shutdown -h now" and then it will not wake up.

So, what is the difference between those two shutdown methods?

---

### Post by papibe on 2013-10-18
Hi Bigfoot73.

A few thoughts:

The fact that the machine shutdown by itself makes me think the problem may relay on the lost of the arp table over the network.

What tool are you using to wake up the computer?
What exact command are you running?

Also, I would recommend trying the same GUI version of the shutdown command, but forcing no dialog box:
```
sudo gnome-session-quit --power-off --force
```
Let us know how it goes.
Regards.

---

### Post by Bigfoot73 on 2013-10-19
I tried "sudo gnome-session-quit --power-off --force" and got some error: "** (gnome-session-quit:8651): WARNING **: Failed to call Shutdown: The name org.gnome.SessionManager was not provided by any .service files".

For now I'm using the web interface of my router with tomato firmware to send the magic packet. I just enter the mac address so I don't think there is any ARP table dependencies.

But appearantly I have been messing around with something now, because I got another problem instead! After shutdown with "shutdown -h now" it will always restart after a few seconds. (Unless I unplug the ethernet cable. On the other hand, if I unplug the cable and then plug it back WOL now works as expected.)

Even if I get the "sudo gnome-session-quit --power-off --force" working I'm not sure I can use that instead. The computer also needs to be able to wake on timer (using MythTV for scheduled recordings) and there might be some problems with that if it is shutdown the "usual" way. (At least I had some problems with that when I first configured it a year ago and a number of forum threads suggested that it needed to be shutdown in a certain way.)

---

### Post by Bigfoot73 on 2013-10-22
After a bios update it now works slightly better. (I also upgraded from 13.04 to 13.10 but that didn't make any difference.) WOL works just fine. When shutting down it will sometimes restart, but not everytime as before. I have no idea why it is restarting, but it seems to happen if I have been logged in.
(The computer will shut down again after five minutes if there are no active recordings and no one is logged in. So an extra restart + 5 minutes uptime sometimes is not a major problem.)

---

