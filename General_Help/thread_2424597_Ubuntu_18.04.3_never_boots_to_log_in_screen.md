---
title: "Ubuntu 18.04.3 never boots to log in screen"
date: 2019-08-11
forum: General Help
---

### Post by rapidrob on 2019-08-11
This just started this week. When the computer is turned on, I get the initial Purple logo screen and as it loads this screen for a few seconds and then goes black for about 30 seconds. 
Normally after this delay, the 2ND purple screen appears,I hit enter and the login window is active for the password.
Now it boots to the logo screen and goes dark never to load the login screen. I have to reboot the computer in order to have it boot in a normal way.
Any ideas as to how to fix this problem?
I AM running " Ubuntu with communitheme snap on Wayland"

Intel Core 2 Quad CPU Q9650@3.00 GHz x 4
8 GB Memory
NV92 Graphics
GNOME 3.28.2
64 bit
500 GB HD

---

### Post by Autodave on 2019-08-11
I thought that there was a problem with Wayland and Nvidia.  I am sure someone will either confirm that or tell me that I am wrong.

Anyway, what Nvidia driver are you using and where did you get it from?

---

### Post by rapidrob on 2019-08-11
When I loaded Ubuntu 18.04.3 six months ago all the drivers were found and loaded by the install. It has worked up until last weeks "updates" were downloaded.
I'm not sure how ro verify what vesion of driver for Nvidia I have.

---

### Post by Bashing-om on 2019-08-11
rapidrob; Hello

> 
I'm not sure how ro verify what vesion of driver for Nvidia I have.


Post back - Between code Tags - ( maintains formatting for readability) the outputs of terminal commands:
```

sudo lshw -C display
dpkg -l | grep -i nvidia
lsmod | grep nvidia

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

see here what is not going on here.

[INDENT]we can do that
[/INDENT]

---

