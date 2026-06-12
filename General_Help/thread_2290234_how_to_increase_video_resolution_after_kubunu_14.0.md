---
title: "how to increase video resolution after kubunu 14.04 upgrade"
date: 2015-08-10
forum: General Help
---

### Post by richardfell on 2015-08-10
I am running kubuntu 14.04 on a Dell computer with video card by Advanced Micro devices, RV620 GL (FirePro 2260). The driver is radeon.

Before upgrading, I had a wealth of choice of video resolutions. After upgrading, I am limited to the choices 1024x768, 848x480, 800x600, and 640x480. I would like to have back the finer resolutions I had before the upgrade but cannot figure out how to do it. Yes, I have searched online for help but no posted solutions to similar problems help. Many thanks for any advice.

**** Fell

---

### Post by VMC on 2015-08-10
What upgrade are you referring to? Do you recall what the upgrade was doing.
 If it upgraded your kernel then its possible DKMS wasn't triggered and your video graphics went back to default. Look at "/var/log/apt/history.log" for last update. You can usually tell what was update/upgraded.

---

### Post by richardfell on 2015-08-10
The kernel was upgraded with all that entailed.

---

### Post by VMC on 2015-08-10
Did 'xrandr' give yo the above resolutions?

---

### Post by richardfell on 2015-08-11
Yes, these are the resolutions listed by xrandr.

---

