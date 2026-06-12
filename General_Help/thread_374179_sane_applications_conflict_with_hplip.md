---
title: "sane applications conflict with hplip"
date: 2007-03-02
forum: General Help
---

### Post by vob on 2007-03-02
Hi,

I have some troubles when accessing scanner devices under Kubuntu Dapper on a dell d620. (My scanner is a Canon LIdE 25 which is well supported by sane, but the problem appears to be related to a conflict between sane and hplip rather than a scanner problem, see below). 
This issue first showed up when I tried to start GIMP after installing sane and xsane via adept. GIMP hung during the initialization of the xsane plugin, and there was a line in the syslog saying
```
unable to open /var/run/hplip/hpiod.port: No such file or directory: prnt/hpijs/hplip_api.c 84
```Following a google advice I uninstalled xsane and GIMP started fine afterwards.

However when I attach the scanner and try to run kooka there does not happen much except except the same line in the syslog and a bouncing icon at the mouse pointer, which disappears after several seconds. However, about 3 minutes later, kooka starts up, detecting the scanner and working flawlessly (as far as I can tell so far). A similar delay is observed when using xscanimage from the sane package. In both cases the syslog tells me:
```

Feb 28 22:57:12 host xscanimage: unable to open /var/run/hplip/hpiod.port: No such file or directory: prnt/hpijs/hplip_api.c 84
Feb 28 23:00:21 host xscanimage: unable to connect hpiod socket 50000: Connection timed out: prnt/hpijs/hplip_api.c 703
Feb 28 23:00:21 host xscanimage: ProbeDevices(): unable to send message: Bad file descriptor

```Does anyone out there have an idea what causes the problem and what might be done to cirumvent it. It's quite annoying to wait 3 minutes before the scanner is ready or to be able to use the GIMP even when there is no scanner attached. I've read several posts on the web saying they work with that scanner and kooka out of the box with no problems. As far as I can tell the involved packages (libsane, sane, kooka) are taken from the official servers, nothing self-compiled. 

Any help or suggestion is appreciated.

---

### Post by vob on 2007-03-08
Posting this problem on the san-devel mailing list ([www.sane-project.org](www.sane-project.org)) offered the solution: simply comment all entries except those for the required backend(s) (here: plustek) in /etc/sane.d/dll.conf AND in all files in the /etc/sane.d/dll.d/ directory. Now xscanimage, kooka etc. do only probe the hardware for scanners using the uncommented backend(s), and do not end up querying nonexistent hardware. In fact, hplip and hpaio are only necessary for HP all-in-one printer/scanners.

---

