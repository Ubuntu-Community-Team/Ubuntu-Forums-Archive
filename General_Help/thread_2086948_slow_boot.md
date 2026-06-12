---
title: "slow boot"
date: 2012-11-22
forum: General Help
---

### Post by watgrad on 2012-11-22
Hello,
My ubuntu 12.10 installation is very slow to boot up (dual boot macbook pro8,1). 

There is a long delay in the process.  I was hoping for advice to resolve any potential issues with my installation.  In the middle of the boot the main ubuntu (sda3) partition has to be switched to read/write access and then the swap file is created:

[    4.742054] firewire_core 0000:04:00.0: phy config: new root=ffc0, gap_count=63
[    9.903246] EXT4-fs (sda3): INFO: recovery required on readonly filesystem
[    9.903259] EXT4-fs (sda3): write access will be enabled during recovery
[   11.063178] EXT4-fs (sda3): recovery complete
[   11.071197] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   37.694879] Adding 4748040k swap on /dev/sda6.  Priority:-1 extents:1 across:4748040k 

A total delay of 33 sec.  Are these actions normal for the boot up.  Can ubuntu just use the same swap file or does it really need to create this every time it boots up?

I would appreciate any suggestions for speeding up this startup process...

---

### Post by idoitprone on 2012-11-22
> **watgrad said:**
> Hello,
My ubuntu 12.10 installation is very slow to boot up (dual boot macbook pro8,1). 

There is a long delay in the process.  I was hoping for advice to resolve any potential issues with my installation.  In the middle of the boot the main ubuntu (sda3) partition has to be switched to read/write access and then the swap file is created:

[    4.742054] firewire_core 0000:04:00.0: phy config: new root=ffc0, gap_count=63
[    9.903246] EXT4-fs (sda3): INFO: recovery required on readonly filesystem
[    9.903259] EXT4-fs (sda3): write access will be enabled during recovery
[   11.063178] EXT4-fs (sda3): recovery complete
[   11.071197] EXT4-fs (sda3): mounted filesystem with ordered data mode. Opts: (null)
[   37.694879] Adding 4748040k swap on /dev/sda6.  Priority:-1 extents:1 across:4748040k 

A total delay of 33 sec.  Are these actions normal for the boot up.  Can ubuntu just use the same swap file or does it really need to create this every time it boots up?

I would appreciate any suggestions for speeding up this startup process...

that is very odd

on my machine
> [    0.766748] Pid: 1, comm: swapper/0 Not tainted 3.6.3-2.6.3-custom #1
[    5.616126] Adding 5858300k swap on /dev/sda5.  Priority:-1 extents:1 across:5858300k 
it takes less than 5 seconds

---

### Post by watgrad on 2012-11-26
Any ideas out there?

---

### Post by watgrad on 2012-12-15
Bump - Anyone have an idea???

---

### Post by skaboss on 2013-01-07
Same issue here :
```
[    3.389325] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   26.111289] Adding 2559996k swap on /dev/sda8.  Priority:-1 extents:1 across:2559996k 
```
Did you find a solution ?

---

### Post by watgrad on 2013-01-16
This seems to be a bug with 12.10 (and possible 13.04).
[https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1061639](https://bugs.launchpad.net/ubuntu/+source/ifupdown/+bug/1061639)


Reverting from 12.10 to 12:04 solved the problem with file corruption on all my machines.

---

