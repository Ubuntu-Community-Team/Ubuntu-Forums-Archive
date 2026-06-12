---
title: "Unable to start X when no monitor is plugged in at boot"
date: 2013-03-15
forum: General Help
---

### Post by mrAlmond on 2013-03-15
Dear all,

I'm using Xubuntu 12.10 with an Intel mini PC. The video card is Intel HD 4000.
This mini pc has 2 HDMI video outputs. Everything is fine when booting with an HD TV connected, but if I boot without it (HDMI cable disconnected) and then after the boot I connect it I can only get the console login.
The problem is related to this error:

"screen(s) found but none have a usable configuration"

How can I make possible to connect the TV after the boot having X up and running with the latest resolution configured?

Thanks for the support.

mrAlmond

---

### Post by dino99 on 2013-03-15
Whats giving:

sudo service lightdm restart

---

### Post by grahammechanical on 2013-03-15
If the above given command does not work then think about this. When you installed Xubuntu did you put the monitor/TV resolution settings into the installer utility? No. We do not need to do that. Why not? When we load Ubuntu the display server (X) gets the information it needs from the Monitor/TV every time it loads. This is why we can change monitors without needing to install them in Ubuntu. Please read this:

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)

This is the issue that you have to get around. To do that you may need to create a configuration file with the settings for the TV. Regards.

---

### Post by mrAlmond on 2013-03-19
The lightdm restart method works but is not suitable for what I need to do.
In this specific case this mini pc could be connected-disconnected at any time with different TV sets regardless of the model and the timings.
Moreover I've just discovered that if I unplug and then plug the HDMI cable when xorg is correctly up and running I get black screen until I switch manually the VT using ctrl+alt+F2 and then ctrl+alt+F7.
This is a very bad issue.

I'm booting from an SSD so I thought also about a boot too fast but installing gdm instead of lightdm did not solve the problem (I've found this suggestion from another thread).

---

