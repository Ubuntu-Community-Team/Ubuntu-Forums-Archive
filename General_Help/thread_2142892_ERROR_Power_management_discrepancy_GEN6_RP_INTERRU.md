---
title: "*ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 15000000, wa"
date: 2013-05-07
forum: General Help
---

### Post by ajinthomas on 2013-05-07
My Ubuntu 12.04 seems to take a long time to load and I started Investigating it. Initially this([http://askubuntu.com/a/201870/130724](http://askubuntu.com/a/201870/130724)) answer helped me a lot.
After further research I found the following error in dmesg output.
```

[   26.392776] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 15000000, was 12060000

```

Some times more than one similar errors occur and it takes much more time to boot. See below.

```

$ dmesg|tail
[   21.588994] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   21.589238] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   22.966305] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 15000000, was 12060000
[   23.230445] r8169 0000:04:00.0: eth1: link up
[   23.230557] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[   24.232978] init: plymouth-stop pre-start process (1302) terminated with status 1
[   33.611352] eth1: no IPv6 routers present
[  261.448219] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 00070000, was 15000000
[  269.400954] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 15070000, was 00000000
[  271.542886] [drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 15070000, was 15000000
$

```

Any information on how to solve this problem will be helpful.

---

### Post by holmesc on 2013-05-08
Just registered to add that I am experiencing the same issue, except that my error differs slightly in the 'expected' value:

```
 GEN6_RP_INTERRUPT_LIMITS expected **16000000,** was 12060000 
``` (emphasis mine)

This error began occuring concurrent to my repartitioning of my hard drive to install another copy of Ubuntu.  I'm not sure if this is related; have you done anything similar to change your system lately, ajinthomas?

---

### Post by ajinthomas on 2013-05-09
It is possible; even though I didn't do anything recently, It is possible that the error was there for a long time and I started to notice it only recently. 
Look at this, I think I have one of the weirdest partition layout for an Ubuntu installation.
[IMG]http://ubuntuone.com/0ma0I1H2U40z8P9Vp8aoTZ[/IMG]
Also I did re-sized most of the partitions after installation.

---

### Post by tarverator on 2013-05-22
I am getting the same thing:
[drm:gen6_sanitize_pm] *ERROR* Power management discrepancy: GEN6_RP_INTERRUPT_LIMITS expected 18000000, was 12060000
...in the kenrel log, and appears on screen when resuming from suspend. No recent re-partitioning of the disk.  I am on Linux Mint Mate Maya.

---

### Post by Rexilion on 2013-05-22
My guess is you all have an Intel video card. Another hint are the words 'drm' which indicate the kernel video management subsystem. So, I think it's your videocard protesting against whatever the kernel is throwing at him.

Someone else saw these messages [too]("https://bugs.freedesktop.org/show_bug.cgi?id=50073").

You could try to run a more recent kernel.

---

### Post by Code Warrior on 2013-06-17
I'm facing the same *Power management discrepancy* error since last 3 weeks. 

Here are the OS/Kernel details...

Linux 3.2.0-41-generic-pae #66-Ubuntu SMP Thu Apr 25 03:50:20 UTC 2013 i686 i686 i386 GNU/Linux

Updating the kernel will solve this issue or not?

---

### Post by tarverator on 2013-06-17
I still see the error with this, the most recent kernel:

$ uname -a
Linux thinx 3.2.0-48-generic #74-Ubuntu SMP Thu Jun 6 19:45:16 UTC 2013 i686 i686 i386 GNU/Linux

---

### Post by boregard on 2013-06-17
installing kernal 3.3.6 fixed it for me. find info from [https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/1168467](https://bugs.launchpad.net/ubuntu/+source/gnome-nettool/+bug/1168467)   post # 7.

---

