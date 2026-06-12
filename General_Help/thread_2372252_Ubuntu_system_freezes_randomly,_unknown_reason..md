---
title: "Ubuntu system freezes randomly, unknown reason."
date: 2017-09-22
forum: General Help
---

### Post by cgameing on 2017-09-22
My Ubuntu system has been freezing for some reason that I cannot identity.

The hardware is fine as swapping out each part individually does not result in a stable system.
Memtest shows that the ram is working fine.
SMART tests for hard drives also show 0 issues with hard drives.

I personally checked the xorg and syslog and kern logs for problems and found nothing;
Logs available for download at: [https://drive.google.com/file/d/0BzvGhO8CahwiV2JPbXNwM0RSdlE/view?usp=sharing](https://drive.google.com/file/d/0BzvGhO8CahwiV2JPbXNwM0RSdlE/view?usp=sharing)

The magic system request keys do work. I have been able to do ALT+Sysreq+O to shutdown the system. But I am not skilled enough to know how they will benefit me. 

The crashes do not happen at high memory usage or at high CPU usage and even though I have zfs installed. Uninstalling it and removing all zfs drives also do not fix the issue.

Although weirdly enough even though the crashes can happen even at 20% memory usage. I can cause a very similar freeze to occur with the stress program. Allocating 8 gigs of ram causes a similar problem instantly. Although using Alt+Sysreq+F does not bring the system back into stability.

HardWare
WDC 500Gb hdd (Along with a few others)
Asus prime-b350 plus motherboard
XFX RX 460 gpu
Ryzen 7 1700 cpu
8Gigs corsair ddr4 ram
Be quiet 700Watt powersupply

I am completely perplexed by this issue, any help is very much appreciated.

---

### Post by ajgreeny on 2017-09-23
What hardware do you have?

---

### Post by cgameing on 2017-09-23
I updated the post

---

### Post by ajgreeny on 2017-09-24
Thanks for the post update and added info.

I see you have a Ryzen 7 1700 CPU which I seem to recall has had some difficulties with Linux, though it is many years since I have had any very new hardware, so have not bothered to investigate this.

Which Ubuntu version and which kernel are you using as there is some suggestion that kernel 4.10 minimum is required, and some users have suggested that Ubuntu-18.04 may be the best way to be sure of getting that CPU fully supported.

---

### Post by cgameing on 2017-09-25
Yeah, origionally the motherboard had some difficultys, im currently on 4.11 but changing to 4.13 doesnt help the issue.

---

