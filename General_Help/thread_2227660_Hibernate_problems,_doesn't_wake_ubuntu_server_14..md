---
title: "Hibernate problems, doesn't wake: ubuntu server 14.04 on desktop"
date: 2014-06-03
forum: General Help
---

### Post by tga2 on 2014-06-03
for the past 3 weeks I've been working on setting up an old  hp pavillon a1540n with ubuntu server 14.04. Main problem is the  hibernate/suspend process. I've done a lot of reading and made great  progress thus far, but I feel I reached a point where Google isn't  helping anymore. 
  
Right now, pm-hibernate saves to disk correctly, computer stops  making sounds, but the screen shows a blinking cursor. After that, no  event can wake it up and I have to force shutdown by pressing and  holding the power button. On restart however, it loads perfectly and  resume where I left. This leaves me thinking that somehow no events can  wake it up.

  Here is a short list of any effective actions I've done that I can think of: 
-Removed graphics card and tv tuner card 
-Updated BIOS to 5.07 (no new option for power management though, but it helped)
 -Updated driver to nvidia 330 (latest recommended)

  Doing basic pm-debugging (basic-pm-debugging.txt#178 on mjmwired dot  net), using reboot works fine but using platforms create the same  problem as pm-hibernate.

  Pastebins: 
dmesg: [http://pastebin.com/b1KPb4gi](http://pastebin.com/b1KPb4gi) 
pm-suspend.log: [http://pastebin.com/5WAGrFgR](http://pastebin.com/5WAGrFgR) 
/proc/acpi/wakeup: 

  Device  S-state   Status   Sysfs node
HUB0      S5    *disabled  pci:0000:00:10.0
XVRA      S5    *disabled  pci:0000:00:04.0
XVRB      S5    *disabled
XVRC      S5    *disabled  pci:0000:00:02.0
USB0      S3    *enabled   pci:0000:00:0b.0
USB2      S3    *enabled   pci:0000:00:0b.1
AZAD      S5    *disabled
MMAC      S5    *enabled   pci:0000:00:14.0
MMCI      S5    *disabled
PS2M      S4    *disabled  pnp:00:07
PS2K      S4    *enabled   pnp:00:08
  Thanks for any suggestions

---

