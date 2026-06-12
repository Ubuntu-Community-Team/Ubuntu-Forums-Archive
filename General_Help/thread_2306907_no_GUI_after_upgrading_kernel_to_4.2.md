---
title: "no GUI after upgrading kernel to 4.2"
date: 2015-12-20
forum: General Help
---

### Post by rivy2 on 2015-12-20
I had version 3.13.0-generic installed before and just installed linux-image-4.2 via apt.
After rebooting I'm presented with a terminal login and no gui afterwards.
Is there a way to restore the old version (3.13) or do I have a chance to fix xfce?
Also, it must have messed up some dns settings since every host is unknown. (no internet)

Every help appreciated.

regards,
rivy

[update]:
I found a way to boot into an old kernel by holding down shift and going into the grub menu, then advanced options and selecting an old kernel
Now I only need to set an older version as the default version, right?..

---

### Post by ajgreeny on 2015-12-20
Which version of Xubuntu?  The original kernel is from 14.04 so I presume that is what you are still running, and like me, you keep with the LTS versions.

What graphic card do you have, using which driver?  That new kernel may perhaps have problems with drivers if you use proprietary versions from AMD or Nvidia, though I am not aware of details of any, and I haven't tried a newer kernel, and I also have only on-board Intel graphics.

---

### Post by rivy2 on 2015-12-20
Yeah, I'm keeping with the LTS version 14.04, 64bit.
The GPU is a nVidia GF117M and I also have on-board intel graphics.
NVIDIA Driver version is currently 340.96, proprietary

---

### Post by grahammechanical on 2015-12-20
You could try reverting to the open source video driver and then seeing if you can load to a desktop with the Linux 4.2 kernel. When we are successfully loading with an open source video driver we can then run a command. The output from that command might indicate a failure to compile a video driver module or something else that might explain why this is going wrong.

```
ubuntu-drivers autoinstall
```

That command will install the latest current proprietary video driver. This command will give information about our video adapter and the drivers available in the repositories.

```
ubuntu-drivers devices
```

Regards.

---

