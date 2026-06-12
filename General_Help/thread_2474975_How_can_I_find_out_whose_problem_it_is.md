---
title: "How can I find out whose problem it is?"
date: 2022-05-13
forum: General Help
---

### Post by WHK on 2022-05-13
I use ubuntu 22.04 LTS with an nvidia 1060 and 510 driver. I have a problem but I don't know what is causing it and who is responsible. How can I know who is responsible for the problem to know where to make a ticket?

The problem is that I have two monitors and when I apply night light from the gnome settings panel, it applies only to the first monitor.

How can I know where the problem is?, is it the driver? is it gnome? is it the desktop session?.

```
$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 22.04 LTS
Release:    22.04
Codename:    jammy
$ lspci -k | grep -EA3 'VGA|3D|Display'
01:00.0 VGA compatible controller: NVIDIA Corporation GP106 [GeForce GTX 1060 3GB] (rev a1)
    Subsystem: ASUSTeK Computer Inc. GP106 [GeForce GTX 1060 3GB]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
$ xrandr --query | grep HDMI
HDMI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 477mm x 268mm
HDMI-1 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 477mm x 268mm

```

---

### Post by Tadaen_Sylvermane on 2022-05-13
If you are using the official nvidia driver you report it to them. Don't think they'll do anything but worth a shot. Nvidia isn't the most friendly to linux

---

### Post by WHK on 2022-05-13
But how can I be sure that the problem is with the nvidia driver and not with the ubuntu desktop session manager o gnome settings?

---

### Post by #&amp;thj^% on 2022-05-13
If you use the Wayland session the problem lays with Nvidia: [https://forums.developer.nvidia.com/t/gnome-night-light-not-working-under-wayland/193590](https://forums.developer.nvidia.com/t/gnome-night-light-not-working-under-wayland/193590)

---

