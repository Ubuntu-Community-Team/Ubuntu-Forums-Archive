---
title: "Characters missing on the screen with NVIDIA proprietary drvers"
date: 2024-12-08
forum: General Help
---

### Post by simone-c on 2024-12-08
Hi,

A random issue when after waking up the laptop the login screen and the toolbar may be missing characters. I have seen that in the past happening once a half-year.
But recently it started to occur almost every day. When it happens I need to blindly find log out button and re-login. Then it will work for for a few suspends, but then will happen again and require to logout/login.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=294613&stc=1[/IMG][IMG]https://ubuntuforums.org/attachment.php?attachmentid=294614&stc=1[/IMG]

Latest Ubuntu 24.04.1
Nvidia driver installed using "ubuntu-drivers" utility
nvidia-driver-550:
  Installed: 550.120-0ubuntu0.24.04.1

This happens with any DE: Ubuntu, Gnome, Gnome classic, on Wayland or not.
This does not happen with Nouveau driver.
But I need Nvidia driver for OpenCL :(

Is there any way to fix this? :(

---

### Post by simone-c on 2024-12-09
Found another similar question: [https://askubuntu.com/questions/1512797/most-characters-disappearing-in-gnome-after-suspend](https://askubuntu.com/questions/1512797/most-characters-disappearing-in-gnome-after-suspend)

The proposed workaround of adding `options nvidia NVreg_PreserveVideoMemoryAllocations=1` did not help.

But at least I found how to restore characters without killing the whole Gnome:

1. open Tweaks app
2. go to Fonts
3. change Rendering back and forth (ex, from Full to Slight and then back to Full)
4. characters are back

---

