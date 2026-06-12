---
title: "Error allocating resources during boot"
date: 2008-02-05
forum: General Help
---

### Post by pormogo on 2008-02-05
Anytime I boot my box the first thing that output tells me as the box is coming up is

*[   29.281831] PCI: Cannot allocate resource region 0 of device 0000:00:00.0*

As long as the computer is coming up from a cold boot everything seems to be fine and it loads gdm and everything proceeds as normal. However when coming back from a reboot it just hangs, when I switch to tty1 to see what's going on the above message is just sitting there. 

I checked the device ID that's being referred to to and it looks like my 

*00:00.0 Host bridge: VIA Technologies, Inc. VT8385 [K8T800 AGP] Host Bridge (rev 01)*

I get this issue booting the generic x86_64 kernel as well as the kernel I compiled myself...

*Linux superb-odifference 2.6.22.9-custom-a64-01 #1 PREEMPT Wed Jan 30 19:24:21 PST 2008 x86_64 GNU/Linux*

I'm not sure why this would happen? I'm tempted to just sort of dismiss it because the only time it seems to cause a problem is when I'm rebooting my box (which is a rare occurrence). But I'm not really sure why this would happen (I don't remember ever seeing this message when running past 32bit versions of the distro, but that's not to say that it wasn't happening and I was just being less attentive).

---

