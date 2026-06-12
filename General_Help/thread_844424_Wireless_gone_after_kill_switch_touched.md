---
title: "Wireless gone after kill switch touched"
date: 2008-06-29
forum: General Help
---

### Post by stash1071 on 2008-06-29
Dell XPS M1330 with Ubuntu 7.10 preinstalled

Wireless was working great, but the other day I bumped the switch to turn wi-fi off, and wireless went away after my next reboot.  I put the switch back to the on position but wireless is still gone after a reboot.

The drivers appear to load fine, but a connection cannot be found. How can I get Ubuntu to act like a never touched the switch?  Thanks in advance

```

$ lsmod | grep ipw
ipw3945               119840  0 
ieee80211              35656  1 ipw3945

$ sudo /sbin/ipw3945d-2.6.22-15-generic 
ipw3945d - regulatory daemon
Copyright (C) 2005-2006 Intel Corporation. All rights reserved.
version: 1.7.22
2008-06-29 13:25:29: ERROR: Could not find Intel PRO/Wireless 3945ABG Network Connection

```

---

### Post by stash1071 on 2008-06-29
I was able to get a wireless connection back in the network manager, but am unable to detect any networks, so some progress at least.

I followed the instructions here (even though my problem was not LED related):
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/176090](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/176090)

I upgraded to Ubuntu 8.04 then:

```

$ sudo apt-get install linux-backports-modules-hardy
$ sudo rmmod iwl3945
$ sudo modprobe iwl3945
$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 
prystasj@dell-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

eth1      IEEE 802.11a  ESSID:""  Nickname:""
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

