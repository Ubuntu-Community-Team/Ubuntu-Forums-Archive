---
title: "Display Problems"
date: 2022-07-01
forum: General Help
---

### Post by jonny6363 on 2022-07-01
Hello,
I just installed Ubuntu 22.04 on my hard drive and am having display problems. The display setting is too small. It is set at 1024x768 but my monitor needs 1920x1080. I went into "settings", "display" and tried to change it but there is only that one size to choose from. I tried to look in "Additional Drivers" but that wouldn't open. The thing is when I was looking at Ubuntu on the flash drive before I installed it every thing was ok, it was set at 1920x1080, it gave me plenty of choices. I looked Additional Drivers and I noticed the drivers it had selected "Using X.Org X server - Nouveau display driver...". The other choice was nvidia-driver-390. I was wondering how to get into the Additional Drivers to see what is selected. If it's the Nvidia 390 ones I could change to the X.Org ones and see if that fixes it.

---

### Post by grahammechanical on 2022-07-01
If you go to System Settings>About>Windowing system what do you see? Is it Wayland or X-Server?

We can change from Wayland to X-Server at the login screen. Select your username and press Enter and when the password box appears look to the bottom right of the screen and click on the cog icon and select either Wayland or X-Server. You might find a difference.

I may be wrong but I understand that some Nvidia video drivers do not work very well with Wayland. And that could be the reason that Additional Drivers is not showing any options. Also, we need to be connected to the internet for Additional Drivers to find any proprietary drivers.

Regards

---

