---
title: "How to Retain Screen Resolution through Login"
date: 2021-02-21
forum: General Help
---

### Post by 7-webmaster on 2021-02-21
I have attached my large flat-screen 4K TV to my computer by HDMI.  Every time I log on to the computer the screen settings revert to the default 2160x3840 resolution.  This means that every application window displayed on this screen is too small to see at a comfortable viewing distance.  So each time I go to the settings menu and change the resolution of the screen to 1080x1920.  Ubuntu logs me out after inactivity and when I return and log on the screen resolution has reverted to 2160x3840.  For example when I logged on just now I was notified that there were updates to apply.  When I acknowledged this the update window opened on the TV, not the main display, and was too small to use.  I had to change the resolution to be able to apply the updates.  The behavior of resetting to the default on every login does not strike me as intuitive.  I would rather not have to grub around in the internal implementation of the video driver.

My TV could have indicated that the display accessed through that HDMI port was unavailable because I was using another application on the TV at the time.  But TVs buffer all of their inputs that so you can switch more quickly between applications.

VGA compatible controller [0300]: Intel Corporation UHD Graphics [8086:9
bc4] (rev 05)
    Subsystem: CLEVO/KAPOK Computer Device [1558:8535]
    Kernel driver in use: i915
    Kernel modules: i915
VGA compatible controller [0300]: NVIDIA Corporation Device [10de:1f99] 
(rev a1)
    Subsystem: CLEVO/KAPOK Computer Device [1558:8535]
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

---

### Post by CatKiller on 2021-02-21
> **7-webmaster said:**
> I have attached my large flat-screen 4K TV to my computer by HDMI... So each time I go to the settings menu and change the resolution of the screen to 1080x1920.

A much better approach would be to use the native resolution and just make things twice as big. High DPI scaling has been a thing for a while, and just making things individually bigger manually was a thing for a long time before that.

---

