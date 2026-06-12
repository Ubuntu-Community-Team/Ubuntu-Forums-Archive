---
title: "Bottom of screen jitter w/ Quadro M1000M GPU and nVidia driver on Ubuntu 20.04"
date: 2021-11-27
forum: General Help
---

### Post by dev-1one-w01f on 2021-11-27
Hi there, I wonder if anyone encountered a similar problem before and figured out a fix for it.

**Problem**

I got a laptop computer that has a Quadro M1000M and runs Xubuntu 20.04. The problem is that if I use the laptop's monitor, there would be a horizontal band of jitter (around 24 rows of pixels on the bottom of the screen, sometimes more, sometimes less, but the rest of the screen looks fine), which is very annoying. Occasionally the jitter won't be there (perhaps once per 20 reboots), but most of the times it will be. An example is shown in the animated gif below (the application opened is gedit, and the text editing area is OK but the bottom status bar is in the jittery area).

[IMG]https://i.stack.imgur.com/bEmHE.gif[/IMG]

Interestingly, if I use an external monitor, this horizontal band of jitter doesn’t appear. If I use an external monitor + the laptop monitor and mirror the display (both monitors share the same resolution of 1920x1080), the jitter will still exist on the laptop monitor, but not on the external monitor. Whether the external monitor is connected to the laptop’s HDMI or thunderbolt or mini DP does not affect this observation.

**Attempts to diagnose and fix the problem**

First of all, I am quite sure that it’s not a faulty laptop monitor. There’s no jitter in BIOS and the Grub menu. And if I uninstall the Nvidia driver, the jitter does not appear when Xubuntu 20.04 loads. Similarly, if I boot other OSes (e.g. another version of Ubuntu from USB thumbdrive w/o the Nvidia driver), the jitter also does not appear.

The laptop is configured in BIOS to only use "Discrete Graphics" and not the Intel GPU nor Prime. Both "xserver-xorg-video-intel" and "xserver-xorg-video-nouveau" were removed with "apt purge". "nouveau" is also blacklisted. In case it matters, the Xubuntu I'm running is not a fresh installation. It was upgraded from 18.04, which was in turn upgraded from 16.04.

Here is a list of what I tried so far, and unfortunately the jitter is still there: 

[LIST]
[*]various versions of the Nvidia driver (e.g. v495, v470, v460, v450), same jitter 
[*]downgrading to some recent but older versions of kernel, same jitter 
[*]upgrading the system firmware (BIOS) to the latest version, same jitter 
[*]switching the display manager from "lightdm" to "gdm3", same jitter 
[*]adding "nvidia-drm.modeset=1" to "GRUB_CMDLINE_LINUX_DEFAULT"  also doesn't make a difference (I can see "/sys/module/nvidia_drm/parameters/modeset:N" became "/sys/module/nvidia_drm/parameters/modeset:Y", but same jitter) 
[*]setting "Underscan" to values from 1 to 10 in "nvidia-settings", same jitter 
[*]changing/removing/resetting "/etc/X11/xorg.conf", same jitter 
[/LIST]
 
I am running out of ideas. I wonder if any of you got some suggestions for me to try out?

In case it'd help, here's the output of "sudo gpu-manager":

```

last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/5.4.0-90-generic/kernel
Looking for nvidia modules in /lib/modules/5.4.0-90-generic/updates/dkms
Found nvidia.ko module in /lib/modules/5.4.0-90-generic/updates/dkms/nvidia.ko
Looking for amdgpu modules in /lib/modules/5.4.0-90-generic/kernel
Looking for amdgpu modules in /lib/modules/5.4.0-90-generic/updates/dkms
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
Vendor/Device Id: 10de:13b1
BusID "PCI:1@0:0:0"
Is boot vga? yes
Does it require offloading? no
last cards number = 1
Has amd? no
Has intel? no
Has nvidia? yes
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do

```

---

