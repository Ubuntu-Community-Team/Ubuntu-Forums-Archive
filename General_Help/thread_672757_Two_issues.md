---
title: "Two issues"
date: 2008-01-19
forum: General Help
---

### Post by Cardamar on 2008-01-19
Alright, here's the issue. It's vague, so try to bare with me.

Simply put, I'm running in uberlag mode. Here comes my life story to help you all help me solve this:

A while back, I was using Ubuntu 7.10 on an Nvidia 7300. It ran perfectly. Nice and smooth.
After some time, I got it in my head that I should switch to Vista. So I did. While using Vista, I upgraded to an Nvidia 8500GT. After using Vista for a while and it finally pissing me off enough to uninstall it, I switched back to Ubuntu. Well, now Ubuntu isn't running correctly. For example, the refresh rate on my screen. Before the graphics card switch, I was running at 1440x900 at a refresh rate of 59hz. Now, I'm running at 1440x900 at a refresh rate of 50hz. Naturally, when I saw that, I tried to change my refresh rate. Unfortunately for me, the only two available options are 50 and 51hz. I'm assuming this is what's causing the majority of my graphical issues. One of the more obvious issues is the laggyness of my visual effects. Upon minimizing, un-minimizing, and moving windows, my FPS SEVERELY drops. It goes from nearly 600fps to under 60. Also, when I switch desktops ((using the Desktop Plane)), the image ((the four-squared grid with the arrow in it)) is distorted. I'll attach a screenshot to demonstrate this. Tabs in Firefox are also affected. I'll attach a screenshot of this to help as well. Last but not least, we come to the most annoying problem. Flash. I go to any site that requires flash, it prompts me to install the Flash Plugin. I go through the necessary steps to install the Adobe Flash plugin, restart Firefox, and then re-visit the site. Upon arriving at the page, I'm met again with the prompt to install the Flash Plugin. When I try to install it again, it says that it's already installed. So yes, it IS installed, but no, Firefox does detect it ((at least, that what I'm assuming the problem is)). 

The culprit of these problems? I'm assuming it's the 8500GT, as that's the only part of my computer that has changed since I last ran Ubuntu. Actually, my RAM has also gone from 1gb to 3gb, but I'm doubting that's part of it.

Screenshots: [http://i13.photobucket.com/albums/a271/Zalletook/Screenshot.png](http://i13.photobucket.com/albums/a271/Zalletook/Screenshot.png)
[http://i13.photobucket.com/albums/a271/Zalletook/screenshot1.png](http://i13.photobucket.com/albums/a271/Zalletook/screenshot1.png)

---

### Post by pointone on 2008-01-20
When switching video cards, it probably would be a good idea to reconfigure X.Org by running "sudo dpkg-reconfigure xserver-xorg". Also, are you running with the restricted nvidia driver?

---

### Post by Cardamar on 2008-01-20
Yes, I am using the restricted drivers. Upon attempting to reconfigure X, I got this output. Looks like it couldn't write the config file:

colin@GLaDOS:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for colin:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080119234911
dexconf: error: cannot generate configuration file; 
xserver-xorg/config/monitor/horiz-sync not set.  Aborting.  Reconfigure the X 
server with "dpkg-reconfigure xserver-xorg" to correct this problem.
xserver-xorg postinst warning: error while preparing new Xorg X server
   configuration file in /etc/X11/xorg.conf.dpkg-new; not attempting to
   update existing configuration

---

