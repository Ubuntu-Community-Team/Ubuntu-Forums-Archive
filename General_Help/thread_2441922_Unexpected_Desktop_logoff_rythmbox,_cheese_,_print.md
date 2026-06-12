---
title: "Unexpected Desktop logoff rythmbox, cheese , printer"
date: 2020-04-28
forum: General Help
---

### Post by ebuck on 2020-04-28
Was wondering if anyone has experienced this issue before, Ubuntu 18 LTS, PC ROG Asus x370 MB , Nvidia 1070, Ryzen 2500X. For no reason that I can think of when running printer or rythmbox or cheese I suddenly get kicked out of the desk top and have to log in again. 
I never used Rythm box or cheese before but the printer used to work HP 1080  and I only mention those two other applications because I was testing out to see if other application would do the same.  It seems to be related to USB or I/O  since all three of these programs may need input or output or  control of some devices like audio. For printer I just go into the show apps and enter printer, I swear though that I had an Icon set before on my desktop but it is gone now.  

Anyway, before I dive into solving this issue and probably spend hours,  just a quick ask if anyone has seen this and or has a fix ? 


Thanks

---

### Post by CelticWarrior on 2020-04-28
have you installed Nvidia drivers? If not, why not?

---

### Post by ebuck on 2020-04-28
Interesting you should mention that .. I could swear I installed the nvidia drivers but having checked just now I did not ...Okay then i will install them I see the latest 
Whats the visual profiler ? and I assume here I need to install the utils and xserver-xorg ?

nvidia-utils-435/bionic-updates 435.21-0ubuntu0.18.04.2 amd64
nvidia-visual-profiler/bionic 9.1.85-3ubuntu1 amd64
xserver-xorg-video-nvidia-435/bionic-updates 435.21-0ubuntu0.18.04.2 amd64

---

### Post by CelticWarrior on 2020-04-28
Just open Additional Drivers, select and apply. Reboot.
Everything it needs will be installed by the underlining script.

Also, if UEFI, disable Secure Boot.

---

### Post by ebuck on 2020-04-29
okay that seemed to work.  Thanks ..

---

