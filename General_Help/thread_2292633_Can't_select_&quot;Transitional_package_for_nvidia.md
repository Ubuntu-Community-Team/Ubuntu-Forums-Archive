---
title: "Can't select &quot;Transitional package for nvidia-opencl-icd-340-updates&quot;"
date: 2015-08-29
forum: General Help
---

### Post by PenguinLust on 2015-08-29
...using the s/w updater, for the past several week, w/no explanation as to why. Why?

I'm using Ubuntu 14.04.3 64-bit

---

### Post by Vladlenin5000 on 2015-08-29
Do you have the nvidia 340 installed or some other version?
What you described suggests you had it and there are remains of it but you aren't currently using it.

---

### Post by PenguinLust on 2015-09-08
Yes, I do, actually ("proprietary, tested"). There's one that I'm not using which is nvidia-340-updates (which is only "proprietary"). Perhaps that's why it's disabled.

---

### Post by efflandt on 2015-09-09
Which nvidia drivers do you have installed? It looks line nvidia-331, nvidia-331-updates, and nvidia-340-updates packages all use the same 340.76 driver version. The only nvidia-opencl-icd that is described as "Transitional package for nvidia-opencl-icd-340-updates" is nvidia-opencl-icd-331-updates. What is listed when you do:```
dpkg-query -l nvidia* | grep ii
```My desktop PC runs xorg-edgers nvidia-352, but I have not noticed any issues on my laptop running nvidia-331-updates from standard repos:```
efflandt@GE60-2OE:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-331-updates                                    340.76-0ubuntu0.1                                   amd64        Transitional package for nvidia-331-updates
ii  nvidia-340-updates                                    340.76-0ubuntu0.1                                   amd64        NVIDIA binary driver - version 340.76
ii  nvidia-opencl-icd-331-updates                         340.76-0ubuntu0.1                                   amd64        Transitional package for nvidia-opencl-icd-340-updates
ii  nvidia-opencl-icd-340-updates                         340.76-0ubuntu0.1                                   amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver
```

---

### Post by PenguinLust on 2015-09-10
Strange. What I get is slightly different, but perhaps not so unexpected, since the updater is disabling that package. Perhaps this is just academic, since I'm using a proprietary driver.
```

ii  nvidia-331                                            340.76-0ubuntu0.1                                   amd64        Transitional package for nvidia-331
ii  nvidia-331-uvm                                        340.76-0ubuntu0.1                                   amd64        Transitional package for nvidia-340-uvm
ii  nvidia-340                                            340.76-0ubuntu0.1                                   amd64        NVIDIA binary driver - version 340.76
ii  nvidia-340-uvm                                        340.76-0ubuntu0.1                                   amd64        Transitional package for nvidia-340
ii  nvidia-opencl-icd-331-updates                         331.113-0ubuntu0.0.4                                amd64        NVIDIA OpenCL ICD
ii  nvidia-opencl-icd-340                                 340.76-0ubuntu0.1                                   amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                          0.6.2                                               amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                                       331.20-0ubuntu8                                     amd64        Tool for configuring the NVIDIA graphics driver

```

---

