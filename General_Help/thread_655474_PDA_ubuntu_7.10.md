---
title: "PDA ubuntu 7.10"
date: 2008-01-01
forum: General Help
---

### Post by mcs1 on 2008-01-01
Hi,

I am trying for days to connect my ipaq 2490 to a ubuntu toshiba laptop. I tried everything from 5 kernel recompiles to anything else I could find. I finally got to the advise not to recompile the kernel and use the usb-rndis-lite driver which finally!! (phew) installs ok.
Now I find :
[ 8580.504000] rndis0: register 'rndis_host' at usb-0000:00:1d.2-1, RNDIS device, 80:00:60:0f:e8:00

If i start odccm I get:
** (process:5646): DEBUG: PDA network interface discovered! udi='/org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00'

However, the duevice does not regsiters and so I get with pls:

** (process:27230): WARNING **: No devices connected to odccm
pls: Could not find configuration at path '(Default)'

I read about the firewall, but no iptables is running!
I am an experienced debian user but relatively new to ubuntu, so maybe there is something I overlooked. Any help would be greatly appreciated, my family is starting to get really angry with me spending so much time in front of the box!

Cheers
Michael

---

