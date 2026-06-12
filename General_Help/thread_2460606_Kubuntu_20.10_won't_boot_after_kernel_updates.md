---
title: "Kubuntu 20.10 won't boot after kernel updates"
date: 2021-04-14
forum: General Help
---

### Post by benwoodworth on 2021-04-14
My computer gets stuck at the motherboard splash screen when I boot with the latest kernels:
[LIST]
[*]Splash screen 
[*]Grub -> auto selects Ubuntu 
[*]Splash screen (frozen. normally shows kubuntu logo after) 
[/LIST]

I can select "Advanced options for Ubuntu" in Grub, and boot with "Ubuntu, with Linux 5.8.0-44-generic" just fine, but booting from the newer kernels (5.8.0-45, -48, -49) has this issue.

I'm not sure how to go about troubleshooting this, or what logs would be useful, but I'd be happy to share more info if needed :)

Here's my system info:
```
Operating System: Kubuntu 20.10
KDE Plasma Version: 5.19.5
KDE Frameworks Version: 5.74.0
Qt Version: 5.14.2
Kernel Version: 5.8.0-44-generic
OS Type: 64-bit
Processors: 4 × Intel® Core™ i5-7500 CPU @ 3.40GHz
Memory: 23.4 GiB of RAM
Graphics Processor: AMD Radeon RX 5500 XT
Motherboard: MSI B150M MORTAR
```

---

### Post by Xian on 2021-04-15
Let's 1st try the low-hanging fruit:

Update grub with the command:
```
sudo update-grub
```

If still not working post the output of the following:

```
cat /boot/grub/grub.cfg
```
```
ls /boot
```

---

### Post by benwoodworth on 2021-04-15
Thank you for replying! Running update-grub didn't help, so I attached the outputs from those commands :)

---

