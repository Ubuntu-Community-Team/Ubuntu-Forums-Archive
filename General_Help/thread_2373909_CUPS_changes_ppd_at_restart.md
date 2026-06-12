---
title: "CUPS changes ppd at restart"
date: 2017-10-10
forum: General Help
---

### Post by jorgalfonso on 2017-10-10
Hello everybody.

I'm having a little issue with a Samsung multifunction printer (M2070). The printer works great with the "M2070 series (en)" ppd (available after the Samsung's setup), but each time CUPS is restarted (including computer power on cycles and reboots of course) CUPS uses the default setup driver, the "M2070 series, driverless, cups-filters 1.13.4 (en)", which is not so bad as long the only thing you want to do is print test pages, because otherwise just print garbage chars.

There is a way to prevent CUPS to change the driver each time? My setup is Kubuntu 17.04 and CUPS 2.2.2

Thank you.

---

### Post by LeXav on 2017-10-28
Hi !

I've a similar problem. My canon MG4200 has a bugged ppd file. I managed to edit it and correct it, but it's a restart of CUPS to be set-in and then CUPS erase my correction. I'm still stuck on it. :/

---

### Post by mlan on 2017-10-28
A workaround is to configure the printer with the cups web interface. Open localhost:631 in a browser and add the printer there. The settings seems to be persistent if the printer is added this way instead of in Ubuntu's settings. I have a Samsung printer and it always defaults to the "driverless" option when cups is restarted if I add the printer via Gnome settings.

---

### Post by LeXav on 2017-10-29
Hi mlan,

this save me : [https://ubuntuforums.org/showthread.php?t=2375875&p=13704451#post13704451](https://ubuntuforums.org/showthread.php?t=2375875&p=13704451#post13704451)

Thanks ! :)

---

