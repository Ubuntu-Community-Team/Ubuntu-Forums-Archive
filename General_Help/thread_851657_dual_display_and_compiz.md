---
title: "dual display and compiz"
date: 2008-07-06
forum: General Help
---

### Post by monoufo on 2008-07-06
we all know that compiz sometimes had problems with window borders.  Well I am here to report a variation on that.

1) only the top border (title bar) is missing, bottom and sides are fine.

2) It only happens to some windows, not all like the common problems.  Firefox and nautilus are most affected, but other apps like deluge and VLC are just fine.

3) The problem only happens if I boot the computer with my second monitor connected.  With no second monitor, everything is fine.  I can even connect the second monitor after boot, and it will be fine until it's rebooted with the monitor attached again.  

that last point is really perplexing.

NEW

4) Ignore point 2.  Mystery solved.  It is no longer application dependent.  the problem is maximized windows.  nautilus and firefox are typically viewed maximized, while VLC is usually much smaller or full screen.

---

### Post by boppp on 2008-07-09
Unfortunately i got to say that i got exactly the same problem!

I will reboot in a couple of minutes to test what 'compiz' says when i want to start it manually (cause that doesnt seem to be started in dual monitor mode).

---

### Post by boppp on 2008-07-09
I rebooted with my 2nd monitor in.

When i try to start compiz, it says:
> 
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:71c5 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: 


And keeps hanging there. I think the only real problem here is that compiz is not working (and emerald). I use the ATI restricted drivers and did not change anything particular in my xorg.conf.

Does anyone have any suggestions?

glxinfo hangs on: 
> 
bob@bob-laptop:~$ glxinfo
name of display: :0.1


xorg.conf:
> 
Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
EndSection

Section "Screen"
	Identifier	"aticonfig-Screen[1]"
	Device		"aticonfig-Device[1]"
	Monitor		"aticonfig-Monitor[1]"
	SubSection "Display"
		Viewport	0	0
		Depth	24
	EndSubSection
	Defaultdepth	24
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"PairModes"
	Option		"Mode2"	"1280x800,1680x1050"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
	Busid		"PCI:1:0:0"
EndSection

Section "Device"
	Identifier	"aticonfig-Device[1]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
	Screen	1
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
EndSection


Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen" 0 0
  screen "aticonfig-Screen[1]" rightof "Default Screen"
	Inputdevice	"Synaptics Touchpad"
EndSection

Section "Module"
	Load		"glx"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Monitor"
	Identifier	"aticonfig-Monitor[1]"
	Option		"VendorName"	"ATI Proprietary Driver"
	Option		"ModelName"	"Generic Autodetecting Monitor"
	Option		"DPMS"	"true"
EndSection

Section "Extensions"
	Option		"Composite"	"Enable"
EndSection

ps. i removed the input things from the xorg.conf cause that doesnt matter.

---

### Post by Neo_The_User on 2008-07-09
I have had Ubuntu 7.04 to 8.04.1 with ATi and nVIDIA Graphics cards (RADEON 9800 PRO and 5900XT) with dual monitor setup and I can't get desktop effects installed with latest drivers via Envy or not even having Envy installed and going to the nvidia and ati website and downloading the drivers there. I have xserver-xgl with latest drivers from the ATi website right now. I have ATi Graphics Accelerator running as well with all GNOME updates installed. I tried using Ubuntu 8.10 Intreped and I couldn't even get video working right at all. Please help because I like everything shiny. P.S. I also did sudo compiz in the terminal and it said

neo@neo-desktop:~$ sudo compiz
[sudo] password for neo:
Checking for Xgl: not present.
Detected PCI ID for VGA: 01:00.0 0300: 1002:4e48 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present.
Trying again with indirect rendering:
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: present.
Comparing resolution (2880x900) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity

Thank you.

P.S. Toolbars and everything else work fine.

---

### Post by monoufo on 2008-07-10
> **Neo_The_User said:**
> 
Comparing resolution (2880x900) to maximum 3D texture size (2048): Failed.
aborting and using fallback: /usr/bin/metacity

Thank you.


Your problem is completey different from mine.  My compiz works 99%.  only maximized windows have a problem.  Anyway just look at your error.  Your hardware supports up to 2048 resolution in 3d mode. you are trying to run 2880.  You no doubt are trying to run 2 1440 x 900 monitors side by side. You can't do that with compiz on your hardware. Mine only support up to 1024. So I have to have my LCD in mirror mode at a much lower resolution that it was deseigned for.  When I get a new computer my expensive monitor will be more awesome.

Pick a solution.

1) don't use compiz.
2) Set your moniters to be one on top of the other.  It will take some getting used to, but it should be better than one monitor. that way you have 1440 x 1800 which would fit.

---

### Post by porkchopexpressions on 2008-10-02
I had a similar problem on Ubuntu Studio, and it was solved by the afore-mentioned removal / non-use of Compiz (man, that program does a lot less than it should, especially if your video and display hardware aren't detected correctly).  

A key problem was Emerald crashing or bugging out though, so if you download the compiz-fusion package (it's something like that) in Synaptic, you get a Compiz icon in the notification area.  With a right click, you get a drop down menu to select between emerald or your default window manager, usually metacity or something like that.  Also, certain themes have a setting to hide the menu bar, requiring you to right-click the window you're using and select "view menu bar".  I'm not saying that's your problem, but certain themes (especially non-system ones, like the themes available for download with the GnomeArt app) are buggy and will do strange things.

Keeping away from Emerald and window decoration eye-candy settings flushed out most of the bugs for me, but my dual display still isn't working correctly either.  If anyone has successfully configured a dual-monitor setup with a dedicated video card, complete with desktop effects (with or without using Compiz), I'd love to know how you did it, and what you do to keep it that way (after restarts, unplugging the display, etc.).

---

