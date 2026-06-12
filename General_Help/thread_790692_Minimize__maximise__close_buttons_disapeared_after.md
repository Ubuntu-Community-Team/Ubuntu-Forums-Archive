---
title: "Minimize / maximise / close buttons disapeared after beryl instalation"
date: 2008-05-11
forum: General Help
---

### Post by SilverOne on 2008-05-11
Hi ! 

after installing beryl , my close / maximise and minimze buttons have disapered , i've tried to put them back but i've had no sucess at all ... for 5 times :( 

here's a screenshot: 

[http://www.uploadhouse.com/viewfile.php?id=1833946&PHPSESSID=121c893bd2853d9ea2337af7272aba98](http://www.uploadhouse.com/viewfile.php?id=1833946&PHPSESSID=121c893bd2853d9ea2337af7272aba98)

Can you P L E A S E help me with this ? 

Thank you 
Best Regards

---

### Post by lswest on 2008-05-11
> **SilverOne said:**
> Hi ! 

after installing beryl , my close / maximise and minimze buttons have disapered , i've tried to put them back but i've had no sucess at all ... for 5 times :( 

here's a screenshot: 

[http://www.uploadhouse.com/viewfile.php?id=1833946&PHPSESSID=121c893bd2853d9ea2337af7272aba98](http://www.uploadhouse.com/viewfile.php?id=1833946&PHPSESSID=121c893bd2853d9ea2337af7272aba98)

Can you P L E A S E help me with this ? 

Thank you 
Best Regards
what Ubuntu are you using?  because beryl was replaced by compiz-fusion in 7.10, which comes pre-installed nowadays.  What tutorial did you follow to install it?

unless you removed compiz-fusion, doing ```
compiz --replace
``` should fix your problem, else disable effects with ```
metacity --replace
```

---

### Post by SilverOne on 2008-05-11
> **lswest said:**
> what Ubuntu are you using?  because beryl was replaced by compiz-fusion in 7.10, which comes pre-installed nowadays.  What tutorial did you follow to install it?

unless you removed compiz-fusion, doing ```
compiz --replace
``` should fix your problem, else disable effects with ```
metacity --replace
```

hello, first of all thank you for your awnser ! 

i've tried your steps, and unfortunatly they have not worked. 

Ok, i am a linux n00b, and i downloaded linux like 3 days ago, i believe it's version 8.04 !

the tutorial, i used to install it, was most probably this 1 ;  [http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html](http://www.ubuntugeek.com/how-to-install-beryl-with-latest-nvidia-drivers-in-ubuntu-feisty-fawn.html)

if i right click the beryl icon, and i go Select Window Manager, and i choose Metacity, they become visible again. 

BTW, would it help if i copy pasted my xorg.conf here ? 

Thank you 

Best Regards

---

### Post by lswest on 2008-05-11
well, you've probably done more damage than worth fixing, since Feisty fawn=7.04, whereas Hardy Heron is 8.04, and comes with compiz-fusion pre-installed.  If you don't have much set up yet, i'd suggest re-installing Hardy, and then installing graphics drivers (if you need them) then going to system-->preferences-->appearance and under "visual effects" choosing "normal".  for further customization install compizconfig-settings-manager with ```
sudo apt-get install compizconfig-settings-manager
```.  if you can't easily lose what you have, post back and i'll help you undo what was done.


*edit* i just looked at the tutorial, try removing the packages you installed with ```
sudo apt-get remove [package names]
``` and then removing the lines you added to your sources.list file, and install compiz again (if it's been removed).  Still think a fresh install would be best though.

---

### Post by SilverOne on 2008-05-11
If you say so, i'll chose the reinstall option... since i'm young and i'm really likin this OS. 

no worries... but i'd like a more deep "explanation" what i've done wrong tho, so i avoid doing it in the future, and i learn alitle bit of this...if it wasn't too much trouble ... ofcourse. 

by the way, could you tell me afew hints on how to get symilar specs with compiz-fusion

oh and by the way, my pc has the following specs:

instel 3.6 processor. hyperthreading tech.
2 gb ram
creative x fy ( haven't configured it yet )
asus 7800GTX 256 MB

Best Regards

Thank you.

---

### Post by lswest on 2008-05-11
it's really quite simple.  Beryl (as it was known before Ubuntu Gutsy Gibbons aka 7.10) combined with the compiz project to form compiz-fusion, which comes pre-installed in Ubuntu as of 7.10.  So all the cool beryl effects people have come to know are easily available from compizconfig-settings-manager, i mentioned how to install it above.  So mainly, the problem is that you installed a setup that conflicts with the newer version already in Hardy Heron, and probably ended up overwriting certain required files.  The only thing you need to install for special effects are your graphic card drivers (ATI or nvidia only, intel chipsets are supported pretty much out of the box) and then to install compizconfig-settings-manager, and go to system-->preferences-->advanced desktop effects, and configure what you need.  Hope this is clear enough, feel free to PM me and i can write a more thorough explanation for you.

---

### Post by SilverOne on 2008-05-11
i think it is pretty clean indeed... but i'll double check. 

after reinstallin linux, i will type this in the terminal 
```
sudo apt-get install compizconfig-settings-manager
```

it's getting a little late now, but i'm gonna try to doing it, i'll check by later and tell you my results....

thank you for your opportunity to let me go deeper on ubuntu linux, my first linux experience.

Cya l8ts

Best Regards
Thank You

---

### Post by lswest on 2008-05-11
yup, that's all you need to do (unless you need to install graphics drivers - not sure what chipset asus cards use), but Ubuntu should prompt you for it.  Good luck, and i'm always happy to help,
Lswest

---

### Post by SilverOne on 2008-05-11
Hello ! , i'm back, evreything seems to be running smoothly ! i have done all the steps you've asked and i'm now runing the compiz, oh btw : 

did i told you i run dual screens ? 

i'd like to know if this tuto is OK  : 

[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html) 

also, how do i activate 4 cubes instead of 2 ?

EDIT: i've got 4 cubes now x) 

thank you ! 
Best Regards

---

### Post by lswest on 2008-05-11
> **SilverOne said:**
> Hello ! , i'm back, evreything seems to be running smoothly ! i have done all the steps you've asked and i'm now runing the compiz, oh btw : 

did i told you i run dual screens ? 

i'd like to know if this tuto is OK  : 

[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html) 

also, how do i activate 4 cubes instead of 2 ?

EDIT: i've got 4 cubes now x) 

thank you ! 
Best Regards

looks like the tutorial is fine, if your card is an nvidia card.  Also, there is no restriction on the OS given, so it should work fine. However, you can start where it says > Option &#8220;RenderAccel&#8221; &#8220;true&#8221;. i think. Good luck :)

*edit* might also want to look at this: [http://ubuntuforums.org/showthread.php?p=4873918](http://ubuntuforums.org/showthread.php?p=4873918)

---

### Post by SilverOne on 2008-05-12
hello , i've followed all the steps ... but i still can't get my screens running right ... 
 * 
right now i'm running 800 / 600 and i can't do nothing else... i've tempted to follow all the steps, but when i reach Option &#8220;RenderAccel&#8221; &#8220;true&#8221;.


there's a popup coming before or after login saying "linux is runing low graphics mode " 

then i say configure, and when i put the second screen working... test just fails... 

here's my conf 

```


# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg
Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Boardname	"ASUS 3Dexplorer"
	Busid		"PCI:5:0:0"
	Driver		"glx"
	Screen	0
	Vendorname	"ASUS"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 940T/940B/940Fn(Digital)"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
	Gamma	1.0
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Configured Video Device"
	Monitor		"Configured Monitor"
	Defaultdepth	24
	SubSection "Display"
		Depth	24
		Virtual	1920	1200
		Modes		"1440x900@75"	"1440x900@60"	"1280x800@60"	"1600x1024@60"	"1280x768@75"	"1680x1050@60"	"1280x800@75"	"1920x1200@60"	"1280x720@60"	"1280x768@60"	"800x600@60"	"800x600@75"	"800x600@72"	"800x600@56"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen 0 "Default Screen" 0 0
##This turns on NVidia&#8217;s TwinView
Option &#8220;TwinView&#8221;
##Here I&#8217;m setting the resolution to the individual monitors.
Option &#8220;MetaModes&#8221; &#8220;1400x900 1400×900&#8243;
EndSection
Section "Module"
	Load		"glx"
	Load		"GLcore"
	Load		"v4l"
EndSection
Section "device" # 
	Identifier	"device1"
	Boardname	"ASUS 3Dexplorer"
	Busid		"PCI:5:0:0"
	Driver		"nv"
	Screen	1
	Vendorname	"ASUS"
EndSection
Section "screen" # 
	Identifier	"screen1"
	Device		"device1"
	Defaultdepth	24
	Monitor		"monitor1"
EndSection
Section "monitor" # 
	Identifier	"monitor1"
	Gamma	1.0
EndSection
Section "ServerFlags"
EndSection


```

Best Regards
SilverOne.
Thank you.

---

