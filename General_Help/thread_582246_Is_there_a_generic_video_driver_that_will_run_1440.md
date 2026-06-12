---
title: "Is there a generic video driver that will run 1440x900 widescreen"
date: 2007-10-19
forum: General Help
---

### Post by garymansell on 2007-10-19
I have a HP ZD8000 laptop with a knackered X600 gfx chip but it worked ok at 1440x900x24bpp with a non accelerated driver (no DRI) with Ubuntu Feisty.

Is there a low level driver similar to vesa or vga that will run in 1440x900x24bpp that I can use instead of the at one that seems to cause the laptop to crash?

Any help gladly received....

Rgds

Gary

---

### Post by repawn on 2007-10-20
My ancient laptop runs at native 1400x1040 on the standard vesa driver - it picked it up automatically - on other machines I have had to add the resolution to my xorg.conf file.

just open a terminal and enter: sudo gedit /etc/X11/xorg.conf

look for the area where the resolutions are presented and add your resolution in to the list.

example: 
Section "Screen"
	Identifier	"Default Screen"
	Device		"nv"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1400x1050"
	EndSubSection
EndSection

---

### Post by garymansell on 2007-10-21
Thanks for taking the time to reply to my post - I had already put the 1440x900 in my xorg.conf file with the vesa driver but it made no odds - it would still display at a horribly stretched 1024x768.

I have now got round the problem and have proper 1440x900x24bpp using the Radeon driver and turning off the dri acceleration using an option to the module:

Section "Device"
        Identifier      "ATI Technologies Inc M24 1P [Radeon Mobility X600]"
        Driver          "radeon"
        Option          "NoAccel" "off"
        Option          "DMAForXv" "on"
        Option          "DRI" "off"
        BusID           "PCI:1:0:0"
EndSection

This allows my to run my laptop with a knackered ATI X600 gfx chip in a non accelerated mode - no 3D but otherwise fine - god I love Linux, try doing that with Windoze...

Cheers again

Gary

---

### Post by zeller on 2007-11-28
How can I find my xorg.conf file while in recovery mode? All I have is a prompt and I don't know enough yet to run the Os strictly from the command line.

My x600 is crashing my laptop and I can't get into the X Windows manager to change settings.

---

### Post by paul.matthijsse on 2007-11-28
hello, use vi for that. Type:
vi /etc/X11/xorg.conf

when opened, press Insert key to start editing; 
when done, pres Insert key again (cursor left under appears) and type :w (or :w!, I forgot) to write the changes to disk.

---

### Post by danketchpel on 2007-11-29
> **repawn said:**
> My ancient laptop runs at native 1400x1040 on the standard vesa driver - 

I'm trying to get the vesa driver to run in 1400x1050 and it will only run in 1024x768 no matter how much editing I do. It works fine in 1024x768 but I really prefer the higher resolution on my Acer AL2017 20" LCD. I'm running this system at 1400x1050 in twin view when dual booting to Win2K and have been successful in getting another system with a Nvidia card to run higher resolutions in twin view under Feisty.

I've run the config utility, hand edited it, zilch. I have been successful in obtaining other resolutions using the Nvidia cards/drivers but this card was made by 3DLabs (Wildcat VP560) and they don't support Linux directly.

Maybe it's just a limitation of the vesa drivers related to that particular hardware?

Any comments from people who've gotten the vesa driver to operate at higher than 1024 resolution would be much appreciated.

In the end it might easier to just install an Nvidia card.

---

