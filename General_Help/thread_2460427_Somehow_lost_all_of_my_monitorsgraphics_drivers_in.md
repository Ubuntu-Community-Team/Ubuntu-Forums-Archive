---
title: "Somehow lost all of my monitors/graphics drivers in Xubuntu 20.04"
date: 2021-04-09
forum: General Help
---

### Post by robp2175 on 2021-04-09
I was trying to get my Bluetooth to work properly and along the way I seem to have hosed my monitors. Now it will only recognize one monitor, but only as default. It was suggested to fix bluetooth to install

```
apt install linux-modules-extra-5.8.0-34-generic
```
but immediately after that my graphics were completely wonky. Only half the text showed up for everything on screen. So I uninstalled that package and rebooted, but now I have lost multiple monitor functionality. I have an onboard radeon card. I tried reinstalling xubuntu-desktop but that did nothing.

I would appreciate any ideas.

```
$ xrandr --listmonitors
xrandr: Failed to get size of gamma for output default
Monitors: 1
 0: +default 1920/508x1080/286+0+0  default
```

---

### Post by TheFu on 2021-04-09
Try:
```
sudo apt update
sudo apt full-upgrade
sudo ubuntu-drivers autoinstall
```

---

