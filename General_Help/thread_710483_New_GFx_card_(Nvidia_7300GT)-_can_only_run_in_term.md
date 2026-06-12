---
title: "New GFx card (Nvidia 7300GT)- can only run in terminal mode"
date: 2008-02-28
forum: General Help
---

### Post by greeneggsnsam on 2008-02-28
I've searched around, but I can't find any threads about this already. Point me towards them if there are!

Essentially, after replacing my ATI 9200SE graphics card with an Nvidia 7300 GT, when I boot Ubuntu, it starts to load as normal, and then suddenly switches to terminal mode when the orange bar reaches about halfway. Once a load of text telling me what it's doing (I.e. "Booting blah blah blah" etc) I'm hit with a grey screen telling me there was no monitor found (It says quite a lot more, but none of it makes sense, so I can't remember it). 

After I escape from this screen, I'm left with Ubuntu running in full screen terminal. I've tried using this to install Nvidia drivers, several times, and it says that it's successful, but after rebooting, it does exactly the same thing every time. Can anyone help?

---

### Post by BSAguy on 2008-02-28
Did you uninstall the ATI drivers first?

---

### Post by greeneggsnsam on 2008-02-28
Hmm, I don't think so. I never actually installed any drivers for the ATI card, so would I need to uninstall them anyway?

---

### Post by PinkFloyd102489 on 2008-02-28
Yes, and probably install the Nvidia drivers from the site while you're at it.

---

### Post by Gillingham on 2008-02-28
At a first thought some things to try are, editing the xorg.conf to use the vesa or nv drivers.  vesa being the more basic mode.  This can be found in /etc/X11 directory (you may want to google this a bit).

Another thing is to check what errors are in the logs e.g. via cat /var/log/Xorg.0.log | grep EE  (replace EE with WW to find the warnings).

I had similar sounding troubles with my GEforce 6600 graphics card.  If it is then my solution was to tell the card not to check what the monitor was and to manually give the allowed screen sizes.  My screen section in the xorg.conf file now reads

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV43 [GeForce 6600/GeForce 6600 GT]"
    Monitor        "ACER AL 1715"
    DefaultDepth    24
    Option         "UseEDID" "FALSE"
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024_75" "1024x768" "800x600"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024_75" "1024x768" "800x600"
    EndSubSection
EndSection


I hope this helps

---

### Post by greeneggsnsam on 2008-03-27
Status update:

I tried what Gillingham said, and the EE log said:

> Failed to initialise the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly.

and

> Screen(s) found, but none have a useable configuration.

The WW log said something about a font not existing.

After configuring using the "wizard" thing with "sudo dpkg-reconfigure xserver-xorg", I get this error:

> Failed to open framebuffer device. 

The final error I get on EVERY boot since I've had this problem is 

> no screens found

---

### Post by greeneggsnsam on 2008-03-29
It also said something about the Drivers not having the same firmware as the kernel. What does this mean, and what can I do? Also, how do I go about getting rid of any ATI drivers, if I need to do this? 

EDIT: I fixed the problem by reinstalling completely. :(

---

