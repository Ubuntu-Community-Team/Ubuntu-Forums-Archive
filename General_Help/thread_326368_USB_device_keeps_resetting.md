---
title: "USB device keeps resetting"
date: 2006-12-27
forum: General Help
---

### Post by Zaggy on 2006-12-27
Hi, I'm trying to listen to music from my usb external hdd, and every music app I try -rhythmbox, amarok, mpd and xmms- keep freezing on me.

A look in /var/log/syslog gives me this a lot:

Dec 27 19:54:50 localhost kernel: [17208290.300000] usb 5-1: reset high speed USB device using ehci_hcd and address 2

Is my hardware bad or is the usb driver bad?

---

### Post by Zaggy on 2007-01-03
/bump

---

### Post by Zaggy on 2007-01-04
Someone on #ubuntu on Freenode gave me the tip to try a different usb port.
It helped :D
Thanks beck!
Jan 03 12:26:24 <beck>	Have you tried unplugging it and plugging it back in

---

