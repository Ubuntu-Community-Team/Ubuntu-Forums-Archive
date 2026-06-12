---
title: "Ubuntu 18.04 - nvidia-driver-430 settings not loading on boot from xorg.conf?"
date: 2019-08-27
forum: General Help
---

### Post by nullbio on 2019-08-27
Hi all. 

I've installed a fresh version of Ubuntu 18.04 and  nvidia-driver-430, and I can't figure out how to get my nvidia driver  settings to persist across reboot. I change something in the nvidia driver panel related to my monitor layout, and  then go "Save to Configuration File", and save it to  ```
/etc/X11/xorg.conf
```, and then I reboot, but it doesn't load the changes  from that config file. 

I've also tried putting it in  ```
/etc/X11/xorg.conf.d/xorg.conf
```, ```
etc/X11/Xsession.conf.d/20-nvidia.conf
```,  nothing seems to work. 

Any advice? Thanks.

---

### Post by TheFu on 2019-08-27
I wasn't able to get the nvidia-settings program to save any settings on 16.04 either. You didn't say the specific program, but I suspect it was that one.

The **nvidia-xconfig** tool created a more useful base config file that I moved from my HOME into /etc/X11/xorg.conf.d/nvidia.conf  following the normal xorg.conf format. It has been around since at least the early 1990s.  I had to reboot about 20 times to get everything correct.  Watch the Xorg.0.log file in /var/log/ while troubleshooting.

The manpage for xorg.conf.d explains the order that different locations are checked for valid config files and the required names/patterns for those files to be used.

---

