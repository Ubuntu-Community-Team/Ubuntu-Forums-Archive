---
title: "Why couldn’t I suspend/hibernate my laptop without NVIDIA driver?"
date: 2023-08-11
forum: General Help
---

### Post by yurad on 2023-08-11
I recently had the following incident with NVIDIA driver. (There was a thread [https://ubuntuforums.org/showthread.php?t=2486253&p=14140407#post14140407](https://ubuntuforums.org/showthread.php?t=2486253&p=14140407#post14140407))  I had NVIDIA-driver-525 installed on my Asus X556UQ  running Ubuntu 22.04.  The PRIME profile was set as “NVIDIA on demand”. GNOME and  Plazma sessions were crashing every 2-3 days and I decided to try  NVIDIA-driver-530. The driver was installed via Ubuntu “software  and updates”. After a reboot, the X server did not start. I got a black  screen instead of the GUI login screen. In the virtual terminal, I changed  prime-select to “intel”.  After a reboot, I was able to open a GNOME session. Then I  found that my network, WiFi, Bluetooth, touchpad and sound were gun. I  also couldn’t suspend/hibernate. After that, I did the following steps:

    I uninstalled NVIDIA driver and rebooted again. It didn’t change anything.
    I reinstalled linux-modules-extra-5.15.0-71-generic. All devices were back, but,  suspend to memory still didn’t work.
    I blacklisted Nouveau driver ( Nouveau didn’t work with my card ).  Suspend/hibernate didn’t work
    I reinstalled nvidia-driver-525. Suspend/Hibernate started working.

Why suspend/hibernate didn’t work for me without reinstalling  NVIDIA driver?

---

