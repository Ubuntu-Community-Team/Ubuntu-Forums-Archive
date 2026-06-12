---
title: "how to install tar.xz file in ubuntu"
date: 2022-10-22
forum: General Help
---

### Post by ianadds2 on 2022-10-22
Hi All,
       I have an issue with ubuntu freezing which i am slowly sorting out but i have an issue and need some advice? I found an app called Hardware Probe which analyised my drive and found three issues
    8086:2725:8086:0024 »
/ 02-80    Intel Corporation    Wi-Fi 6 AX210/AX211/AX411 160MHz    network    iwlwifi    works 
PCI    144d:a80a:144d:a801 »
/ 01-08-02    Samsung Electronics Co Ltd    NVMe SSD Controller PM9A1/PM9A3/980PRO    storage    nvme    detected 
PCI    8086:9a0b:8086:0000 »
/ 01-04    Intel Corporation    Volume Management Device NVMe RAID Controller    storage    vmd    detected 

The errors can be corrected by a latest drive Linux-6.3.0.tar.xz file which i have downloaded, however the instructions i have used don't install the driver  sudo apt install-utils  after doing an update. Any advice or help in installing this file would be great i am using a omen 17 laptop, intel i7, iT, 16 gigs of ram, 6 gigs memory

Cheers ian

PS i think the storage one is the main issue

---

### Post by TheFu on 2022-10-22
Those look like log entries, not errors.  During boot, Linux searches for hardware it recognizes and that gets logged.

I've never heard of "Hardware Probe". When  I wan to know what hardware is inside a system, I use either
lshw
or
inxi -Fxxx

lshw will show much more detail about the hardware, version of the hardware, capabilities, and the current driver loaded.  
inxi is shorter, but provides a nice overview. It is possible to get more information from inxi too, but it isn't as complete. Still, it is a good place to start to see what hardware is recognized by the kernel.

An 980 PRO shouldn't have any issues, assuming normal stuff.
I wouldn't expect issues with the wifi adapter either. Intel network stuff sorta just works, almost always.
The Intel RAID controller could be an issue, but the fact that is is recognized is a good sign.  Probably best not to use a RAID control since the software-RAID that all Linux systems support is more flexible, convenient and typically faster than all but the $400+ HW-RAID controllers.

Are you seeing any specific issues or did the log entries just cause you to worry?

An OS shouldn't lock up.  Typically, the dmesg output would show a stack trace when that sort of issue happens and we can tell based on the stack what the likely issue is.  For example, I had a Ryzen system with 3200Mhz RAM that was crashing daily.  The RAM was from 2 unmatched sets.  When I pulled 2 of the sticks out, the system never crashed.  If I pulled the other 2 sticks out and put the original RAM back in, it never crashed.  That made it clear that even with 4 RAM sticks with exactly the same model, speed, and vendor, they weren't "matched".  The solution is to return all 4 sticks and get a matched set or to slow down the RAM from 3200 until it becomes stable.  For about a year, running at 2800Mhz, it was stable, then it got finicky again, so I slowed it down to 2600Mhz and it has been stable over a year at that speed.  The system is on 24/7/365 and I reboot it only when a new kernel gets installed, like today.
```
$ uptime
 21:46:39 up 7 days,  4:32,  5 users,  
```
I haven't rebooted today, but will probably in the morning. No hurry.

The way to find issues in logs is either with 'journalctl -perr'
or
'sudo egrep -i 'warn|erro' /var/log/*og'

There are things that will show up in those commands that aren't really errors. Research each to see if they apply to your system or not.  Most will not.

---

