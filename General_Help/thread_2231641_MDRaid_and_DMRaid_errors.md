---
title: "MDRaid and DMRaid errors"
date: 2014-06-26
forum: General Help
---

### Post by RickKnight on 2014-06-26
Hello,

I have a MDRaid software RAID drive on my Kubuntu 14.04 system that has been working fine for a few months now. A few days ago I added an internal fan. I had to remove all my drives to install the fan and when I put the drives back in and rebooted, I discovered the bios had lost it's settings. I loaded the defaults and rebooted. I didn't realize it at the time, but with default settings my BIOS turns on a Marvall SATA controller for RAID. Now I'm getting some DMRaid errors, most notably when I run update-grub...

```
ERROR: ddf1: wrong # of devices in RAID set "ddf1_OS" [1/2] on /dev/sda
```

My RAID drives are /dev/sdc and /dev/sdd. My Windows 7, and boot drive, is /dev/sda (Kubuntu is on /dev/sdb). I am able to boot my system, all of my data is intact and my MDRaid drive, /dev/md0, seems fine. However, my Windows 7 installation does not show up in the GRUB menu and when I try to add it with update-grub I get the error above.

Can anyone confirm that having the Marvell SATA controller enabled caused this and, more importantly, can anyone tell me how to fix this? I thought about using 

```
$ sudo -rE /dev/sda
``` 

to remove the DMRaid metadata from /dev/sda but I don't want to destroy the windows installation, or boot sector.

Any ides anyone?

Thanks,
Rick

---

