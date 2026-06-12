---
title: "slow choppy graphics"
date: 2006-09-10
forum: General Help
---

### Post by danielfretto on 2006-09-10
graphics look pretty choppy overall.  how do i alter graphics settings?

d@shedd:~$ glxgears
X connection to :0.0 broken (explicit kill or server shutdown).

---

### Post by toasterofirony on 2006-09-10
Depends on your graphics card. Tell us which one you have and we can go from there.

---

### Post by danielfretto on 2006-09-11
pretty sure it's nvidia

in windows i can tell you in a second.

with linux i don't know where to look.  

sorry i don't know off the top.

---

### Post by danielfretto on 2006-09-11
here's the card info

0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420 ] (rev a3)

---

### Post by toasterofirony on 2006-09-11
Have you installed the nVidia drivers?

---

### Post by danielfretto on 2006-09-11
yes.

before installing drivers i had only one screen resolution to chose from in dropdown but it was the max.  after installing drivers i have multiple choices in dropdown.

i don't see myself gaming very much with ubuntu...maybe here and there with the kids.  

for normal use the graphics work ok.

should stock screensavers move in such a choppy manner?

---

### Post by toasterofirony on 2006-09-12
humour me, if you type "glxgears -printfps" into the terminal what does it show? If your fps is in the hundreds something is wrong. And what resolution are you using? Given your card isn't especially top-end it might well have trouble doing OpenGL stuff at high resolutions.

---

### Post by danielfretto on 2006-09-12
will apply suggestion this pm.  not at home pc now.
i'm at max resolution though...(maybe 1024 by 12XX) can't remember exactly.
by OpenGl do you mean ubuntu?

---

### Post by toasterofirony on 2006-09-12
No, OpenGl is the system which nice 3-D stuff is rendered in Linux. Such as "GL" screensavers. I'm not sure what to suggest, other that make sure you're running the native resolution of your monitor (if you have an LCD) and make sure you're using the "nvidia" (and not the "nv") display driver in your xorg.conf (found in /etc/X11/xorg.conf)

You should be aware that if you're running anything in the background (say a video encoder or somesuch) your fps will be lower than normal.

I've must say from a first hand account that theres nothing wrong with the way tha Ubuntu handles 3-D rendering, I play WoW under Wine quite happily :)

---

### Post by danielfretto on 2006-09-12
1280 x 1024  SyncMaster 172N

applied your suggestion...i don't see the fps displayed.

installed nvidia drivers thru synaptic.

not sure how to find the files as you suggest.

d@shedd:~$ glxgears -printfps
Usage:
  -display <displayname>  set the display to run on
  -stereo                 run in stereo mode
  -fullscreen             run in fullscreen mode
  -info                   display OpenGL renderer info
d@shedd:~$

---

### Post by toasterofirony on 2006-09-13
okay, heres what we're going to do:

When you installed the nvidia drivers via Synaptic, did you run the command "nvidia-glx-config-enable" afterwards? No? Okay open a terminal now and do it (you may need to do it with sudo, I can't remember). It may tell you that the script cannot be completed automatically, so in the terminal type:

sudo gedit /etc/X11/xorg.conf

scroll through the file until you reach this:

Section "Device"
	Identifier	"NVIDIA Corporation NV31 [GeForce FX 5600]"
	Driver		"nvidia"
	BusID		"PCI:2:0:0"

Obviously, this will not be exactly what you see, but check to see whether is says "nv" or "nvidia" in the Driver line. If you've installed the nvidia drivers, you want "nvidia" there. So change it and save it. And then reboot. If all is well you should see a nvidia splash screen when X starts.

---

### Post by danielfretto on 2006-09-13
here is the terminal script you suggested.  as you see it isn't shown exactly as you described.  below that you'll see the conf text.  i'll apply changes, reboot, and tell you what happened.   unending thanks.

d@shedd:~$ sudo nvidia-glx-config-enable
Password:
sudo: nvidia-glx-config-enable: command not found
d@shedd:~$ sudo gedit /etc/X11/xorg.conf

(gedit:5711): libgnomevfs-WARNING **: Cannot load module `/usr/lib/gnome-vfs-2.0/modules/libcdda.so' (/usr/lib/gnome-vfs-2.0/modules/libcdda.so: cannot open shared object file: No such file or directory)

There was a bunch of other info above this but here is the graphics info to the end.  It does say "nv" not "nvidia" as you can see.


Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 420]"
	Driver		**"nv"**
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 420]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by danielfretto on 2006-09-13
i didn't see a nvidia splash on reboot.

this is that other command you advisedf the second time and it's results"

d@shedd:~$ sudo nvidia-glx-config-enable
sudo: nvidia-glx-config-enable: command not found
d@shedd:~$


after reboot config reads as such:

Section "Device"
	Identifier	"NVIDIA Corporation NV17 [GeForce4 MX 420]"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV17 [GeForce4 MX 420]"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by toasterofirony on 2006-09-13
Sorry, that should read "nvidia-glx-config enable".

---

### Post by danielfretto on 2006-09-13
i may have missed it first time round but nvidia splash is showing now and graphics appear to be much better.

should i still apply the script you sent?

i will be at pc in round 5 hours.

is there a good test for graphics?

---

### Post by toasterofirony on 2006-09-13
Weird.

Try the glxgears thing again. Be aware that glxgears is not a system for benchmarking your system - It's more like licking your finger and holding it up to figure out which way the wind is blowing.

---

### Post by danielfretto on 2006-09-13
d@shedd:~$ glxgears
4861 frames in 5.0 seconds = 972.163 FPS
4831 frames in 5.0 seconds = 966.186 FPS
4880 frames in 5.0 seconds = 975.848 FPS
4851 frames in 5.0 seconds = 970.166 FPS
X connection to :0.0 broken (explicit kill or server shutdown).
d@shedd:~$

---

