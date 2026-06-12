---
title: "Help with using TV as monitor?"
date: 2018-01-20
forum: General Help
---

### Post by ubunt72 on 2018-01-20
I am using Ubuntu (upgraded 17.04 to 17.10) and my gpu (if it helps to know) is a Nvidia EVGA GTX 750 card - I believe I'm using the proprietary driver.

My 22" monitor died so I am suck with using my 32" Samsung TV as the primary monitor.   The previous settings were as follows:  the 22" monitor was the primary and the Samsung was the secondary.   Of course, the 22" monitor is no longer listed in the Display settings.   Same with the Nvidia settings.   

But, when I look at the Display settings, it lists the display as follows:
Samsung Electric Company 7"
Resolution 1360 x 768 (16:9)

So, the browser window is large, icons are large - the icons going up and down the left margin of the screen - large and the bottom of the browser window often overlaps at the bottom of the screen.  Know what I mean?

I figure this might be a common issue that happens or it's not unheard of - I just don't know what to google or what you would call this - or I would try to search online.

I am concerned that I might have to use the CLI - but, I will if I have to. :)  I am just not familiar with the syntax/commands for X11/xrandr or maybe this has more to do with resetting the resolution?   Is the problem that there is still a 'status' of there being two monitors - or that those settings are configured/in memory?  I am not sure what the deal is so maybe someone recognizes what's going on?   

I think this setting 'Samsung Electric Company 7"' is shown because I was using both monitors simultaneously before but for some reason, 'disconnecting' the other one hasn't resulted in any change with the Samsung display - although, the Gnome settings show just one display and they do list the native resolution.   I am also wondering if the non-standard resolution is also playing a part or causing an issue?

Edit:  Oh btw, I almost forgot to mention - I have another Ubuntu-based OS on another partition (Kubuntu or KDE-installed Ubuntu, I think) and the icons/text is really small there.

---

### Post by TheFu on 2018-01-20
HDMI connections communicate the resolutions supported by the monitor.  So, what resolutions does the TV support?  The manual should say.  Those are the resolutions you should see in any of the xrandr/lxrandr/arandr tools.

Many 37 inch and smaller TVs from a few yrs ago are just 720p screens.

---

### Post by SeijiSensei on 2018-01-21
You haven't told us whether you're using the proprietary driver.  Run the Driver Manager and install what it recommends, probably the nvidia-384 package if you have not already installed it.  That's what drives my GTX 750.  Reboot.

Next, generate an xorg.conf file for your system.  We'll need it in a moment.

```
sudo nvidia-xconfig
```

Next, use the NVIDIA tool in the Accessories section of the program menu to choose the resolution.  

Now let's deal with the tiny font problem.  I have this all the time with NVIDIA cards and televisions.  Edit the file /etc/X11/xorg.conf as root with sudo, e.g., "sudo nano /etc/X11/xorg.conf".  In the stanza called "Screen" add this line
```
    Option         "DPI" "96x96"
```
I usually put it at the bottom of the stanza, just above the "EndSection" directive.  Now, after a reboot, you should be able to read the text on your screen.

---

