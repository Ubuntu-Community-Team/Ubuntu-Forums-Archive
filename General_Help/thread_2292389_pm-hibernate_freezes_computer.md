---
title: "pm-hibernate freezes computer"
date: 2015-08-27
forum: General Help
---

### Post by el_baby on 2015-08-27
Hi, I have a brand new ZaReason Zini 1550 with 2 SSD drives.

I installed stock Ubuntu 14.04.3 (it came with 15.04 regardelss I had asked for 14.04)

It has 16Gb of RAM and I have one 16Gb swap partition in each drive (each swap partition is slightly larger than the RAM).

Before enabling hibernation I manually run "sudo pm-hibernate" from an xterm and the computer froze completely. It turned off and on the video briefly and then, with the video on, it froze. Only way out was keeping the power button pressed. I saw nothing unusual in /var/log/pm-suspend.log or in /var/log/syslog.

Last lines from pm-suspend.log are:
```
Running hook /usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate:
/usr/lib/pm-utils/sleep.d/00powersave hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_grub-common hibernate hibernate:
/etc/pm/sleep.d/10_grub-common hibernate hibernate: success.

Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate:
/etc/pm/sleep.d/10_unattended-upgrades-hibernate hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate:
/usr/lib/pm-utils/sleep.d/50unload_alx hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate:
Selected interface 'wlan0'
OK
/usr/lib/pm-utils/sleep.d/60_wpa_supplicant hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/75modules hibernate hibernate:
/usr/lib/pm-utils/sleep.d/75modules hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/90clock hibernate hibernate:
/usr/lib/pm-utils/sleep.d/90clock hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate:
/usr/lib/pm-utils/sleep.d/94cpufreq hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate:
stop: Unknown instance: 
/usr/lib/pm-utils/sleep.d/95anacron hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95hdparm-apm hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/95led hibernate hibernate:
/usr/lib/pm-utils/sleep.d/95led hibernate hibernate: not applicable.

Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate:
Kernel modesetting video driver detected, not using quirks.
/usr/lib/pm-utils/sleep.d/98video-quirk-db-handler hibernate hibernate: success.

Running hook /usr/lib/pm-utils/sleep.d/99video hibernate hibernate:
/usr/lib/pm-utils/sleep.d/99video hibernate hibernate: success.

Running hook /etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate:
/etc/pm/sleep.d/novatel_3g_suspend hibernate hibernate: success.

Thu Aug 27 12:12:08 ART 2015: performing hibernate

```

Any hints?

---

### Post by el_baby on 2015-09-02
**¿bump?**

---

