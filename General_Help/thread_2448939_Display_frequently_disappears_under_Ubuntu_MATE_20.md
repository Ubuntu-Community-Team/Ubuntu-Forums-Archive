---
title: "Display frequently disappears under Ubuntu MATE 20.04"
date: 2020-08-16
forum: General Help
---

### Post by allcoms on 2020-08-16
Today I installed Ubuntu MATE 20.04 on a friends i7 desktop that uses Intel HD 4600 graphics. Every few minutes the whole display (a 1080p HDMI TV) cuts out for a few seconds before re-appearing. It's very annoying, enough to be a showstopper for using 20.04. This machine was previously running an old install of Arch Linux that hadn't been updated in 3+ years but that didn't have this issue so I am presuming its an issue with 20.04's newer kernel and/or xorg drivers.

Things tried so far that have failed to fix this issue:

* Trying different refresh rates
* Using Marco's No Compositor mode
* Trying custom xorg.conf files to use uxa, sna and tearfree modes
* Adding the `i915.enable_psr=0` boot parameter as suggested on [https://wiki.archlinux.org/index.php/intel_graphics#Screen_flickering](https://wiki.archlinux.org/index.php/intel_graphics#Screen_flickering)

I have not yet tried different (older) kernels or Wayland, if Wayland is a usable option for MATE users? I don't like GNOME 3.

Has anyone encountered and solved this issue under 20.04 on similar hardware?

---

### Post by allcoms on 2020-08-17
Here is the xorg log:

[https://paste.ubuntu.com/p/cFMWfbBfh4/](https://paste.ubuntu.com/p/cFMWfbBfh4/)

I can't see any intelfb/i915 errors in dmesg or journalctl. There are some concerning bits in the xorg log tho such as:


> Quirked EDID physical size to 2x1 cm
(II) modeset(0): EDID vendor "OEM", prod id 14080

Which would say to me its not detecting the display properly.

---

### Post by allcoms on 2020-08-17
Fixed it - it was just a case of using the 24 Hz refresh rate under the MATE Displays settings app. Ubuntu defaulted to using 30 Hz which caused frequent display droputs and 25 Hz had similar issues at 1080p whilst 24 Hz is working fine.

---

