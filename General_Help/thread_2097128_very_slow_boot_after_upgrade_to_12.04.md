---
title: "very slow boot after upgrade to 12.04"
date: 2012-12-22
forum: General Help
---

### Post by DrScum on 2012-12-22
Since 10.04 LTS support ends in March I upgraded to 12.04 LTS two days ago. I am still dealing with the aftermath. The boot time is extremely slow (30+ seconds after grub kicks in) compared to what I had before (10+ seconds). From the
Dmesg output:

...
[    7.250552] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)

…........27 seconds delay  ...............................


[   34.143144] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.173418] udevd[491]: starting version 175
[   34.233869] lp: driver loaded but no devices found
[   34.237833] Adding 4642780k swap on /dev/sda4.  Priority:-1 extents:1 across:4642780k 
[   34.436431] nvidia: module license 'NVIDIA' taints kernel.
[   34.436434] Disabling lock debugging due to kernel taint
[   34.466474] type=1400 audit(1356173114.599:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=551 comm="apparmor_parser"
...
I conclude that the network adapters are the problem. 
The wireless adapter does not get started (broadcom 4311, device b43) I have to start it manually with modprobe b43 after the system is up. If the wired connection is connected it works fine. 

Is there anyone out there who can help me? I have a parallel post in Networking regarding the b43 module.

---

### Post by rnerwein on 2012-12-22
> **DrScum said:**
> Since 10.04 LTS support ends in March I upgraded to 12.04 LTS two days ago. I am still dealing with the aftermath. The boot time is extremely slow (30+ seconds after grub kicks in) compared to what I had before (10+ seconds). From the
Dmesg output:

...
[    7.250552] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)

…........27 seconds delay  ...............................


[   34.143144] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   34.173418] udevd[491]: starting version 175
[   34.233869] lp: driver loaded but no devices found
[   34.237833] Adding 4642780k swap on /dev/sda4.  Priority:-1 extents:1 across:4642780k 
[   34.436431] nvidia: module license 'NVIDIA' taints kernel.
[   34.436434] Disabling lock debugging due to kernel taint
[   34.466474] type=1400 audit(1356173114.599:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=551 comm="apparmor_parser"
...
I conclude that the network adapters are the problem. 
The wireless adapter does not get started (broadcom 4311, device b43) I have to start it manually with modprobe b43 after the system is up. If the wired connection is connected it works fine. 

Is there anyone out there who can help me? I have a parallel post in Networking regarding the b43 module.
hi
i guess too it's your network (timeout). place your modul b43 in /etc/modules then it will be loaded by the kernel. just infix a line:
b43

but by the way - what's 30 seconds  ?
cheers

---

### Post by DrScum on 2012-12-22
Thanks for the tip rnerwein. Regarding "what's 30s?" I know you're right but I worked hard to minimize boot times on 10.04 and you experience double boot time it feels like booting Windows or something. 

The adapter gets started at boot time now. Thats the good news. However, overall boot time didn't improve, I'll have to dig further. Thanks for your help though.

---

