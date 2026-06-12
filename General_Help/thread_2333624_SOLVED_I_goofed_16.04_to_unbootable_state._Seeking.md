---
title: "SOLVED: I goofed 16.04 to unbootable state. Seeking aid"
date: 2016-08-11
forum: General Help
---

### Post by jarif on 2016-08-11
I have a dual boot system for Windows 10 and Ubuntu 16.04

Last update of Ubuntu broke something and Ubuntu is not more bootable.

"systemctl reboot" told me that this is destructive but I rebooted anyway,
they way as I'm built sometimes

Message:
[https://www.dropbox.com/s/3as0rmdduvu5d39/2016-08-05%2004.44.34.jpg?dl=0](https://www.dropbox.com/s/3as0rmdduvu5d39/2016-08-05%2004.44.34.jpg?dl=0)

Grub works, at least for Windows, as that can be used fine, and the Grub
is the boot manager.

Ubuntu boots, but ends up in Emergency shell. After entering password
and seeing "journalctl -xb I can's see errors. It complaints about some
local disk that is not available (must be an external drive). I now
plugged it out to see if that changes something.

Status:
[https://www.dropbox.com/s/ou8txabztsfl3ns/2016-08-09%2013.07.23.jpg?dl=0](https://www.dropbox.com/s/ou8txabztsfl3ns/2016-08-09%2013.07.23.jpg?dl=0)

It I run systemctl default it always ends up the latter. And no errors
in journalctl -xb

Is there some common recovery procedure for these, so that I would not
need to reinstall the beast?

Ubuntu: Ubuntu Gnome 16.04.1 LTS

---

### Post by QIII on 2016-08-11
Hello!

Please use the default font and color unless you need to highlight a specific portion of you text.

Thanks!

---

### Post by jarif on 2016-08-11
Uh. I did not use any specific font, and I did not mean to highlight anything. On my screen now the font in my post and yours are just the same.

EDIT: Ah, you had edited them. But anyway, I did not pick any fonts...

---

### Post by jarif on 2016-08-18
SOLVED

I have a hate against dnsmasq and NetworkManager and had tested something with /etc/network/interfaces. I later removed my modification but there was still my eth0 in "auto lo eth0" That "eth0" made the system startup invalid.

It's an another issue to ask that why in earth the dnsmasq does fail often resolving my LAN bind9's (3 hosts) DNS responses. All other machines in LAN work fine, but Ubuntu 16.04 does not.

But this is resolved.

---

