---
title: "nvidia requires a specific kernel, but that kernel doesnt support dual core?"
date: 2007-01-03
forum: General Help
---

### Post by Choad on 2007-01-03
ok this is getting ridiculous.... need this sorted :D

i have a core 2 duo and a geforce go 6600 in my laptop

at first, the core 2 duo was detected right, because i was using the generic kernel with SMP enabled

installing the nvidia binary depended upon a different kernel, and this one doesnt have SMP

if i use the old kernel, i get no graphics, if i use the new one, i only get to use half of my expensive processor

please can someone help me!

---

### Post by Magnes on 2007-01-03
Install nvidia drivers from nvidia.com - there are some howtos.

---

### Post by Choad on 2007-01-03
i would prefer to use the repository. it has the latest stable driver anyway. the only issue here is the kernel, not the driver per se

---

### Post by majoridiot on 2007-01-03
your best bet is to download and install whichever stable binary you desire directly from
nvidia and config it with the proper kernel headers.  i doubt you'll get what you want from
a repo, unless you can find one with packages built for your specific kernel.  

[http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html)

forum help at:

[http://nvnews.net/vbulletin/forumdisplay.php?f=14&order=desc](http://nvnews.net/vbulletin/forumdisplay.php?f=14&order=desc)

---

### Post by tseliot on 2007-01-03
> **Choad said:**
> i would prefer to use the repository. it has the latest stable driver anyway. the only issue here is the kernel, not the driver per se

Try this:
1) Boot in the kernel which you would like to use
2) It might get you to the command line (instead of the desktop environment) but this is not a problem. Type:
```
sudo aptitude install linux-restricted-modules-`uname -r`
```

---

### Post by Choad on 2007-01-03
ahhh never mind, i finally got round to downloading all the updates that were due to be gotten and now the generic kernel plays nice with nvidia so all is good again :)

---

