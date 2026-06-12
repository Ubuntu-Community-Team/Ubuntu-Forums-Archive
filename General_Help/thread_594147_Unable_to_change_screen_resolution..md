---
title: "Unable to change screen resolution."
date: 2007-10-27
forum: General Help
---

### Post by Rua on 2007-10-27
I recently installed 7.10 on my Acer Aspire 1350 laptop, and I cannot seem to change the screen resolution to anything other then the default 1024x768. 

A few months ago I had installed 7.04 on this same system, and did not have any problems changing the resolution. I had used the sudo dpkg-reconfigure -phigh xserver-xorg command, picked the resolutions I wanted, and it worked perfectly. However, this time when  I run this command and add the resolutions  I want, it does not allow me to choose anything other then the default 1024x768 even after I restart X server. 

I checked the xorg config file, and it does have the resolutions listed in it. I have included a screenshot of the monitor and screen sections of xorg. [http://radiant.sasktelwebsite.net/xorgscreenshot.jpg](http://radiant.sasktelwebsite.net/xorgscreenshot.jpg)

One thing I can mention that I think was different this time around, is after running sudo dpkg-reconfigure -phigh xserver-xorg it does not give me the option of choosing a driver, it just takes me directly to the portion where it wants me to choose the resolutions. I seem to recall it asking me to first select a driver on my previous 7.04 install. Is the problem then perhaps related to the driver I am using? I am currently using a VIA unicrhrome driver, should I switch that to VESA?

Any help would be appreciated.

---

