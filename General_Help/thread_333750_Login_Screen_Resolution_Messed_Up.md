---
title: "Login Screen Resolution Messed Up"
date: 2007-01-07
forum: General Help
---

### Post by darweth on 2007-01-07
This problem began when I installed kde with sudo aptitude install kde-desktop...  i had various resolution problems there and so on.  KDE has since been removed.

One of the problems that came with a reboot though was the change in Login Screen Resolution.  It is now too big for my monitor.  I have to PAN DOWN to see the settings on the lower left and so on.  The login box is not centered.  This is only with a themed login.  A plain login is fine, but how do I fix my themed?  This is my xorg.conf            Shouldn't be start up at 1024 and be scaled to screen? (that is what I am looking for)  

Section "Screen"
  Identifier "Default Screen"
  Device "NVIDIA Corporation NV17 [GeForce4 MX 420]"
  Monitor "Generic Monitor"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 1280 1024
    modes "1024x768@60" "1152x768@54" "800x600@60" "1280x854" "800x600@56" "1280x960@60" "640x480@60" "1280x1024@60"
  EndSubSection
EndSection

---

### Post by scrooge_74 on 2007-01-07
if you click CTRL+ALT+(PLUS OR MINUS) it should let you use another resolution.

You can always try to reconfigure the Xserver sudo dpkg-reconfigure xserver-xorg

---

### Post by peterLinux on 2007-01-07
First thought:

virtual 1280 1024
modes "1024x768@60"

Your virtual mode is bigger than your effective mode
remove the virtual line and restart X
(CTRL-ALT-BACKSPACE)

Second thought

I had something simular with DELL LCDs, changing them to generic LCD panels 1024x768 @ 60 Hz
solved that problem


KDE is not to blame this is a X config.
I am running UBUNTU and KUBUNTU without problems but had to tweak X manually.

2 cups

Peter

---

