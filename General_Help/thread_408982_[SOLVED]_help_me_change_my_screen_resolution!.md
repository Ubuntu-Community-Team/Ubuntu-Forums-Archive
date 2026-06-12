---
title: "[SOLVED] help me change my screen resolution!"
date: 2007-04-14
forum: General Help
---

### Post by unebaguettesvp on 2007-04-14
i have a "ATI Radeon 9800PRO 128MB DDR AGP 4X/8X All-In-Wonder Video Card" that worked perfectly with my LCD monitor that was connected by a standard PC cable.

now i want to connect my computer to my 720p projector via component cables. when i tried it out, ubuntu started out in 800x600@60Hz. but that didn't work, so i had to change it to 800x600@56Hz. that works great but now i want a larger resolution!

i don't have the option to select 1280x720@60Hz or even 1920x1080@60Hz under Screen Resolution. My only choices are 800x600@60Hz (doesn't work), 800x600@56Hz, and 640x480@60Hz.

i tried following this guide:
[http://ubuntuforums.org/showthread.php?t=83973&page=9](http://ubuntuforums.org/showthread.php?t=83973&page=9)
but that totally did not work.

here is my relevant xorg.conf data:

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"LCD MONITOR"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R350 NH [Radeon 9800 Pro]"
	Monitor		"LCD MONITOR"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

thanks in advance!

---

### Post by procras on 2007-04-14
My set up is similar to yours.

- 720p projector is a panasonic AE700E. (1280x720 native resolution)
- graphics card is ATI X800XT PE
- using fglrx 8.35.5

I also cannot get the native high resolution with the component video outputs. Only lower resolution modes. ???I am not sure if this is possible ???? This was disappointing as I splashed out on a nice component cable and figured out how to connect this to the graphics card. Reading around for posts about this I saw that some people said that the graphics card driver in WinXP would downscale the resolution when connected via component out to reduce illegal movie copying. I am not sure if fglrx does this also. I no longer run WinXP on this box so I cannot try that to see what happens.

I can get the native resolution from the projection using the VGA (PC) connector. Best result is by setting the aspect to VSCROLL on the projection with the VGA connector outputing 1280x1024, I then scroll the picture up and down to fit the movie or whatever I am watching. I am concerned though that this is not a very good way of connecting to the projector as you have to get your graphics card to change the signal to analog and this has to be then reversed by the projector, a bit like the best way to connect a flat panel to your box. (Remember all those horrible clock and phase adjustments on the early panels, yuck!)

Reading around, some users say that the best result is with a DVI to HDMI dongle and using the HDMI input to the projection. But I have not bothered trying to get the dongle and HDMI cable. If I was to try to improve the image from my projector then that would be the next thing I would try unless I can see some way of getting a good result from the component connectors.

---

### Post by zvacet on 2007-04-14
[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

### Post by procras on 2007-04-15
Just a short note to follow up on this.

I cannot get any resolution higher thatn 525p from the component out (cv)  using fglrx 8.35.5 and my radeon X800XT. I have set the hsync and vrefreash etc in xorg.conf and by using the aticonfig commands in the links above. No informative error messages in /var/log/Xorg.0.log. I get an nice clear 720x480 525p image, xrandr gives the 720x480 as the highest resolution.

I reinstalled winXP and the latest ati drivers and can confirm that the component out will give and nice 1280x720 resolution in winXP. This appearance of this is superior to the 1280x720 I can get with the PC input as would be expected.

Maybe this is a problem with the fglrx driver rather than a configuration problem.

---

### Post by unebaguettesvp on 2007-11-02
i solved this problem by creating a new modeline with one of the many online modeline configuration tools. and then i added the new modeline to the relevant section in the xorg.conf.

---

