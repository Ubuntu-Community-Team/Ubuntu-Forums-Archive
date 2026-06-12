---
title: "Change Screen Resolution"
date: 2004-12-05
forum: General Help
---

### Post by karthik085 on 2004-12-05
When I installed Ubuntu on my laptop, it didn't ask me any questions regarding Screen Resolution. Now, I'm stuck with a 640*480, 60HZ. I wanted 1024*768.

Only one option available was 640*480 at 60HZ in Computer->System Configuration->Screen Resolution.

So, I tried modifying the XF86Config-4 file.  These are the changes I made:
1) Changed all 640*480 in the file to 1024*768
2) Changed 24 of monitor depth to 60 also.

Then, I did the following:
cp /etc/X11/Xf86Config-4 /etc/X11/XF86Config-4.custom
md5sum /etc/X11/XF86Config-4 >/var/lib/xfree86/Xf86Config-5.md4sum
dpkg -reconfigure xserver xfree86

The first two step was fine. At the last step, I got the following error
dpkg: need an action option

Type dpkg --help...
...
optopns marked [*] produce a lot of output - pipe it through less or more

I even tried getting the latest xserver-xfree86 using 
apt-get install xserver-xfree86.

For little more info regarding it, I tried dpkg -l xserver-xfree86
Desire=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpakced/Failerd-config/Half-installed
| /Err?=(none)/Hold/Reinst-required/X=both=problesm (Status, Err: upperbase=bad)
|| / Name              Version                       Description
+++-================================================
ii xserver-xfree8 4/3/0/dfsg-1.6 the XFree86 X server

I also did sudo ddcprobe
vbe: VESA 3.0 detected
oem: NVIDIA
vendoe: NVIDIA Corporation
product: NV17 Board - m17refnz Chip Rev A5
memory: 65536kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x16
mode: 800x600x256
mode: 1024x768x16
mode: 1024x768x256
mode: 320x200x64k
mode: 320x200x16m
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x64k
mode: 1024x768x16m
edidfail

Can someone help me with this?

Karthik

---

### Post by karthik085 on 2004-12-05
I have finally made my resolution to 1024x768.

If you guys have any problem with the screen resolution, these are the ways you guys can try in /etc/X11/XF860

1) Increase the HorizSync and VertRefresh to recommended values from monitors.
I changed mine to 30-95 and 50-180. Increase in the first SubSection "Display", Depth from 1 to 24. Also, in the modes in all Subsections, put the desired resolution first, then followed by others.

2) Comment out the HorizSync and VertRefreshlines. X wil work it out for itself

Also, use Ctrl+Alt+Backspace. This will save you from restarting the pc.
An Example:

Section "Monitor"
	Identifier	"Generic Monitor"
	HorizSync	30-95
	VertRefresh	50-180
	Option		"DPMS"
EndSection
Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34 [GeForce FX 5200]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1600x1200" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection



Other ways I tried without changing the config file:
1) Get the latest version of xfree-xserver and install it.

2) sudo dpkg-reconfigure xfree-xserver.
It will not do the easy probe for the video card and montior but will walk you through a series of steps that will ask you all the nitty gritty details.

3) "I found that if I didn't set it during the installation, I couldn't go above 1024x768. Incidently, use SPACEBAR to select the available resolutions you want NOT the enter key. I had to reinstall twice before I figured that out. Now I can set all the resolutions I selected." Some guy wrote in the forum. It didn't work for me.
But, better to try it out as it will save you enough time.

4) Finally, as anyone would have tried:
Click "Computer"
Click "System Configuration"
Click "Screen Resolution"
Choose the resolution your monitor lists as optimal from the first drop-down list
Choose the accompanying refresh rate from the second drop-down list
Click Apply

Hope the above helps.  
Golden rule: Search in the forum and google. You may not be the first one to have the problem. Ubuntu rocks!!!

Karthik

---

