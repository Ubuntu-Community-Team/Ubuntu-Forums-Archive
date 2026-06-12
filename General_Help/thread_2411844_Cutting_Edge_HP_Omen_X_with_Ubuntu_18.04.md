---
title: "Cutting Edge HP Omen X with Ubuntu 18.04"
date: 2019-02-04
forum: General Help
---

### Post by markackerman8@gmail.com on 2019-02-04
Most Everything is WORKING AWESOMELY!!  Good Job Ubuntu !!!!
Nvidia 415 now just as good (except ever so slight jittering with window movement)
Nvidia GTX 1080 Working Well EXCEPT!
1/ No Kernel support for NVHDA HDMI Sound MODULE, must load the module independently.
2/ Hibernation/ Suspend/ Hybrid Sleep leads to dysfunctional NVHDA Sound and must be manually turned OFF before and back on After - SIMPLY AWKWARD 
$ sudo tee /proc/acpi/nvhda <<< OFF          (before Hibernation/Suspend or Sleep)
• $ sudo tee /proc/acpi/nvhda <<< ON            (After Resume)
3/ Suspend with above workaround works great, but Hibernation and Hybrid Sleep lead to NO Blinking Cursor to wake up, and no possible way to wake up without rebooting  AWKWARD

Always trying to help Mark

---

