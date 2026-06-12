---
title: "Modify USB stick for Ubuntu live"
date: 2024-06-18
forum: General Help
---

### Post by lapetesson on 2024-06-18
I've recently started using Ubuntu Live on a PC. I have no intention to install Ubuntu on a hard drive; I'll be booting it from the USB stick. I would like to make some changes either in the ISO image before I burn it or on the USB stick after burning. Clearly, I would also consider making permanent changes to the USB stick during an Ubuntu session, but it doesn't seem possible. One thing that I would like to change first is the WiFi parameters, so I don't have to do it each time I boot. I know which file under /etc keeps WiFi data. How can I add this data to the Ubuntu bootable image?

I'm rather new to Linux, but I worked with Unix for three decades, and I love vi.

---

### Post by tea for one on 2024-06-18
Three choices for you to consider:-

(a) Use mkusb to create a live system with persistence [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
(b) Full installation to your external device with username and password login
(c) Remaster the iso with Cubic [https://github.com/PJ-Singh-001/Cubic](https://github.com/PJ-Singh-001/Cubic)

---

