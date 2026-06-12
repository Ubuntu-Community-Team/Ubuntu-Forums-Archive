---
title: "Ubuntu 12.10 High CPU Usage and System Temprature"
date: 2012-10-19
forum: General Help
---

### Post by donniezazen on 2012-10-19
Hi,

I did a clean install of Ubuntu 12.10. My system temperature is over 80C and power usage is around 28W. I have only installed few basic packages like laptop-mode-tools, lm-sensors, vim, msttcorefonts, powertop, indicator-sysmonitor, thinkfan and Chrome.

I am not using any boot parameters and I have made no system changes.

```
Linux donnie-laptop 3.5.0-17-generic #28-Ubuntu SMP Tue Oct 9 19:31:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
```

Thanks.

---

### Post by Linuxisfast on 2012-10-19
Install the proprietary drivers for your video card and see if this issue resolves, my temps on my sandy bridge asus laptop hovers around 45c and with full load at around 62c max. I don't have a discrete video card though, just built in Intel HD 3000.

---

### Post by 2F4U on 2012-10-19
It seems as if you have one of these laptops with two graphics cards. You might want to look at Bumblebee, which allows you to switch between the two graphics cards:

[http://geek.co.il/wp/2012/02/19/nvidia-optimus-on-ubuntu-12-04](http://geek.co.il/wp/2012/02/19/nvidia-optimus-on-ubuntu-12-04)

---

### Post by donniezazen on 2012-10-19
I have disabled Nvidia Card from BIOS so that I can have a silent system.

My base temperature seems to be atleast 10-15C more than what I had on 12.04. It seems like some power regression bug in 3.5 kernel.

---

