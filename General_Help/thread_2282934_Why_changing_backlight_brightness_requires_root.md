---
title: "Why changing backlight brightness requires root?"
date: 2015-06-17
forum: General Help
---

### Post by kagashe on 2015-06-17
On my Lenovo G50-45 Laptop the back-light brightness is adjusted either through Fn keys 11 (down) and 12 (up) or through System_settings/Brightness_&_Lock/Brightness.

While trying to make it work on Ubuntu LXDE Desktop I discovered that the brightness is altered through USER=root through auth.log while you do it by any of the two methods.
```
Jun 18 07:56:37 LenovoG50-45 pkexec[2215]: user: Executing command [**USER=root**] [TTY=unknown] [CWD=/home/user] [COMMAND=/usr/lib/unity-settings-daemon/usd-backlight-helper --set-brightness 27]
```

This machine is new and I have installed Ubuntu 14.04 & 15.04 in multi boot and it is same for both but I have seen a discussion on this forum that someone who upgraded from Ubuntu 12.04 to 14.04 discovered that the back-light brightness settings required root after the upgrade. So this feature seems to be implemented from Ubuntu 14.04 onwards.

My question is Why changing backlight brightness requires root?
is it some kind of security feature.

Kamalakar

---

### Post by wildmanne39 on 2015-06-17
I did not find anything suggesting it is a security feature, which I did not believe was the case.
If you use sudo with a GUI instead of gksudo then root can become the owner of those files a cause issues but other then that I do not know.

---

### Post by CharlesA on 2015-06-17
The desktop manager/display manager runs as root even if you are logged into the GUI as a normal user.

A normal user cannot modify system files, but root can.

---

