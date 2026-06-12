---
title: "GRUB is graphically glitchy and laggy?"
date: 2016-07-01
forum: General Help
---

### Post by tfriz on 2016-07-01
I just installed Ubuntu alongside Win10. When GRUB boots, first the screen fills with what looks like TV static. Then it very slowly loads the boot menu. I've never seen GRUB be so laggy on other computers I used Ubuntu on. Any ideas for how to fix this? thanks!

---

### Post by oldfred on 2016-07-01
BIOS or UEFI?
And what video card/chip?

Grub now tries to use default driver installed rather and BIOS driver. So may be related to video driver or settings? 
Did you install a proprietary driver?

---

### Post by tfriz on 2016-07-01
UEFI (it says UEFI BIOS when I ender the bios menu), and  its one of those hybrid Intel/Nvidia Quadro K2100M setups. I did install the proprietary drivers, and no luck. My laptop has a very bizarre resolution as well, and I've always had issues with graphics drivers crashing, so there may not be a good fix for this

---

### Post by oldfred on 2016-07-01
It can be the wrong driver or just issues with the video chip you are using is not configured correctly.

Can you set in BIOS which video mode/chip you use?

If using the Intel chip different settings are required.

       sudo apt-get remove --purge nvidia-*
sudo ubuntu-drivers devices
sudo ubuntu-drivers autoinstall 
   #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
xrandr -q
xrandr --q1
#What is installed
dkms status 
    
What version of Ubuntu.
One fixed with newer kernel when using 14.04. Another updated BIOS.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1378744](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1378744)

---

