---
title: "Seemingly Random Reboots -- Advice?"
date: 2016-02-07
forum: General Help
---

### Post by jpgerick on 2016-02-07
Hey all,

Been a loyal Ubuntu-er for years on my HP dv6t Quad Edition (dual booting with Win10).  Currently running 14.04, fully updated.

Ever since 13.10 (maybe even with 13.04), I've experienced random hard system reboots, usually while watching videos (either online or locally) but not always.  Never once been a problem in Windows.

Things I've tried:
1. intel_pstate=enable
2. i915 rc6 disabling
3. Turning off virtualization technology in BIOS just in case
4. Switching dedicated graphics drivers, tried both Nvidia proprietary and nouveau
5. Checking CPU temps, they're usually in mid-to-high 60s when it happens (and my CPU is Ivy Bridge, so it was supposed to run at higher temps anyhow)
6. Installing, and subsequently removing, Bumblebee

[Here's my syslog from last night.]("https://dl.dropboxusercontent.com/u/37097724/syslog")  You can crtl-F for "http://www.rsyslog.com"] start and see that 5/7 times there was an unprompted reboot and no particular pattern in what the system was doing before the restart.

Thoughts?

---

### Post by sohlinux on 2016-02-07
check the logs in /var/log look for the time and date it rebooted, it may shed some light

---

