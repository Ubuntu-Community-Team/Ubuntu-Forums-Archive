---
title: "Fixing screen resolution for Ubuntu w/ Parallels for windows"
date: 2006-11-04
forum: General Help
---

### Post by ubudave on 2006-11-04
I am running 6.10 with Parallels workstation for windows. My screen  resolution wont go any higher than 1024X768.  I installed Fedora 6.0 and get a screen res of 1900X1200 but no sound and I don't like it as much as Ubuntu anyway.  Any help on this would be great! ohh by the way I have only been using Linux for 2 weeks so I don't know a lot yet.

---

### Post by DonnieP on 2006-11-10
I assume you're talking about the screen resolution in Gnome and not the screen resolution for usplash.  Since it worked for you in Fedora, I further assume you specified your custom resolution in Parallels.  For Ubuntu, then, have you run this command?

sudo dpkg-reconfigure xserver-xorg

If not, then run it and accept defaults (unless you otherwise know what you're doing) and *definitely* allow it to auto-detect monitor and communicate with video driver. Accept the resulting defaults from the auto-detection and communication. It will create the xorg.conf file for you with correct sync/refresh and resolution mode lines.  Getting these sync/refresh numbers right is the key - changing the resolution alone won't get you there.

---

### Post by LorenzoM on 2006-11-14
I asked the Parallels techs about this.  We figured it out that you have to run the command 'gtf h v r -x'   where h is the horizontal scan and v the verticle and r the refresh rate.  I used 'gtf 1680 1050 60 -x' for my macbook. This creates a modeline that you can insert somewhere in the Monitor section of the xorg.conf.

Next change the Screen section so that there is only one Subsection Display. Get rid of all the others. The only one should be for the default depth and it should have only one line for mode that reflects your new res (i.e 1680x1050 in my case). Get rid of all the other modes in that line.   Reboot and done.


Larry

---

### Post by DonnieP on 2006-11-15
Using 'sudo dpkg-reconfigure xserver-xorg' gets you to the same place without having to manually edit xorg.conf (which a two-week Linux user might not be comfortable doing).  And in my set-up at least (with same 1680x1050 res) having the multiple "Display" subsections for non-default depths doesn't seem to affect anything.  But congratulations on getting Parallels to respond to the issue.  That's truly an accomplishment.

---

