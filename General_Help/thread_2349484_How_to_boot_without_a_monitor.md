---
title: "How to boot without a monitor ?"
date: 2017-01-15
forum: General Help
---

### Post by jean-pierre2 on 2017-01-15
Hello,

I have a gigabyte brix GB-BXBT-1900 where I installed ubuntu 16.04.1 as a server (no desktop). 
The server cannot boot if there is no monitor attached.
I just want that most of the time it can boot without a monitor. And from time to time, for a new installation or else, I can boot and login with a monitor (plus keyboard).

There is nothing related to VGA or the monitor  in the uefi bios (version F4).
I read several posts saying that a /etc/X11/xorg.conf must be created. 
Or some grub config to be modified (GRUB_CMDLINE_LINUX_DEFAULT="nomodeset")
I tried but nothing worked.

I really need to use it as a headless server, far from any monitor.
How to do that ?
TIA

JP

---

### Post by jean-pierre2 on 2017-01-21
To do that, simply modify /etc/default/grub this way :
```
GRUB_CMDLINE_LINUX_DEFAULT=""
GRUB_CMDLINE_LINUX="text"
GRUB_TERMINAL=console
```

Then ```
update-grub
```
Found here the solution : [http://www.shaunfreeman.name/gigabyte-brix-bxbt-1900-not-booting-without-monitor-on-ubuntu-minimal-16-04/](http://www.shaunfreeman.name/gigabyte-brix-bxbt-1900-not-booting-without-monitor-on-ubuntu-minimal-16-04/)

---

