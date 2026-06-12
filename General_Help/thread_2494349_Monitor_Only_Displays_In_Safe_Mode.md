---
title: "Monitor Only Displays In Safe Mode"
date: 2024-01-13
forum: General Help
---

### Post by AtsCalgary on 2024-01-13
A couple of days ago I booted up my desktop running 22.04. And it was only displaying in 1024x768 with a border around the screen. 
When I rebooted to see if that would clear the issue I noticed that my bootloader was no longer available to use recovery mode. I've tried several fixes including a fresh install with no luck. After the first reboot post install, I had full resolution(1920x1080) but my keyboard and mouse weren't recognized, I rebooted and ran recovery mode and was able to get my keyboard and mouse running but the display is not recognized and is at default settings. The system is using the correct driver for my GTS450 - nvidia-driver-390.
Any recommendations would be greatly appreciated.

EDIT: In recovery if I launch 6.2.0-26 , I have no issues. with 6.5.0-14 the issue is present.

---

### Post by MAFoElffen on 2024-01-13
Do you have NVidia as a GPU?

---

### Post by AtsCalgary on 2024-01-13
Yes I do. GTS 450

---

### Post by BicyclerBoy on 2024-01-13
AFAIK nvidia 390 & 470 (as supplied by ubuntu) are both not compatible with kernel 6.5.

You need to roll kernel back to kernel 6.2 & wait.
Nvidia-470 can be made to work with kernel 6.5 but it is possible that legacy-legacy 390 never will be (think there are 3rd party hacks).

But why bother with this mess?
Have you considered just using nouveau or just simple built-in framebuffer (fbdev) driver?
You may not notice any real drop in performance.

But nouveau driver is not very stable running on GTX600 series.

---

### Post by AtsCalgary on 2024-01-13
Thanks, I'm going to stick with 6.2 and upgrade my video card shortly.

---

### Post by BicyclerBoy on 2024-01-13
Your old GTS450 prevents you from using UEFI booting.
And IMO using close source Nvidia modules makes the startup process an embarrassment.

If you upgraded to nvidia GTX1650 or higher then there is a future with new open source kernel module (nvidia driver is still closed) and you can choose to use nouveau. 
[https://www.phoronix.com/review/nvidia-open-kernel]("https://www.phoronix.com/review/nvidia-open-kernel")

I've had years of solid reliable use from Nvidia videocards (& still do in media PC) but would not recommend them unless this had happened (started to happen).

---

### Post by MAFoElffen on 2024-01-14
NVidia GTS40 is covered by legacy driver nvidia-340, which is legacy and still it the 3rd party repo's...

I've been using NVidia since 2004-2005 with Unix and Linux. They are more work, but I still recommend them.

---

### Post by MAFoElffen on 2024-01-14
I can confirm that NVidia driver do not want to build for Linux Kernel 6.5.0-14. RE: [https://forums.developer.nvidia.com/t/linux-new-kernel-6-5-0-14-ubuntu-22-04-can-not-compile-nvidia-display-card-driver/278553](https://forums.developer.nvidia.com/t/linux-new-kernel-6-5-0-14-ubuntu-22-04-can-not-compile-nvidia-display-card-driver/278553)
```

mafoelffen@Mikes-ThinkPad-T520:~$ uname -r
6.2.0-39-generic
mafoelffen@Mikes-ThinkPad-T520:~$ nvidia-smi
Sun Jan 14 06:57:34 2024       
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 390.157                Driver Version: 390.157                   |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  NVS 4200M           Off  | 00000000:01:00.0 N/A |                  N/A |
| N/A   63C    P0    N/A /  N/A |    186MiB /   964MiB |     N/A      Default |
+-------------------------------+----------------------+----------------------+
                                                                               
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID   Type   Process name                             Usage      |
|=============================================================================|
|    0                    Not Supported                                       |
+-----------------------------------------------------------------------------+
mafoelffen@Mikes-ThinkPad-T520:~$ apt list nvidia-driver-* --installed
Listing... Done
nvidia-driver-390/jammy-updates,jammy-security,now 390.157-0ubuntu0.22.04.2 amd64 [installed]
N: There is 1 additional version. Please use the '-a' switch to see it

```
My fix? I uninstalled kernel 6.5.0-14 and pinned kernel 6.2.0-39. I reinstall that kernel to make sure the header files and such were all there.
```

sudo apt remove --purge --yes linux-headers-6.5.0-14-generic linux-image-6.5.0-14-generic linux-modules-6.5.0-14-generic linux-modules-extra-6.5.0-14-generic
sudo apt install --reinstall --yes linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic
sudo apt-mark hold linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic

```
When a newer driver comes out that does work, then I will unpinned it via
```

sudo apt-mark unhold linux-headers-6.2.0-39-generic linux-image-6.2.0-39-generic linux-modules-6.2.0-39-generic linux-modules-extra-6.2.0-39-generic

```

---

