---
title: "Getting quite a few lockups, freezes, and crashes in Hardy."
date: 2008-07-08
forum: General Help
---

### Post by Opeth on 2008-07-08
I was using Feisty for a while, and I had no problems with it. But then I did a fresh install of Hardy, and I've run into a few problems.

First, it started with Firefox closing every 15 minutes, but I googled some help and found a solution to uninstall a file, and that was fixed.

But now, Nautilus locks up. It seems to happen more often when I am doing something intensive or something, but sooner or later, it will lock up. When I try to open a terminal during this lockup, it never fully loads, and I'm forced to ctrl + alt + backspace and then restart. Programs become unresponsive and/or don't fully load all the way during this. Pidgin also crashes once every few hours, and when it crashes, it usually tells me that a lockup is imminent. 

Another thing is that I can't install the latest Nvidia driver, and I'm forced to use a older driver. 

Any suggestions? 

Hardy 8.04 
AMD dual core 4000+
2GB DDR2 667 
GA-M61P-S3
Nvidia 7600GT

Thanks.

---

### Post by enchesss on 2008-07-08
can you explain more about the driver installation?

have you tried installing proprietary drivers by going

system -> administration -> hardware drivers

and enabling proprietary drivers?

---

### Post by cimdrap on 2008-07-08
i've similar issues..
my cpu is a intel core2quad q6600 with a 8600gt video card!
i installed the nvidia drivers with envyng and the logo appears before the login!
The whole system is instable...it was instable also when i ran it from cd live on XP OS!
I got different errors each time i reboot:
1)it try to load the login screen and the screen becomes black then it appears the login then it becomes black again and then it reboot or shows me the login screen finally.

2)If i success to type my username and password, it loads gnome with several errors....:
     2a)it reboot
     2b)it shows me the screen perfectly, but it's instable, so sometimes it freezes or it's very slow(for example firefox...i ran it from shell and i got the "segmentation fault" error and if i keep trying to run it, it reboot the whole system or it start well, but keeping crashing time to time)
     2c)it shows me an error box: "the session...for less than 10 seconds...look at the xsession-errors" and it says:
/etc/gdm/Xsession: Beginning session setup...
Setting IM through im-switch for locale=it_IT
Start IM through /etc/X11/xinit/xinpunt.d/all_ALL linked to /etc/X11/xinit/xinpunt.d/default
SESSION_MANAGER=local/mionome-desktop:/tmp/.ICE-unix/5725
ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909: (snd_ctl_open_noupdate) Invalid CTL front:0
Shutdown failed or nothing to shut down.
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.background" on line 238 overrides entry on line 192

---

### Post by cimdrap on 2008-07-09
is there someone that can help me?

---

### Post by Opeth on 2008-07-12
I am using the 173.14.09 Nvidia drivers. It seems to happen more and more often now. 

:(

---

