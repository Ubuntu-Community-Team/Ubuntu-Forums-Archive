---
title: "Nvidia install loop back to login: what to remedy"
date: 2022-04-25
forum: General Help
---

### Post by hrsetrdr on 2022-04-25
After installing Nvidia drivers and rebooting I've encountered the " loop back to login" situation.   If there's a solution to get past this ,I would love to know.

---

### Post by aug7744 on 2022-04-25
Try start the machine use disc or USB installation and access your /home.
Try see the what is the owner of /home.
If owner not is you try fix.

---

### Post by Bashing-om on 2022-04-25
hrsetrdr; Hello

Secure boot enabled ? As the Nvidia driver is 3rd party - secure boot is doing it's job/
What shows:
```

mokutil --sb-state

```

[INDENT]maybe yes
[INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT]

---

### Post by hrsetrdr on 2022-04-26
> **Bashing-om said:**
> hrsetrdr; Hello

Secure boot enabled ? As the Nvidia driver is 3rd party - secure boot is doing it's job/
What shows:
```

mokutil --sb-state

```

[INDENT]maybe yes
[INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT]

This machine doesn't have Secure Boot, has legacy BIOS.   I had just installed Ubuntu, and chose the 510 Nvidia Proprietary Drivers  from the "Software & Updates / Additional Drivers feature.  Upon reboot it would get to the log-in screen, but once the password was given, rather than boot to desktop it just came back to log-in.  I didn't see an opportunity to get a grub prompt or other means to get back into the OS.

---

### Post by Bashing-om on 2022-04-26
hrsetrdr; Well well ...

The plot do thicken :(

OK not but ... 
what release are you running and what is the desktop ( Wayland/22.04/Nvidia has it own set of issues)
```

lsb-relase -a
ps -efly | grep Xorg
loginctl session-status
cat /var/log/gpu-manager.log

```
Also here we see what the GPU manager has to say.

[INDENT]gots to be a reason
[/INDENT]

---

### Post by hrsetrdr on 2022-04-26
> **Bashing-om said:**
> hrsetrdr; Well well ...

The plot do thicken :(

OK not but ... 
what release are you running and what is the desktop ( Wayland/22.04/Nvidia has it own set of issues)
```

lsb-relase -a
ps -efly | grep Xorg
loginctl session-status
cat /var/log/gpu-manager.log

```
Also here we see what the GPU manager has to say.

[INDENT]gots to be a reason
[/INDENT]

This was/ is release 20.04.4, Mate DE.  Since this conversation began, I've since re-installed and am staying with the 470 drivers, there doesn't appear to be any benefit to upgrading to the 512.xx drivers...I'm running folding@home and not looking to optimize video gaming.    Looks to be pretty stable, I still would like to know what a person can do to fix the loop back to log-in situation.

---

### Post by hrsetrdr on 2022-05-18
> **Bashing-om said:**
> 

cat /var/log/gpu-manager.log



```
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/5.13.0-41-generic/kernel
Looking for nvidia modules in /lib/modules/5.13.0-41-generic/kernel/nvidia-510srv
Looking for nvidia modules in /lib/modules/5.13.0-41-generic/kernel/nvidia-510
Found nvidia.ko module in /lib/modules/5.13.0-41-generic/kernel/nvidia-510/nvidia.ko
Looking for amdgpu modules in /lib/modules/5.13.0-41-generic/kernel
Looking for amdgpu modules in /lib/modules/5.13.0-41-generic/updates/dkms
Is nvidia loaded? yes
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? no
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? yes
Is amdgpu kernel module available? no
Vendor/Device Id: 10de:2504
BusID "PCI:1@0:0:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Skipping "/dev/dri/card0", driven by "nvidia-drm"
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Takes 0ms to wait for nvidia udev rules completed.
Single card detected
Nothing to do
```

---

### Post by Bashing-om on 2022-05-18
hrsetrdr - well :)

gpu manager seems in a happy state.

---

### Post by hrsetrdr on 2022-05-18
OK so I did a tty login, removed the nvidia drivers and enabled the  Nouveau driver. So now I can work on what happened, because I want to know(yes, I'm jiggy like that).  Although, I did earleir today install debian(shrank a partition) and am doing my[ f@h]("https://foldingathome.org/start-folding/?lng=en") there nicely, ATM. Never hurts to have alternatives. ;)

---

