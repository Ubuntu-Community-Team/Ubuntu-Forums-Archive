---
title: "Ubuntu 17.10 not loading login screen/boot loop"
date: 2018-01-13
forum: General Help
---

### Post by quantumtrading on 2018-01-13
Hey guys, 

This is very strange what has happened after I updated my workstation.

My driver situation is I have Cuda toolkit 8 installed with the following output from Nvidia-smi.

```
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 387.26                 Driver Version: 387.26                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 1070    Off  | 00000000:01:00.0  On |                  N/A |
|  0%   40C    P8     8W / 166W |    316MiB /  8112MiB |      3%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0       883      G   /usr/lib/xorg/Xorg                            18MiB |
|    0       938      G   /usr/bin/gnome-shell                          52MiB |
|    0      1147      G   /usr/lib/xorg/Xorg                           130MiB |
|    0      1290      G   /usr/bin/gnome-shell                         112MiB |
+-----------------------------------------------------------------------------+


```

Below is a link to the output of the command

```
cat /var/log/Xorg.0.log
```

[http://termbin.com/e23t](http://termbin.com/e23t)

the weirdest part is this only started occuring after my desktop did a kernal upgrade. After booting into grub and selecting the kernal below the top it worked fine. 

Any help would be greatly appreciated since this computer is critical to my Ai research.

---

### Post by quantumtrading on 2018-01-13
I had forgotten to add, what happens is the computer will boot up, show the ubuntu screen loading, go black, then go to the terminal, black, back to term, black etc.

---

