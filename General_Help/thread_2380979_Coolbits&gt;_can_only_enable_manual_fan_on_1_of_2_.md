---
title: "Coolbits&gt; can only enable manual fan on 1 of 2 gpus"
date: 2017-12-24
forum: General Help
---

### Post by ubuntini2 on 2017-12-24
Hi
In my xorg.conf I have the following

```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "Coolbits" "12"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option "Coolbits" "12"
EndSection
```

But when I view the **Thermal Settings** for each card in [B]NVIDIA X Server Settings
[/B]I only see 'Enable GPU Fan Settings for 1 of the 2 cards. (attached)

Any Coolbits experts able to suggest what I am doing wrong?

---

### Post by again? on 2017-12-24
Use the "enable-all-gpus" option as shown in this recent thread.
[https://ubuntuforums.org/showthread.php?t=2380735&p=13723447#post13723447](https://ubuntuforums.org/showthread.php?t=2380735&p=13723447#post13723447)

---

### Post by ubuntini2 on 2017-12-24
Thanks!
Interesting so, doing just the following 
> sudo nvidia-xconfig --enable-all-gpus

makes the following changes in the xorg.conf file

Adds **BoardName**  and **BusID** parameters

---

