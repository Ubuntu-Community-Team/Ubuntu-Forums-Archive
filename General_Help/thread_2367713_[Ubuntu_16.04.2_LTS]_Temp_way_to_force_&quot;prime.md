---
title: "[Ubuntu 16.04.2 LTS] Temp way to force &quot;prime-select nvidia&quot; in Grub?"
date: 2017-08-02
forum: General Help
---

### Post by G226 on 2017-08-02
Hello Everyone, Hope your day is going good.

I recently installed Ubuntu 16.04.2 LTS on a Dell 9650, I was trying to follow various guides for power savings, proper drivers etc and ended up installing nvidia drivers and then decided to try testing out swapping to intel via "[COLOR=#111111][FONT=Consolas]sudo prime-select intel"
[/FONT][/COLOR]
This prompted for a restart/logout, I opted to restart. When I did so I got a black screen after I successfully input my encryption password. The login screen I'd normally see before selecting intel graphics via Nvidia prime, I was instead met with a black screen.
To note, after installing appropriate nvidia drivers, a reboot was done which let me login via the ui as expected just fine and I could get into the OS.

After doing some reading I held shift on boot to get to grub, then tried hitting "e" in grub and setting "nomodeset" in the appropriate location but that got me to a purple screen.
[B]
Question:[/B] Is there a way to temporarily force "prime-select nvidia" via the grub "e" menu and then boot into that so I can install what I think are the needed intel drivers?

Thanks

---

### Post by #&amp;thj^% on 2017-08-02
The Intel drivers are installed automatically with the install. So nothing to install there.
How did you install the nvidia driver?
```
Graphics:  Card-1: Intel Sky Lake Integrated Graphics
           Card-2: NVIDIA GF114 [GeForce GTX 560 Ti]
           Display Server: X.Org 1.19.3 driver: nvidia
           Resolution: 1920x1080@60.00hz
           GLX Renderer: GeForce GTX 560 Ti/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 384.59

```
EDIT what dose this show?
```
modprobe -R nvidia

```

---

