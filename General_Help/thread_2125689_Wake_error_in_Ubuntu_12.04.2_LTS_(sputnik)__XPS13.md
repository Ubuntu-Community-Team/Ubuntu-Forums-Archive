---
title: "Wake error in Ubuntu 12.04.2 LTS (sputnik) / XPS13"
date: 2013-03-14
forum: General Help
---

### Post by vuarnet on 2013-03-14
Good afternoon --

I have been having a strange error recently... and I have found the error *message* but I can't (for the life of me) figure out what it means or is affecting. As far as I can tell, nothing is broken, although occasionally the WiFi doesn't resume and I have to either reboot or disable / enable wireless networking in order to get it to connect to a remembered network.

Details:

Hardware: Dell XPS 13 Sputnik
ISO: Custom Sputnik ISO (12.04.2 LTS 64-bit with some preconfigured tweaks)
PPAs added for hardware support
Intel i7 dual-core
Intel Centrino Advanced N 6235

Everything appears to work almost flawlessly with this one exception.

Every time I wake the computer up... I get this error:

legacy_resume(): pnp_bus_resume+0x0/0x70 returns -19
PM: Device 00:07 failed to resume: error -19

Basically, this log accrues each time I shut my laptop and re-open it. So, after a full day's use I have several of this same message... over and over.

If it's not affecting any negatively, I'd almost be content just disabled the output of the message.

Does anyone have any ideas what this might mean? How to fix it? Or at least how to disable the message output?

Thanks in advance!

~ vuarnet

---

