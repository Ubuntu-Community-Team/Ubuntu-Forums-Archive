---
title: "Gallium 0.4 on AMD ARUBA"
date: 2014-06-09
forum: General Help
---

### Post by jeremy33 on 2014-06-09
It's been quite a while since I've used Ubuntu and have lost the bit of knowledge I did have. 

I have a fairly new laptop from September 2013 that I've installed Ubuntu 14.04 on which is an HP Pavilion with AMD onboard graphics - Gallium 0.4 on AMD ARUBA. Since the original hard drive died on me and not wanting to spend money on microsofts latest abomination, I decided to have a go at Ubuntu again.

Any video I watch has that bit of grainy look to it, as if the color bit depth is too low and artifacting is present. I can't find any way to change bit depth. Got used to the Windows way of right clicking on the desktop which isn't working here unfortunately. 

What is the procedure for changing video settings such as resolution and color bit depth in Ubuntu? Please be as detailed as possible, this old brain isn't what it used to be :)

---

### Post by grahammechanical on 2014-06-09
A lot has changed in Ubuntu since you last used it. Ubuntu has become even less complicated to use but it means that many of the utilities that were present that might have done what you want are not present.

To start with Ubuntu or rather the Xserver gets the monitor screen resolution from the monitor itself. It reads something stored on the monitor call Extended Display Identification Data (EDID). This is why we do not need to set screen resolutions during installation. The Xserver is already set to the optimum resolution.

There is a Screen Display utility in system settings. The term Gallium 0.4 means that you are using an open source video driver. I find it perfectly adequate but you might want to try a proprietary video driver. You will find the utility to install video drivers in System Settings>Software and Updates>Additional Drivers tab. Allow time for the utility to find the drivers. You need to be connected to the internet.

The installation of a proprietary video driver will also bring in a settings manager for that driver. You can find it by looking in the Dash. It will have an icon in the Applications settings of the Dash. I have no idea what the AMD/ATI settings manager will be called.

Regards.

---

### Post by jeremy33 on 2014-06-09
That has done the trick, thank you very much Graham :)

---

### Post by mörgæs on 2014-06-09
Good, please mark the thread 'solved'.

---

### Post by xdonbaldwin on 2014-06-15
> **grahammechanical said:**
> A lot has changed in Ubuntu since you last used it. Ubuntu has become even less complicated to use but it means that many of the utilities that were present that might have done what you want are not present.

To start with Ubuntu or rather the Xserver gets the monitor screen resolution from the monitor itself. It reads something stored on the monitor call Extended Display Identification Data (EDID). This is why we do not need to set screen resolutions during installation. The Xserver is already set to the optimum resolution.

There is a Screen Display utility in system settings. The term Gallium 0.4 means that you are using an open source video driver. I find it perfectly adequate but you might want to try a proprietary video driver. You will find the utility to install video drivers in System Settings>Software and Updates>Additional Drivers tab. Allow time for the utility to find the drivers. You need to be connected to the internet.

The installation of a proprietary video driver will also bring in a settings manager for that driver. You can find it by looking in the Dash. It will have an icon in the Applications settings of the Dash. I have no idea what the AMD/ATI settings manager will be called.

Regards.

Hi I'm using an HP Pavilion g7 that also has Gallium 0.4 on AMD ARUBA and when I go to the Software & Updates/additional drivers window It shows that I'm using X.OrgXserver -- AMD/ATI display driver wrapper from xserver-xorg-video-ati(open source, tested) but it also gives me two other options

Video driver for AMD graphics accelerators from fglrx (proprietary)
&
Video driver for AMD graphics accelerators from fglrx-updates (proprietary)

What should I be using to 1. get the most out of my graphics card and 2. possibly fix the problem of my laptop not waking from sleep mode?

---

