---
title: "Screen goes blank after a while"
date: 2013-05-04
forum: General Help
---

### Post by theknuckler on 2013-05-04
Howdy ya'll. I'm running 12.04 and every now and then randomly while I'm surfing the internet, or whatever, the screen will just turn white, and I cannot get out of it without doing a hard reboot. I had this problem with 11.10 and I thought maybe if I upgraded that would help. It didn't. Could it be a hardware problem? I reall am computer illiterate, especially with ubuntu, so I have no idea what to do.

---

### Post by romain.astie on 2013-05-05
Seems like this may be a variant of a known bug: [https://bugs.launchpad.net/bugs/913555](https://bugs.launchpad.net/bugs/913555)
Only difference is that your screen goes white whereas the bugs report says it goes black.
If it is this, then it's a software problem, not hardware. Maybe it has been fixed in later versions... I don't know

---

### Post by claracc on 2013-05-05
> **theknuckler said:**
> Howdy ya'll. I'm running 12.04 and every now and then randomly while I'm surfing the internet, or whatever, the screen will just turn white, and I cannot get out of it without doing a hard reboot. I had this problem with 11.10 and I thought maybe if I upgraded that would help. It didn't. Could it be a hardware problem? I reall am computer illiterate, especially with ubuntu, so I have no idea what to do.

It would be good to obtain advice to know what kind og graphic card you have.

In a xterm, write the following code ```
sudo lshw -C video
```
and post the rsults here.

---

### Post by theknuckler on 2013-05-05
> **claracc said:**
> It would be good to obtain advice to know what kind og graphic card you have.

In a xterm, write the following code ```
sudo lshw -C video
```
and post the rsults here.

*-display:0             
       description: VGA compatible controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:45 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:e140(size=8)
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile 4 Series Chipset Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
       resources: memory:d0400000-d04fffff



i dont know what that means but thanks for the replies so far! Also, I upgraded t 12.10 and the problem has been persisting... sometimes after 10 minutes... sometimes after an hour.

---

### Post by theknuckler on 2013-05-05
anyone else have suggestions?

---

