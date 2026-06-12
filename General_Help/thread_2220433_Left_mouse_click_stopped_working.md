---
title: "Left mouse click stopped working"
date: 2014-04-27
forum: General Help
---

### Post by ju2wheels on 2014-04-27
Hi all, I am running Ubuntu 12.04 on Thinkpad T410 which has been working perfectly for two years without issues. After upgrading the kernel today all mouse left click (top and bottom trackpad left click and USB mouse left click) stopped working. Its odd because at first I thought it was an issue with the trackpad as the nub pointer stopped working as well and only touchpad works for moving the mouse (which has never happened to me before), but when I plugin in a standard USB mouse it also cant left click.

When I was upgrading the kernel, it ran out of space on /boot/, so before rebooting I removed all old kernels (except for the current running one) and then force reinstalled all the packages for the new kernel. I dont think this contributed to the problem though as it stopped working as it was upgrading either way and trying both kernels doesnt make a difference.

Ive cleared /etc/X11/xorg.conf and put it back in again to what it was before and it didnt help. Im at a loss of what else to try, any ideas would be appreciated.

---

