---
title: "ATI drivers installed; dual monitors?"
date: 2005-11-02
forum: General Help
---

### Post by summersab on 2005-11-02
With the help of several wonderful people on the forums, I successfully installed the following drivers:

fglrx-control
xorg-driver-fglrx
xorg-driver-fglrx-dev

I ran dpkg-reconfigure xserver-xorg and set up my video card (ATI Radeon x600 All in Wonder) as fglrx. It works. No more locking up.

HOWEVER, I had also gotten the ATI Proprietary drivers. I tried to install the .run file (./*.run), but I kept getting told that there were errors in the install (something about adding precompiled modules to the kernel). I tried creating distro-specific packages, but no good. I believe it was the Proprietary setup that game me the ATI Control Center in my K-menu. Perhaps it was the installation of fglrx-control, though. Either way, it is there. It gives me options I want - dual monitors that take advantage of the dual heads on my card, TV tuner, etc (all but input/output which I know is still in development).

To this point, it doesn't seem I have a problem. Well, whenever I try to have a horizontal shared desktop between two monitors using the ATI Control, nothing sticks. I check the option, restart X, and it's back to a cloned monitor setting. How do I make use of this $200 card and do dual monitors with an extended desktop off of this card? Additionally, once I get this beast set up, is it possible to have a different resolution on each monitor? One is a 15" and the other is a 17". Thanks SO much if you can help. This is the last thing I need before I am gonna go all Ubuntu!

---

### Post by beefsprocket on 2005-11-02
Try running aticonfig within a konsole. Read through the options carefully and make sure you have a backup xorg.conf. It may take a few tries to get it, but eventually you'll come up with a config that sticks. Note that ctrl+alt+backspace restarts X without requiring a reboot. 

I take it (according to your packages) that you've run through the howto for the drivers? [http://ubuntuforums.org/showthread.php?p=423589](http://ubuntuforums.org/showthread.php?p=423589). You should have aticonfig installed. If not, the howto is where it's at.

You can definitely have two different sized monitors. Specify the hsync2 and vrefresh2 options. Then in System Settings, choose Display and the Screen dropdown.

---

### Post by locutus42 on 2006-03-01
Look in your /etc/X11/xorg.conf file. you'll want to use one of these settings for the multi-head stuff:

# === Screen Management ===
#    Option "DesktopSetup"               "0x00000200"  #horizontal LCD=primary
#    Option "DesktopSetup"               "0x00000201"  #horizontal LCD=secondary
#    Option "DesktopSetup"               "0x00000300"  #virtical LCD=primary
    Option "DesktopSetup"               "0x00000301"  #virtical LCD=secondary(bottom)
#    Option "DesktopSetup"               "0x00000100"  #clone
#    Option "DesktopSetup"               "0x00000000"  #single
    Option "MonitorLayout"              "LVDS, CRT"  #laptop LCD,  external connector

---

### Post by bluebox on 2006-03-27
Thanks everyone for your input - between this and a couple other threads I got dual-head working on a D600 laptop (with extended dextop). The only problem I can't seem to solve is that the second head is connected to an older KVM and Ubantu seems to think it is a monitor capable of only 256 colors. It is wrong - so how do I force the second head to do a higher color depth?

I'm assuming it is the KVM because I have another Ubantu box hooked to the KVM that was previously hooked directly to the flat-panel on the KVM and it is doing the same thing: it switched to 256-color depth.

I presume this is an easy one - but my brain hurts, eyes are bugging out of head, and can't seem to find my answer.

Thanks in advance for the help!

-Mark

---

### Post by mpancotti on 2006-11-19
Unfortunatly I do not have any answer,and I hope you solved your problems. I'm experiencing the same "clone" problem that you solved in my laptop when I use it connected with two screens. I use aticonfig --dsetup=horizontal but Y always get a clone configuration. The ridicolous is that I was able to have it running yesterday, and Y did not touch the xorg.conf in the meantime. I just used my laptop disconnected. After that I was not able to have back my horizontal configuration. Can you ples tell me which other posts helped you?

Thanks
Marco Pancotti

---

### Post by strabes on 2006-11-19
sudo aticonfig --dtop=horizontal -f --mode2=1600x1200,1280x1024,1152x864,1024x768,800x600

I'm not sure how you get different resolutions on different screens. If someone knows this, please tell me. Beefsproket, why do the horizontal and vertical refresh rates affect this?

---

### Post by Balstromb on 2008-05-03
Thanx Strabes!

I'm not the one who asked the question but it works perfectly with my monitors!

Have a nice day!

---

### Post by userfriendly on 2008-06-17
> **Balstromb said:**
> Thanx Strabes!

I'm not the one who asked the question but it works perfectly with my monitors!

Have a nice day!

what he said. =) great stuff.

---

