---
title: "Edgy only displays on external laptop monitor"
date: 2007-03-19
forum: General Help
---

### Post by m0gely on 2007-03-19
During the install of Edgy (this is my first use of Ubuntu and am also inexperienced with Linux) my laptop screen would go blank after the initial Ubuntu logo appeared.  Connecting a monitor to my external port revealed the setup screens.  In Windows the function keys operate the display properly when using this laptop with presentation software.  This continued after Ubuntu was installed.  A person on a helping me from a Linux mailing list recommended editing the xorg.conf file and changing the display driver from *ati* to *vesa*.  This solved that problem and now it boots Ubuntu on the laptop display.

However now the video performance is poor.  It is clear to me that I am simply using a generic display driver which most likely has no hardware acceleration.  The windows move around in a very choppy manner, though video media seems to display OK.  My laptop is an HP ZE4365.  It has an AMD XP2200, 1GB of mem and an ATI IGP320 video chipset with 128MB of memory allocated to it.  No other modifications have been made.  TIA for the suggestions.

---

