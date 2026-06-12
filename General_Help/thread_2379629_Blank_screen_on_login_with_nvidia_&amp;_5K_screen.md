---
title: "Blank screen on login with nvidia &amp; 5K screen"
date: 2017-12-07
forum: General Help
---

### Post by mtruyens on 2017-12-07
Hi all, 


I have installed Ubuntu 17.10 (all latest updates installed), and am using an nvidia 1060 card (tried both 387.34 and 384.90 drivers). 


Connecting my HP Z27Q 5K screen (5120 x 2880 pixels, which internally "fuses" two separate tiles/monitors of 2560 x 2880) works OK, except that I always get a black screen during a reboot or logout when this screen is connected. The only way to proceed is then to reboot, connect some other screen with less pixels, login, disconnect that screen, and reconnect the 5K screen. Logging in after sleep is no problem. 


Also note that many other recent distros (e.g., Mint and Arch) do not present this problem when a recent nvidia driver is installed.


Does anybody know a solution how I can avoid all this hassle? I tried: 
- copying the configuration file (monitors.xml) to ~gdm/.config
- automatic or timed login 
- purging & reinstall gdm / gdm3 / ubuntu-desktop


Attached is a log of a failed reboot & login session with the 5K screen (debugging enabled in /etc/gm3/custom.conf)


Many thanks!


Maarten

---

