---
title: "VNC and Dual Screens (nVidia / Xinerama)"
date: 2007-09-15
forum: General Help
---

### Post by cyberfunk on 2007-09-15
After being frustrated by ATI's setup.. I finally broke down and switched to nVidia, and had a much nicer time at getting dual screens to work.  Currently, I have my screens setup as follows:

Xinerama enabled.  In the "nvidia-settings" GUI control panel i have the configuration set as "seperate X screen" for each of the two monitors.  I have my left monitor (a Mitsubishi Diamondtron) so that it's blank space to hold windows (no title/task bar on the top/bottom) and my right screen (a Dell flatscreen) as my main monitor.

They're both running at 1600x1200.  The left screen is X Screen number 1, and the right one is X screen 0.

Now, the problem is this... when I enable desktop sharing.. or try to use a VNC server otherwise... I get on my remote vncviewer a very strange image.  I get a full sized image ( 3200x 1200), but 1/2 of it is dark (black).  The half that is dark is my screen 0 (my right monitor, the Dell) and the half that is visible is my left monitor (screen 1, the Mitsubishi).  Stranger still, when I move my mouse on the LEFT side of the 3200x1200 image, my mouse on the actual computer moves on the RIGHT monitor (the Dell).  When I move my mouse into the dark area of the VNC viewer, nothing happens on the real computer.

In summary then, I can see the left monitor, but only control the right one.  Any idea what's going on?  How do I properly setup VNC so that I can see and control both monitors' worth of screen space?

Thanks in advance,

cyberfunk

---

### Post by Meroigo on 2007-10-05
Bump - because I have the same problem.

---

### Post by bobpaul on 2007-12-18
Same problem, just manifested itself after doing a fresh install of gutsy and using gnome's Screens and Graphics tool to configure dual monitors. In the past I've either carried over a 2 yr old manually configured Xorg.conf from previous installs or simply used the nvidia-glx-settings tool, which appears to be missing from the menus.

By taking a quick look at the xorg.conf I am using, I notice that it's using Xinerama and not nVidia's TwinView. TwinView the Xinerama compliant tool built into nVidia's drivers. I'm rather certain that switching to this and restarting the X session will solve this issue. I'll try it out later.

**Edit:** Yes, switching from Xinerama to TwinView made the difference.

---

