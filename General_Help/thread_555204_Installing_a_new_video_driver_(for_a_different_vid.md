---
title: "Installing a new video driver (for a different video card)"
date: 2007-09-19
forum: General Help
---

### Post by Doc.Caliban on 2007-09-19
I have a laptop with two GPUs that I can switch between with a switch.  This is done before powering the system up.

I installed Ubuntu with the lower-powered Intel GPU activated.  I am thinking about using the Nvidia GPU from time to time because I've heard that there are settings in the configuration application for the driver that make it easy to use an external display.

What I would like to know is:

1.  First and foremost, is it actually true that the nVida driver makes it easy to utilize an external display?  If not, then I'm not going to bother with this as the Intel gives me better battery life, and Beryl screams with it.

2.  If I do install the nVidia driver, do I simply do it now, with the Intel activated since I can't boot into X with the Nvidia activated yet?

or

3.  Can I get started (or as far as I need to go) by editing the xorg config and change the video driver to NV?   

Thanks in advance.

-Doc

EDIT:

I guess it might not be quite as easy as #3 due to the BusID for the nVidia possibly not being the same.  Would that make a difference?  I'm going to try it for the hell of it and I'll let you know if #3 works.

Section "Device"
	Identifier	"Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

---

