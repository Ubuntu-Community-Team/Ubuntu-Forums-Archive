---
title: "Bluetooth and speaker occasionally working on ASUS N550JV"
date: 2014-05-20
forum: General Help
---

### Post by Tianming_Chen on 2014-05-20
I use a ASUS N550JV laptop with Ubuntu 14.04 and Windows 8 dual boot. The Bluetooth module is atheros ar3012. Since the day Ubuntu is installed, the behavior of Bluetooth and speaker is weird. They are not totally dead. They sometimes work, but I find no pattern about when they  work and when they don't. Sometimes Bluetooth works right after start up. In other time, the Bluetooth icon does not show up in menu bar (I have "Show Bluetooth status shown in menu bar" checked in settings). When I enter settings, Bluetooth is shown to be off. Even though I can set it to On by clicking it, the device menu below still shows "Bluetooth is disabled" and I cannot search and add device (I use a Bluetooth mouse). Also, if I close the settings and open it again, Bluetooth will be set to off again. When the Bluetooth does not work, I checked /var/log/dmesg and the error about bluetooth is as follow:

```
[    5.032070] Bluetooth: Error in firmware loading err = -110,len = 448, size = 1184
[    5.032126] Bluetooth: Loading sysconfig file failed
[    5.032166] ath3k: probe of 3-5:1.0 failed with error -110
```
The same is with the speaker. Sometimes it works right after startup but sometimes it just refuse to work. I am so confused. Could anyone  tell me how to solve this problem? Thanks in advance.


P.S. Every time I start up, at the page where I enter my password to log in, it always pops up a window titled "Authentication required by Wi-Fi network" and asks me for wifi password. But even if I type in the password, the connect button is still grayed out. Does this has anything to do with the problems above?

---

