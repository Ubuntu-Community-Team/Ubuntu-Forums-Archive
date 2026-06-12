---
title: "New monitor problem (resolution related)"
date: 2007-08-01
forum: General Help
---

### Post by foug on 2007-08-01
Hey, just bought a new monitor and it was working until I tried installing the drivers to try and make the picture look better. The drivers wouldn't install so I went to #ubuntu for some help. I was told to put in the command "sudo dpkg-reconfigure -phigh xserver-xorg", after that the problems started to occur. My resolution is now stuck at 1024x768. At the log in screen it's correct at 1920x1200, but after logging in it changes. I've tried editing xorg.conf, pressing ESC at the GRUB menu and running the (restore whatever), I tried disabling then enabling my restricted drivers (which fixed a problems of my windows not having any borders, now I just need to get my resolution back to normal) The monitor is a 24" Samsung Widescreen, Model 245BW. In xorg.conf under Monitor, it still says the name of my old Gateway monitor. What should I replace it with and how do I go about finding that out? I'm thinking reinstalling Ubuntu might be the only option, but hopefully not if someone here can help. Thanks in advance!

---

### Post by tylerjroach on 2007-08-01
When I first installed ubuntu it didn't recognize my monitor resolution and it barely readable. I ran the command that you have been told to run and once you get to where it asks all the resolutions to list for the screen resolution app in the preferences panel, get rid off all the asterisks except add an asterisk for the resolution you want. Then when ubuntu loads up it will see that this is the only option and hopefully be in the right resolution. I hope this can help you if this is what you was asking.

---

