---
title: "Trying to disable Dell Inspiron E1705 screen turning off in 14.04"
date: 2014-09-21
forum: General Help
---

### Post by Mike_Goltsman on 2014-09-21
I am trying to turn my old Inspiron E1705 into a photo frame. One thing a photo frame should do is not turn off the screen after 5 minutes. I got feh to start on boot and suck photos out of a share based on a filelist I built, but it is all for naught 5 min. later when the screen blanks to save power. The only relevant control that I was able to find was the "Dim screen to save power" setting in "Brightness & Lock" section of "System Settings". That is unchecked but did not help. Any suggestions on how to find what might be blanking out my screen and how to turn that off would be helpful.

---

### Post by Dennis N on 2014-09-22
If this is Ubuntu, disable Power Manager and Gnome Screensaver as startup applications so they do not start. If you continue to have screen blanking, install xscreensaver, and set display mode to disabled. This may seem paradoxical, but xscreensaver overrides another system called DPMS which also can cause screen blanking, usually after 10 minutes.

---

### Post by Mike_Goltsman on 2014-09-22
This IS Ubuntu, straight install off 14.04 LTS with hardly any tweaking. Where do I look for "startup applications"? In the "Startup Applications" applet I only have indicator-application-service running - which should not cause this. Should I be looking in additional config files? Look for any specific processes in process list output?

The DPMS seemed to be what was causing it, but I thought installing xscreensaver to override it would be like putting in a bigger stereo instead of fixing the muffler in your car. Sniffing around on the google I found that xset command deals with DPMS settings and further from *'man xset'* that *`xset -dpms`* should disable it. So, I stuck that in the "Startup Application" setting that kicks off the slideshow app and it appears to have stopped the screen blanking.

That still feels like a bit of a hack though - there should be a config file somewhere that specifies the options controlled via *xset *that I would be able to edit and avoid having to enter that command. Any suggestions on where these settings might reside?

---

### Post by Dennis N on 2014-09-22
Type "startup" in the dash search box, and "startup applications" should appear. Uncheck "screensaver". All the startup applications may not displayed. In Ubuntu 12.04, we have to use the command:
```
sudo sed -i 's/NoDisplay=true/NoDisplay=false/g' /etc/xdg/autostart/*.desktop
```
to see all of them. The same might apply to 14.04 (I only have Ubuntu 12.04). If you install xscreensaver, you add it to startup applications in this same dialog.
Nix the suggestion on power manager - that's in Xubuntu and Lubuntu. But there is a simple **Power** dialog in Ubuntu under Settings. Mine is set to "Don't suspend".
I know about xset. There are numerous posts about it on these forums. It may work for you. For some it seems it doesn't.

---

### Post by Mike_Goltsman on 2014-09-23
Ah, there's the hiding place! There is a gnome-screensaver in there, but  fortunately for me it is not started in Unity - only in GNOME3 (as best  I can interpret without learning everything there is to know about this  autostart feature). The xset -dpms appears to work for me. I read  someplace that you need to put up a few seconds sleep before that  command so that X has enough time to gather its wits sufficiently to  react to the command. I went down the rabbit hole of manual Xorg  configuration via xorg.conf.d files, just enough to realize that it  would be more work than it's worth to get it done right. To summarize,  for me (maybe because I boot off SSD) it was sufficient to stick a xset  -dpms in front of the feh activation in the autostart entry I created.  The Power dialog - naturally - is set to Don't suspend, Never and all  that. Did not have to use xscreensaver to bend the system to my will.

Now,  if only I could find a semi-transparent floating clock app... Will  experiment with cairo-clock, might have to tweak the code (oh, noes...).

Thanks much for your help Dennis!

---

