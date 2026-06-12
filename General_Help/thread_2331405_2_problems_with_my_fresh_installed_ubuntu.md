---
title: "2 problems with my fresh installed ubuntu"
date: 2016-07-21
forum: General Help
---

### Post by naxon2 on 2016-07-21
**_Issue no. 1_**

[COLOR=#111111][FONT=Ubuntu]I just migrated from Windows to Ubuntu. On windows, I was using dual 27" dell monitors, one connected through an HDMI and the second with a mini docking station usb 3-c to hdmi (stlab u-1200).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]On Ubuntu it doesn't seem to work. It doesn't recognize the adapter.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any way to make it work?
[B][U]
Issue no. 2[/U][/B]

[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]I just updated to bluez5, and now whenever I restart my computer, it gets stuck on the restart screen until I force it to turn off with the power button (It can be stuck like that for hours).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]When Installing bluez5, the installation was stuck on:

> Installing new version of config file /etc/init.d/bluetooth
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]For hours. I has to exit the terminal.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Any ideas?

UPDATE

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]It also doesn't let me install apt-get packages. I already killed the only running process and deleted the lock file (also from cache).[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]This is what I get:

> E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
 E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]
Btw, I'm using Ubuntu 14.04.[/FONT][/COLOR]

---

### Post by papibe on 2016-07-21
To fix this:
```
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? 
```
Try:
```
sudo rm /var/lib/apt/lists/lock

sudo rm /var/cache/apt/archives/lock

sudo dpkg --configure -a

sudo apt-get update
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by naxon2 on 2016-07-22
It fixed it, but still stuck on restart screen.

---

### Post by papibe on 2016-07-22
Could you describe the steps you took to install bluez5?

BTW, newer versions of Ubuntu already come with bluez5. I'd try Xenial 16.04.1 just released these days (upgrade from 16.04)

Regards.

---

### Post by gordintoronto on 2016-07-22
USB 3-c can be described as "the latest hardware." You should also use "the latest software" -- Ubuntu 16.04.

---

### Post by naxon2 on 2016-07-23
The only problem with this is that 16.04 caused a lot of problems when I installed it.. like no cursor etc... That's why I installed 14.04 instead because it's been a while out there and there's a wide range of knowledge about it...

And one more thing - the system seemed to recognize that there's a usb mini docking station (as I saw on the terminal), but it didn't display anything on the screen.

---

