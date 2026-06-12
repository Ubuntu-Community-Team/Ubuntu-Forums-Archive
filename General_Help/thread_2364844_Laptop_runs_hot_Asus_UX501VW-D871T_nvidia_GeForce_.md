---
title: "Laptop runs hot Asus UX501VW-D871T nvidia GeForce GTX 960M"
date: 2017-06-28
forum: General Help
---

### Post by 007casper on 2017-06-28
Laptop runs hot. It sometimes reaches 92 degrees... usually hovers around 68-72 degrees.

I tried multiple things but couldnt bring the temperature down. The only option is... I shut down and wait for the laptop to cool down.

cpu fan 3300rpm 
cpu fan min 800rpm
cpu fan max 4200rpm

Please, advise. Thank you.

laptop - Asus UX501VW-D871T 

video card - nvidia GeForce GTX 960M

nvidia driver - 381.22

OS - ubuntu 17.04

uname -r
4.10.0-22-generic

nvidia-smi
Mon Jun 19 10:29:03 2017       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 381.22                 Driver Version: 381.22                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 960M    Off  | 0000:01:00.0     Off |                  N/A |
| N/A   60C    P5    N/A /  N/A |   1471MiB /  2002MiB |     18%      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0      8736    G   /usr/lib/xorg/Xorg                            1196MiB |
|    0      9458    G   /usr/bin/compiz                                268MiB |
|    0      9713    G   /usr/lib/firefox/firefox                         3MiB |
+-----------------------------------------------------------------------------+

---

### Post by 007casper on 2017-06-28
[IMG]http://imgur.com/a/PYQqP[/IMG]

link image
[http://imgur.com/a/PYQqP](http://imgur.com/a/PYQqP)

---

### Post by gsahli on 2017-06-28
run terminal command top and watch for high/persistent CPU use.

Also, Check out these recommendations.
[https://itsfoss.com/reduce-overheating-laptops-linux/](https://itsfoss.com/reduce-overheating-laptops-linux/)

---

