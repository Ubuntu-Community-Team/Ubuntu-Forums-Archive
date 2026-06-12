---
title: "Opencl doesn't detect gpu after suspend"
date: 2021-03-01
forum: General Help
---

### Post by neodimiummagnet on 2021-03-01
I've been going crazy trying to figure this one out. Clinfo detects my gpu fine on boot with a themed desktop and cuda applications work. When I change my desktop's theme in any way (icon set, wallpaper, etc) and wake from suspend, clinfo shows 0 platforms and programs that use cuda no longer detect my gpu. Nvidia-smi still shows everything functioning as normal. Changing the theme back to defaults and rebooting makes opencl work again, even after subsequent suspends.

I have an Nvidia 3060 ti and nvidia driver 460. I tried on both a fresh install of Xubuntu and Kubuntu 20.04.2, using both the default kernel 5.8 and mainline 5.10. 

I have no idea how to even begin to troubleshoot this. Any help is appreciated.

---

### Post by neodimiummagnet on 2021-03-08
Bump. It's been about a week, haven't made any headway on this, and having to restart my computer every time it goes to sleep is quite annoying.

---

