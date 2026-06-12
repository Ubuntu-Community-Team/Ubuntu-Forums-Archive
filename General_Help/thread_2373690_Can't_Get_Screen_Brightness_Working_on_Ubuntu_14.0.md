---
title: "Can't Get Screen Brightness Working on Ubuntu 14.04 LTS - HP Pavilion dm1"
date: 2017-10-08
forum: General Help
---

### Post by pcfast on 2017-10-08
I am running Ubuntu 14.04 on a HP Pavilion dm1 netbook. I can't get the screen brightness up or the screen brightness keys working. I've tried multiple solutions from Googling and checking this forum.  

Here is the exact version I am running. 
```

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty
```

As well as the all the hardware information. 

```

Architecture:          x86_64
CPU op-mode(s):        32-bit, 64-bit
Byte Order:            Little Endian
CPU(s):                2
On-line CPU(s) list:   0,1
Thread(s) per core:    1
Core(s) per socket:    2
Socket(s):             1
NUMA node(s):          1
Vendor ID:             AuthenticAMD
CPU family:            16
Model:                 6
Stepping:              3
CPU MHz:               1300.000
BogoMIPS:              2593.42
Virtualization:        AMD-V
L1d cache:             64K
L1i cache:             64K
L2 cache:              1024K
NUMA node0 CPU(s):     0,1
```

What is in my grub file. 
```


GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash video.use_native_backlight=1"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```




So what can I do to get screen brightness working? Appreciate any helps, tips, and advice.

---

### Post by pcfast on 2017-10-09
Found the solution. 

Click the Battery Icon in the Upper Right.  

Select >>> Power Settings

>>> Screen Brigthness 

Uncheck "Dim screen to save power".  

You may need to slide the Brightness up. The function keys for brightness still don't work but at least it is adjustable now.

---

