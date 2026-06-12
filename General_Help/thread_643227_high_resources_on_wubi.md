---
title: "high resources on wubi"
date: 2007-12-17
forum: General Help
---

### Post by tytons on 2007-12-17
im not sure if this is a firefox prob or wubi, but im definately sure that when running multiple tabs on firefox takes up alot of resources on wubi. it goes up to 80-90% 

after patching the kernels and installing the flash player manually from adobe site..firefox doesnt take that much resources..but still bad enough, does installing through a virtual machine cause this?is wubi considered a virtual machine?

and how do you check how much space is left for wubi?the last time i had too many applicated downloaded and couldnt log back in.

---

### Post by ago on 2007-12-17
wubi should not affect performance unless you have an extremely fragmented disks or are using swap a lot

---

### Post by tytons on 2007-12-19
> top - 04:41:21 up 31 min,  1 user,  load average: 1.30, 1.39, 1.09
Tasks: 129 total,   5 running, 123 sleeping,   0 stopped,   1 zombie
Cpu(s): 24.7%us,  0.7%sy,  0.0%ni, 72.9%id,  1.7%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    514508k total,   508356k used,     6152k free,    33164k buffers
Swap:   488272k total,    33896k used,   454376k free,   142652k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 7766 benjamin  15   0  147m  28m  16m S 17.6  5.7   1:01.72 totem-plugin-vi
 6199 benjamin  15   0  337m 110m  27m R  4.0 22.1   3:41.96 firefox-bin
 5486 root      15   0 72648  45m  19m S  1.7  9.0   1:59.75 Xorg
 6002 benjamin  15   0 17228  10m 7652 S  1.0  2.0   0:07.98 metacity
 6820 root      15   0 71136  30m  19m S  0.7  6.1   0:13.30 synaptic
 2942 root      15   0  2488 1124  604 S  0.3  0.2   1:05.82 ntfs-3g
 6173 benjamin  15   0 54416  12m 9156 S  0.3  2.5   0:00.22 mixer_applet2
 6684 benjamin  15   0  2316 1176  880 R  0.3  0.2   0:02.41 top
    1 root      25   0  2908 1844  524 S  0.0  0.4   0:00.20 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
   30 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kblockd/0
   31 root      18  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid

does this look normal?i tried running ubuntu from the live cd, had firefox on as well and it was alot more stable in terms of processes. most of the time it would be a single digit %

i also did a lsb_release -a
n somehow it says that my ubuntu is..

> Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

why/how is this so?i swear i downloaded the latest wubi which is Wubi-7.04.04.exe, shouldnt it be 7.10?

---

### Post by ago on 2007-12-20
It's on the high side, try to disable the totem-plugin and see if things improve. Also try firefox-3 (beta2 is out), it's lighter and behaves better with resources.

---

### Post by kwiggit on 2007-12-20
> **ago said:**
> wubi should not affect performance unless you have an extremely fragmented disks or are using swap a lot

Vista **alone** sucks up resources out the proverbial wazoo-( I have disabled many features (after doubling my memory) the problem was still there, so upon further perusing this matter I noted what was sucking the life
out of my resources and have disabled them accordingly.

Now mind you, I'd be using the latest version of my favorite of Linux distro- but up until last week I had a good running version; then suddenly the deb busybox came up and all sorts of other sh** hit the fan.

Unless you know what you are disabling, I don't suggest arbitrarily disabling all vista resources (heh heh- so **maybe I would**...)


I am seriously bumming I can not get Ubuntu/kubuntu up running again...
Just when I had it where I wanted....poof gone again

---

