---
title: "Error while using airmon-ng and airodump-ng"
date: 2013-06-01
forum: General Help
---

### Post by Foerunner on 2013-06-01
Hi,

I installed aircrack and reaver today with the help of a blog.Then I tried to use aircrack so I typed 
**airmon-ng start wlan0** but it showed an error:
[B]Found 5 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!
-e 
PID   Name
522   avahi-daemon
523   avahi-daemon
739   NetworkManager
773   wpa_supplicant
1224   dhclient
Process with PID 1224 (dhclient) is running on interface wlan0


Interface   Chipset      Driver

wlan0      Unknown    wl - [phy0]mon0: ERROR while getting interface flags: No such device

            (monitor mode enabled on mon0)[/B]

I saw that monitor mode is enabled on mon0 so I thought this error would be a minor problem so I proceeded typing: [B]airodump-ng mon0
[/B] but again an error 
I[B]nterface mon0: 
ioctl(SIOCGIFINDEX) failed: No such device.[/B] 
I tried googling but no answer. My wireless driver is manufactured by Broadcom. The driver is BCM5906M. If more information is needed, then please ask :)
Foerunner a.k.a. Vedant.

SCREENSHOTS:

***IWCONFIG:***

[IMG]http://www.upload.ee/image/3352468/IWCONFIG.png[/IMG]

[B][I]ERROR:

[/I][/B][URL="http://www.upload.ee/image/3352469/Error.png"][IMG]http://www.upload.ee/image/3352469/Error.png</a>[/IMG]

[B][I]LSPCI:

[/I][/B][IMG]http://www.upload.ee/image/3352471/LSPCI.png[/IMG]

**Link to the image:**

***ERROR:***

[/URL][http://www.upload.ee/image/3352469/Error.png](http://www.upload.ee/image/3352469/Error.png)

***LSPCI:***

[http://www.upload.ee/image/3352471/LSPCI.png](http://www.upload.ee/image/3352471/LSPCI.png)

***IWCONFIG:***

[http://www.upload.ee/image/3352468/IWCONFIG.png](http://www.upload.ee/image/3352468/IWCONFIG.png)

---

### Post by lisati on 2013-06-01
We don't support aircrack here, even though it's in the repos. The aircrack folks have a nice shiny new forum where you might be able to get help.

---

