---
title: "Low Resolution, Low Graphics Mode, Configuring GPU and Monitor. Help!"
date: 2008-03-08
forum: General Help
---

### Post by archermitch on 2008-03-08
Ok, I'm in some serious trouble with Linux. I'll give you as many details as I can.

I have an Nvidia Geforce 8800GT with a 2..66GHz Intel Core 2 Duo. I built this PC myself and am dual booting Ubuntu 7.10 along with Windows Vista. My first concern is the screen resolution. In the beginning it asks me to configure my monitor and graphics card, but as soon as I log in all changes are gone and it is at 640x800. Extremely harsh condition to work with. I try to reconfigure it, but I need to log in again for it to take effect. This works, but next time I boot up it stops working. I have a Samsung Syncmaster 932BW which doesn't show up in the list of monitors, so I either choose the generic monitor or the Samsung Syncmaster 931. Any suggestions? I've found the remnants of other people who have had the same problem, but none of the solutions work! TIA!

---

### Post by mikewhatever on 2008-03-08
Have you installed nvidia-glx-new, the so called restricted driver for your card?

---

### Post by RadarListener on 2008-03-11
I have the same problem.

I am using the linux driver direct from the nvidia website. I can set up dpkg-reconfigure xserver-xorg fine, and that gives me X on one screen, so then I run nvidia-xconfig which gives me a clone version, and then nvidia-settings to do the dual monitors. Upon reboot however it reverts to low-graphics mode.

---

