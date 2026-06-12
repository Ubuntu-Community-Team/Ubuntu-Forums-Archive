---
title: "KDM logon screen in wrong position"
date: 2006-11-12
forum: General Help
---

### Post by Zill on 2006-11-12
Installation of Kubuntu on a new PC worked fine until I changed the default settings for the graphics card (via System Settings, Display in Administrator Mode) to SIS and the default Monitor to Dell D1025HE.  This was necessary to get a 1024x768 display with a decent refresh rate of 85Hz.  Although KDE now runs OK with good video, when I logout the KDM Logon screen shifts right down to the bottom right corner of the screen and is only partly visible.  This will return to the centre if I restart the X Server but returns back to the bottom right on every logout.
File /etc/kde3/kdm/kdmrc is unchanged from the original default so the "greeter" position should remain centred at 50:50.
If I change the Display setting to "generic" or "plug and play" and restart the X server then the logon screen goes back to centre.  However, then either the refresh rate (60Hz) or the screen resolution (640x480) is too low.
Any ideas how to get both my graphics card (SIS 661) and monitor (Dell D1025HE) configured correctly while still having the logon screen in the centre?

---

### Post by solderhead on 2006-11-19
I am also having a problem with improper physical/virtual desktop resolutions in KDM. I am using Edgy.
 
 The normal bootsplash theme works properly, but when KDM is started, it is initialized at a resolution that is higher than the resolution of the physical screen display. When Xorg/KDE start, everything is normal. This appears to be a problem that is limited to KDM.
 
 When KDM starts, the KDM logon box is displayed (somewhat large) in the middle of the screen. When I wiggle the mouse, the display ends up scrolling all over the place, and the KDM logon box moves about as additional portions of the much larger virtual desktop are passed over the display.
 
 It would appear that KDM is being initialized so that the size of the virtual desktop exceeds the size of the physical desktop. As a result, when you move the mouse, the physical desktop moves about giving you a "porthole" view of the much larger virtual desktop. It appears as if you are scanning the scene with a pair of binoculars.
 
 I also find this to be a bit annoying, and I'd love to find out how to fix the problem. If anyone has a clue, I'd appreciate a point in the right direction. Thanks.

---

### Post by Zill on 2006-11-19
Sounds like it might be related to my problem, although my KDM does not move with mouse movement, only by restarting the X-Server with Ctrl-Alt-Backspace or by changing the resolution with Ctrl-Alt-plus or minus.  My KDM is always correct following a reboot but always shifts following a logout from KDE.
I suspect it is a problem with X, rather than KDM, but would appreciate some advice from you gurus out there :-)  I am using Dapper, not Edgy (yet!).

---

### Post by solderhead on 2006-11-19
I found the error in Edgy:  when the installation built my xorg.conf, it created a totally unnecessary entry that defined a virtual desktop of 1400x1050 even though the max resolution of my monitor is 1024x768.  Here is the offending snippet from /etc/X11/xorg.conf:

```

Section "Screen"
  Identifier "Default Screen"
  Device "Silicon Integrated Systems (SiS) 630/730 PCI/AGP VGA Display Adapter"
  Monitor "A75f"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1400 1050
    modes "1024x768@85" "1024x768@75" "832x624@75" "1024x768@70" "800x600@60" "$
  EndSubSection
EndSection

```

The "virtual 1400 1050" entry is the culprit.  I commented it out and rebooted, and the problem went away.

HTH.

---

### Post by Zill on 2006-11-20
Well spotted - glad it fixed your problem.  My xorg.conf file had a similar entry (virtual 1920 1440).  However, when I commented it out it made no difference - my KDM window still goes to the bottom right-hand corner :-(
Any other ideas from anyone - please???

---

### Post by notandor on 2006-11-23
Greetings

I had the same problem for months and then one morning it started to bug me and I googled for kdm and resolution and found your postings.

I got it working by not just commenting the "Virtual" line but instead replacing the values with my current resolution, that is:

[FONT="Fixedsys"]       SubSection "Display"
#               Virtual   2048 1536
                Virtual   1280 1024
                Depth     24
[/FONT]
I always use resolution of 1280X1024 so this works for me, but problems might occur if you need to change your resos for example with Ctrl+Alt++ and Ctrl+Alt+-. At least for me that doesn't work very well. In case you have a laptop you probably won't need that feature. 

In addition I have to say that if you want to chenge the resolution of the Usplash check following [https://help.ubuntu.com/community/USplashCustomizationHowto]("https://help.ubuntu.com/community/USplashCustomizationHowto")

My first posting ever on a forum, hope this helps!

---

### Post by Zill on 2006-11-26
Success! - that fixed it for me...

  SubSection "Display"
    depth 24
#    virtual 1920 1440
    virtual 1024 768

Now logs in and out like a dream with KDM always in the centre :-)

Many thanks.

---

