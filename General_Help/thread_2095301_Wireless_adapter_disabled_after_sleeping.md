---
title: "Wireless adapter disabled after sleeping"
date: 2012-12-16
forum: General Help
---

### Post by sean00197 on 2012-12-16
Hello I am running ubuntu 12.10 everything is great except for my wireless adapter. When I start up it connects no problems. When I put my laptop to sleep and wake it the wireless adapter will not connect and it says wireless device is not ready. I looked else where and people said to reinstall and mess with the b43 drivers. I did this and it did not change anything. I currently have them uninstalled and I am connected. So any help on this would be great! Even some command that I can use to reset the adapter instead of restarting would be a big help! Thanks

---

### Post by rnerwein on 2012-12-16
> **sean00197 said:**
> Hello I am running ubuntu 12.10 everything is great except for my wireless adapter. When I start up it connects no problems. When I put my laptop to sleep and wake it the wireless adapter will not connect and it says wireless device is not ready. I looked else where and people said to reinstall and mess with the b43 drivers. I did this and it did not change anything. I currently have them uninstalled and I am connected. So any help on this would be great! Even some command that I can use to reset the adapter instead of restarting would be a big help! Thanks
hi
try   : sudo ifdown wlan0  (or how your wlan device is called)
then: sudo ifup wlan0
cheers

---

### Post by sean00197 on 2012-12-16
> **rnerwein said:**
> hi
try   : sudo ifdown wlan0  (or how your wlan device is called)
then: sudo ifup wlan0
cheers

This is what happens
```
sean@Sean-Linux:~$ sudo ifdown wlan0
[sudo] password for sean: 
ifdown: interface wlan0 not configured
sean@Sean-Linux:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0. 

```

and I double checked in the wifi connection information and it says Interface: 802.11 WiFi(wlan0)

---

### Post by rnerwein on 2012-12-18
> **sean00197 said:**
> This is what happens
```
sean@Sean-Linux:~$ sudo ifdown wlan0
[sudo] password for sean: 
ifdown: interface wlan0 not configured
sean@Sean-Linux:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0. 

```and I double checked in the wifi connection information and it says Interface: 802.11 WiFi(wlan0)
ups
try first: ifconfig      (is  your wifi shown there)
then : ifconfig wifi_interface (e.g. wlan0 if it is shown)
see man: ifconfig
good luck

---

### Post by sgage on 2012-12-18
Do you have nvidia graphics? If so, are you using the proprietary drivers or nouveau?

The reason I ask is because I have a similar-sounding problem, but with a "wired" ethernet connection. With the nouveau drivers, it will not work after resuming from sleep. With the proprietary drivers it works fine.

---

### Post by grahammechanical on 2012-12-18
This might help your understand what is happening.

[http://en.wikipedia.org/wiki/Sleep_mode]("http://en.wikipedia.org/wiki/Sleep_mode")

> Machine state is held in RAM memory and, when placed in sleep mode, the computer cuts power to unneeded subsystems and places the RAM into a minimum power state, just sufficient to retain its data.

If the wireless adapter was left on then it would use up battery power. So, when the machine enters sleep mode the wireless adapter is switched off just as it is switched off when the machine if switched off or powered off.

Run this command:

```
 rfkill list
```

run it after resuming from sleep mode.

Softblocked: yes - means the wireless adapter is switched off by software.
Hardblocked: yes - means the wireless adapter is switched by a hardware (keyboard) switch.

Have you tried clicking on the Network Icon and disabling and then enabling either Networking or Wi-Fi?

You can also do this through System Settings>Network. You will find an On/Off slider for the wireless adapter.

You could also use the command:

```
rfkill unblock wifi
```


Regards.

---

### Post by rscricket on 2013-01-09
[http://askubuntu.com/questions/67280/wireless-doesnt-connect-after-suspend-on-an-asus-k52f](http://askubuntu.com/questions/67280/wireless-doesnt-connect-after-suspend-on-an-asus-k52f)

Pls follow link above. It tells you to do 3 things:
1. find driver for wlan0
2. unload it
3.reload it

this worked for me.

---

