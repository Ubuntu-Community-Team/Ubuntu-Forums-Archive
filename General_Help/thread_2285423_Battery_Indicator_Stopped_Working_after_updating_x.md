---
title: "Battery Indicator Stopped Working after updating xubuntu 14.04"
date: 2015-07-05
forum: General Help
---

### Post by Ralph L on 2015-07-05
I am running xubuntu 14.04 on a Dell Latitude D610 with 2G memory.  I just installed the latest updates and now my battery indicator (part of Indicator Plugin on my screen panel) stopped working.  If I left click it, it pops up with a battery symbol and the words "Battery (charged)".  However, I can no longer select the detailed window that show the charge on each battery and other details.  Anybody know how I can get that window back, or at least how I can launch it some other way.  I don't even know the name of the app that displays the battery details window.

Any help appreciated.......

---

### Post by Ralph L on 2015-09-02
I could sure use some help on this.  I can no longer click on one of the batteries listed in the battery indicator, and get details on the battery.  For example, I can no longer find the percentage of design charge the battery is actually accepting..  Before the update this was standard information, when clicking on one of the batteries listed in the battery indicator.  Is anybody else having this problem with xubuntu 14.04????  As I said before this is a real problem for me........

---

### Post by Ralph L on 2015-09-08
I may have been confused about whether xubuntu or ubuntu gave me detailed battery status.  Anyway I solved the problem by adding this script to my xubuntu whiskers menu.  ```
#! /bin/bash
upower -i /org/freedesktop/UPower/devices/battery_BAT0 >/tmp/a
upower -i /org/freedesktop/UPower/devices/battery_BAT1 >>/tmp/a
zenity --title="Battery 0 and Battery 1 Status" --text-info --filename="/tmp/a"
```
I know little about scripts so if somebody would tell my how to write this script without using the /tmp/a file, I would appreciate it.

---

