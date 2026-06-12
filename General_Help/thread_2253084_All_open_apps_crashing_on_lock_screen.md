---
title: "All open apps crashing on lock screen"
date: 2014-11-17
forum: General Help
---

### Post by Prince Linux on 2014-11-17
I have this serious issue. Whenever the xubuntu goes to lockscreen on timeout or i lock the screen, all the apps are forcefully closed.
Does any one facing or faced similar issue ?
Any solution please. I have disabled lockscreen for now.

Kernal and version

Linux version 3.13.0-39-generic (buildd@toyol) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #66-Ubuntu SMP Tue Oct 28 13:30:27 UTC 2014

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

I am using Xubuntu

---

### Post by Chris_Borkowski on 2015-01-22
> **Prince Linux said:**
> Does any one facing or faced similar issue ?

Yes, I do. My desktop-pc does exactly the same with Xubuntu 14.10. (x64). Somethimes, the xserver crashs, the video display goes crazy (weird, colored quares all over the screen or the resolution drops to 1024x764 or I have to log in over and over again).
Weirdly, my laptop doesn't do this at all and it has a cloned copy of the desktop's Xubuntu on it (so the exact same software). The only difference is the graphic-driver (fglrx at desktop with a HD 7850, free radeon driver on the laptop, which has the IGP of the HP 625 - something like HD 4250).
But as far as I remember, switching to the free radeon at the desktop didn't solve the problem.

> **Prince Linux said:**
>  Any solution please. I have disabled lockscreen for now.

I just got a workaround: Disable Light Locker and use xscreensaver.

---

