---
title: "Issues with apps using xwayland showing up on second monitor"
date: 2022-10-21
forum: General Help
---

### Post by bryannamar on 2022-10-21
This is hard to describe so here is a picture, it does not show up when taking a screenshot. Example is using Slack which is installed as a flatpak, but i can replicate it using JOSM which is installed as a .deb, built in gnome applications and Firefox which are using wayland I can't replicate it with, so I do believe its some kind of issues with apps still using x11 on Wayland 

This happens with both 5.19 and 5.15 kernel and i am fully up to date with 22.10 packages. This is installed on ZFS 

[https://imgur.com/a/yJIytux](https://imgur.com/a/yJIytux)

OS: Ubuntu 22.10 kinetic
Kernel: x86_64 Linux 5.15.0-52-generic
Uptime: 4h 50m
Packages: 3235
Shell: bash 5.2.2
Resolution: 4480x1440
DE: GNOME 43.0
WM: Mutter
WM Theme: Adwaita
GTK Theme: Adwaita-dark [GTK2/3]
Icon Theme: Yaru
Font: Cantarell 11
Disk: 4.2T / 8.6T (49%)
CPU: AMD Ryzen 9 5900X 12-Core @ 24x 3.7GHz
GPU: AMD Radeon RX 5700 XT (navi10, LLVM 14.0.6, DRM 3.42, 5.15.0-52-generic)
RAM: 27035MiB / 32023MiB

---

### Post by TheFu on 2022-10-21
The fix is easy. Use X11, not Wayland.  This is a selection BEFORE logging in.  If that fixes the problem, then you have a choice to make.  Use Wayland or use X11.

Wayland breaks many workflows, including lots of automation tools and screen capture tools.  A few have been rewritten to use the "Wayland way" of doing things, but it will probably take many yrs for those tools to mature to the same level that it took the older X11 tools to mature.  That's the nature of new methods and new software.  It takes time to mature.  

Hopefully, they will get there before the next new thing comes along.  It would be great to have the vastly improved security of Wayland, but retain all the features, like network agnostic communications between X-clients and X-Servers, that have proven to be so very awesome over the last 40 yrs.

You say 22.10.  Does 22.04 have the same issue? Did it work with Wayland on other kernels, with other drivers?

---

