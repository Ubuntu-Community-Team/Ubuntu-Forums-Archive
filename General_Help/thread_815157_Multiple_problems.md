---
title: "Multiple problems"
date: 2008-06-01
forum: General Help
---

### Post by ReeRD on 2008-06-01
All right, so I decided to give Kubuntu 8.04 a try and pretty soon got into problems/annoyances:

1. The default Monitor/GPU driver did not allow me to change to a supported resolution (no option in the dropdown menu under Display settings) so I installed the proprietary nvidia driver. The problem with this is that it always hangs at the login screen. If I restart X (CTRL+ALT+Backspace) it starts to work ok. How do I solve this problem?

2. I still cannot select the right resolution/refresh rate combo. I need to use 1280x960x100. I can select 1280x960, but it only gives me 64Hz and 65Hz options which are ridiculous. How do I set 100Hz for this resolution?

3. There's no way to set epcific settings under System Settings CP (date and time, for example). Why?

---

### Post by cmnorton on 2008-06-02
Before trying this, it would be helpful to make sure there is a recovery option on your grub boot menu.

This sounds like you need to log into a command line as root or boot into recovery mode; cp your /etc/X11/xorg.conf to known name, and then run

dpkg-reconfigure xserver xorg. 

Other than selecting your driver and the resolutions you want to be able to display (and not display), I would take the default answers. Then reboot. 

If you cannot boot, log back into recovery and replace the /etc/X11/xorg.conf file you saved earlier.

---

