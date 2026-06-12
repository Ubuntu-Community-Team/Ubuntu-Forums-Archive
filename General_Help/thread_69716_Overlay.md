---
title: "Overlay"
date: 2005-09-27
forum: General Help
---

### Post by MR.T on 2005-09-27
OK so I've been using ubuntu 5.04 for a months now and I installed the ATI drivers for my radeon 9800pro when I first installed ubuntu.I cant remember what method I used to install the drivers but I do know I have the fglrx driver installed,I have 3d acceleration also.My problem is that when I try and use my tv tuner card with tvtime i get this message in terminal:

Running tvtime 0.9.15.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/taylor/.tvtime/tvtime.xml
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

so I assume I need to enable overlay support?...if so how do I do it?

thanks

---

### Post by serzz on 2005-10-02
Fist type
$sudo gedit /etc/X11/xorg.conf
And then replace Device section with this:

Section "Device"
     Identifier "Device"
     Driver "fglrx"
     Option "UseInternalAGPGART" "yes"
     Option "TVFormat" "PAL-B"
     Option "TVStandard" "VIDEO"
     Option "DesktopSetup" "clone"
     Option "VideoOverlay" "on"
     Option "OpenGLOverlay" "off"
     #Option "OverlayOnCRTC2"
EndSection

---

