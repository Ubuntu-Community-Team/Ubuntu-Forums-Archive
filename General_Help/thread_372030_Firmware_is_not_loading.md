---
title: "Firmware is not loading"
date: 2007-02-27
forum: General Help
---

### Post by trek on 2007-02-27
I'm running Edgy Eft 6.10 with kernel version 2.6.16.  When I boot, I get the error:

```
ipw2200: ipw-2.4-boot.fw load load failed: Reason -2
ipw2200: Unable to load firmware: -2
ipw2200: failed to register network device
```

Basically, my wireless card doesn't work because it can't find the firmware.  I have been researching this problem and several sources have mentioned having a "hotplug/firmware" directory.  I do not have this directory anywhere on my install.  

This problem did not occur until I tried to compile a 2.6.16 kernel.  I had previously been running 2.6.17.10-generic.  A copy of the ipw2200 firmware modules are located in /lib/firmware/2.6.17.10-generic.  So, I'm pretty sure my new (old) kernel doesn't know where to look for this firmware.  Or, I guess it's possible that I didn't compile the necessary options.  Does anyone have any suggestions of what to try next?

I should also mention that I do not have the headers for 2.6.16 installed.  On the the last source I found ([http://doc.gwos.org/index.php/Install_ipw2200)](http://doc.gwos.org/index.php/Install_ipw2200)), it claimed ubuntu required the headers for the kernel version you are running.  Though, I have the full source installed and compiled.  Would it make a difference that I didn't have the headers?

---

### Post by trek on 2007-02-28
bump

---

