---
title: "beryl + ati"
date: 2006-09-26
forum: General Help
---

### Post by dcherryholmes on 2006-09-26
I've been looking for guides to install beryl under edgy with my ATI x300.  I have seen the sticky for nvidia, but nothing for ati.  Does anyone know of a link?

---

### Post by Belibem on 2006-09-26
[COLOR="Red"]EDITED: Ignore this post. Post #7 is a more detailed version[/COLOR]


[COLOR="Silver"]just use the default open-source driver.

Make sure your /etc/X11/xorg.conf

has "radeon" as driver in the device section. 

also add this two lines in the same section:
Option    "EnablePageFlip"
Option    "ColorTiling" 

It should look like this:

Section "Device"
	Identifier	"ATI Technologies, Inc. R420 JI [Radeon X800PRO]"
	Driver		"radeon"
	BusID		"PCI:2:0:0"
	Option		"UseFBDev"		"true"

	
	Option    "EnablePageFlip"
	Option    "ColorTiling"
EndSection


Then just add the repositories and install beryl related packages as described here:
[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

In case you have fglrx driver installed I recommend unistalling it[/COLOR]

---

### Post by coincoin on 2006-09-26
No problem with fglrx for me ;) 

+

---

### Post by dcherryholmes on 2006-09-26
Thanks for the replies, but they don't really address my question.  I had Xgl/compiz (Quinn's fork) running fine with fglrx, too.  After switching to edgy I played with Aiglx.  Philosophically I prefer it to Xgl/Compiz for two reasons: 1) it's an extension to X rather than an additional layer, and 2) it works with the open ati driver.  However, after about a week of suffering hard lock ups I've decided to head back over to Xgl/compiz since it worked great for me.  However, I now find that we're midstream in a shift away from compiz towards the new projects, beryl and emerald.  All I really want to know is if there's a repo out there that has the packages for edgy, and a HOWTO since this process seems to change every few minutes or so. ;)

---

### Post by LamestHolio on 2006-09-26
> coincoin  
No problem with fglrx for me
+

Could you elaborate on that setup?  I've got an X850Pro, installed on Edgy, with the latest fglrx driver.  I have been unable to get beryl to run, even after compiling all the cvs for the later 200+ builds.

Please post your xorg.conf, and what packages you used. 

Thanks.

edit, with the default driver, I was stuck at 800x600.  listed as ATI in xconfig.

---

### Post by GazaM on 2006-09-26
I'm having major issues with the open source radeon driver and my x700Pro... it works, but only at 640x480 and with no dri.

---

### Post by Belibem on 2006-09-26
Radeon open source driver, aiglx, and Beryl

The following steps apply for all ATI cards supported by the radeon open source driver. To find out whether your ATI card is supported look here:
[http://dri.freedesktop.org/wiki/ATIRadeon](http://dri.freedesktop.org/wiki/ATIRadeon)
If your ATI card is not supported by the radeon driver consider using fglrx driver and xgl

1) Uninstall fglrx if it is installed (use synaptic or whatever you like)

2)
STEP 1 from [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)


3)
STEP 3 from [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)


4)
Edit the device section in your xorg.conf to be like this
Section "Device"
	Identifier	"{your card model}" [COLOR="Red"]<-do not edit this line in your xorg.conf[/COLOR]
	Driver		"radeon"
    	Option    	"DRI" "true"
    	Option    	"ColorTiling" "on"
    	Option    	"EnablePageFlip" "true"
    	Option    	"AccelMethod" "EXA"
        Option          "XAANoOffscreenPixmaps"
    	Option    	"RenderAccel" "true"
    	#Option    	"AGPMode" "[COLOR="Red"]x[/COLOR]"     [COLOR="Red"]<- x may be 2 or 4 depending on your system[/COLOR]
	Option		"AGPFastWrite" "on" 
EndSection


Note: line for agpmode is disabled  (to enable remove #) because it may cause your xorg to crash. Use it with caution!!!
Note2: instead of "AccelMethod" "EXA" you can use "AccelMethod" "XAA". XAA is seems to bit a bit faster but not as stable.
Note3: for more details about r300 specific options take a look here:
[http://www.xfree86.org/current/radeon.4.html](http://www.xfree86.org/current/radeon.4.html)

5)
STEP 5 from [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)


I get about 80-90fps in tremulous at 1280x1024, full detail and 250-300fps in beryl with this setup. I have an X800.

edited----
Some corrections that may be helpful
1.
> XAA is the default acceleration method that is reportedly stable. EXA, OTOH, is the newer method that is potentially faster, and potentially less stable. This can be verified via $ man radeon. Also, as xsacha explained to me on #beryl, the "**ANoOffscreenPixmaps" option needs to match the acceleration method; if you are using EXA, you will need "EXANoOffscreenPixmaps", and if you are using XAA, you will need "XAANoOffscreenPixmaps". This IIRC, among other things, prevents the white titlebars on maximized windows.

2. acceptable agp modes
> 
Option "AGPMode" "integer"
Set AGP data transfer rate. (used only when DRI is enabled)
1 -- x1 (default)
2 -- x2
4 -- x4
8 -- x8
others -- invalid


---

### Post by vuitton on 2006-09-27
Thank you very much Belibem, it works like a charm :)

---

### Post by coincoin on 2006-09-27
> **LamestHolio said:**
> Could you elaborate on that setup?  I've got an X850Pro, installed on Edgy, with the latest fglrx driver.  I have been unable to get beryl to run, even after compiling all the cvs for the later 200+ builds.

Please post your xorg.conf, and what packages you used. 

Thanks.

edit, with the default driver, I was stuck at 800x600.  listed as ATI in xconfig.

Hello,

My Xorg.conf :
```
Section "Device"
   Identifier  "card0"
   Driver      "fglrx"
   Option       "UseInternalAGPGART" "no"
   Option       "KernelModuleParm" "agplock=0"
   BusID       "PCI:1:0:0"
   Option  "ForceMonitors" "lvds,crt1"
EndSection
```

Packages :
```
ii  beryl                                 0.0.0-0ubuntu1~svn20060926           Compositing window manager, decorator and th
ii  beryl-core                            0.0.0-0ubuntu1~svn20060926           Compositing window manager - Beryl Project
ii  beryl-dev                             0.0.0-0ubuntu1~svn20060926           Development files - Beryl Project
ii  beryl-manager                         0.0.0-0ubuntu1~svn20060926           Simple app to sit in tray and keep beryl goi
ii  beryl-plugins                         0.0.0-0ubuntu1~svn20060926.1         Collection of plugins for Beryl
ii  beryl-plugins-data                    0.0.0-0ubuntu1~svn20060926.1         Plugins data - Beryl Project
ii  beryl-settings                        0.0.0-0ubuntu1~svn20060926           Plugin and configuration tool - Beryl Projec
```

And : [17179608.072000] [fglrx] module loaded - fglrx 8.29.6 [Sep 19 2006] on minor 0


Bye

---

### Post by dcherryholmes on 2006-09-27
Thanks for the tips.  I've only been using it for about 5 minutes, but beryl/emerald seem really nice.  The performance under Aiglx/open drivers doesn't seem as snappy as it did with fglrx, but the closed drivers brought their own set of problems, too, so I think I'll stick with Aiglx for now.

---

### Post by dcherryholmes on 2006-09-27
I set things up initially with the xorg.conf options that Belibem specified.  As I said before, performance was pretty choppy.  I'm getting much smoother performance with the following options:

Section "Device"
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver      "radeon"
	BusID       "PCI:1:0:0"
	Option      "AGPMode" "4"
	Option	    "AGPFastWrite" "true"
	Option	    "EnablePageFlip" "true"
	Option	    "backingstore" "true"
	Option	    "AllowGLXWithComposite" "true"
	Option      "RenderAccel" "true"
	Option      "XAANoOffscreenPixmaps" "true"
        Option      "AGPSize" "32"
        Option      "AccelMethode" "EXA"
        Option      "SubPixelOrder" "NONE"
        Option      "DynamicClocks" "true"
        Option      "bioshotkeys" "true"
EndSection

---

### Post by Belibem on 2006-09-27
In the r300 wiki I ve read that 
Option "AccelMethode" "XAA"
gives slightly better performance but is less stable

Unfortunately AGPmode 4 borks my xorg and I can't resolve the problem :(
Does anyone have a clue about AGPmode leading to a system hang? My bios is already set to agp mode 4 ( x8 )


Can anyone please lead me to the documentation of this option? Is a generic one? I don't see anything about it in the radeon man page.
BusID "PCI:1:0:0"

---

### Post by stu on 2006-09-27
> **Belibem said:**
> Can anyone please lead me to the documentation of this option? Is a generic one? I don't see anything about it in the radeon man page.
BusID "PCI:1:0:0"

Yea, that's a generic option that specifies which hardware address that device section is for. That is supposed to be the ID of the slot for your card. Changing it will keep your Xorg from starting, because it will not be able to find a device section for your card.

---

### Post by stani on 2006-09-27
> **coincoin said:**
> Hello,

My Xorg.conf :
```
Section "Device"
   Identifier  "card0"
   Driver      "fglrx"
   Option       "UseInternalAGPGART" "no"
   Option       "KernelModuleParm" "agplock=0"
   BusID       "PCI:1:0:0"
   Option  "ForceMonitors" "lvds,crt1"
EndSection
```

Packages :
```
ii  beryl                                 0.0.0-0ubuntu1~svn20060926           Compositing window manager, decorator and th
ii  beryl-core                            0.0.0-0ubuntu1~svn20060926           Compositing window manager - Beryl Project
ii  beryl-dev                             0.0.0-0ubuntu1~svn20060926           Development files - Beryl Project
ii  beryl-manager                         0.0.0-0ubuntu1~svn20060926           Simple app to sit in tray and keep beryl goi
ii  beryl-plugins                         0.0.0-0ubuntu1~svn20060926.1         Collection of plugins for Beryl
ii  beryl-plugins-data                    0.0.0-0ubuntu1~svn20060926.1         Plugins data - Beryl Project
ii  beryl-settings                        0.0.0-0ubuntu1~svn20060926           Plugin and configuration tool - Beryl Projec
```

And : [17179608.072000] [fglrx] module loaded - fglrx 8.29.6 [Sep 19 2006] on minor 0


Bye

I am on Edgy Kubuntu using the fglrx driver with a Radeon X1300 512mb. I can load the Beryl manager. However when I select Beryl as window manager I get this:
```
** (beryl-manager:24299): WARNING **: Couldn't find a Selection Owner, perhaps no WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Falling back to looking for a defined WM in xlsclients.
Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.
Dkwin: Fatal IO error: client killed
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

```
Does someone has any idea? I have composite disabled in xorg.conf, because otherwise I get the mesa driver for opengl. Also I didn't add this to Screen in xorg.conf or should I?
```
    Option "AddARGBGLXVisuals" "True"
    Option "DisableGLXRootClipping" "True"
```

Thanks in advance,

Stani

---

### Post by Belibem on 2006-09-27
AFAIK fglrx driver does not support aiglx yet and unfortunatelly your card is not supported by the open source driver. Maybe you should try xgl instead.

---

### Post by lupine_nickt on 2006-09-27
Hello my ATi friends :). 

I've just spent the last 2 hours helping another ATi bod get Edgy + Xgl + Beryl + fglrx working. In the end, it's surprisingly easy...

1. Install xserver-xgl and set up a session as usual (lots of ways to do this!)
2. Install beryl from the unofficial repos - you can elect not to install the linux-restricted-modules update if you prefer, but installing it doesn't do any harm. The xorg-sched-hack-<whatever> package wasn't installed, so I don't know whether it does harm or good.
3. Do everything listed in "method 1" from [here](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)
4. Load into your Xgl session and run beryl-manager - add to your session startup as appropriate.

In the end we got 670fps out of beryl so it was well worth the hassle ;)

xF,

...Nick

---

### Post by mwaddoups on 2006-09-28
I followed your tutorial, lupine_nickt, and I now have much faster beryl with my X800 then I did previously with the "radeon" open source driver. However, when using xserver-xgl the theme is different from the theme when using normal gnome, and looks a lot uglier overall. Is there a way to correct this, as Preferences --> Themes does not seem to have any effect on xserver-xgl. Could this be because I run XGL as a separate session to my usual gnome desktop? Or a different reason? Any ideas welcome!

Thanks,
Mark

---

### Post by stani on 2006-09-28
> **mwaddoups said:**
> I followed your tutorial, lupine_nickt, and I now have much faster beryl with my X800 then I did previously with the "radeon" open source driver. However, when using xserver-xgl the theme is different from the theme when using normal gnome, and looks a lot uglier overall. Is there a way to correct this, as Preferences --> Themes does not seem to have any effect on xserver-xgl. Could this be because I run XGL as a separate session to my usual gnome desktop? Or a different reason? Any ideas welcome!

Thanks,
Mark

What do you mean with a theme? The style is defined by gnome/kde, but the window decorations use emerald. Right click on the tray icon and select the "emerald theme manager". The window decorations are different from gnome and have special features.

---

### Post by mwaddoups on 2006-09-28
I meant the theme as in the gnome-panel looks off-grey instead of white, and the icons are the default icons. These are not changeable via Preferences-->Theme like they are normally. However, I have solved this problem by not running XGL as a separate session, which seems to have stopped random crashes I was having as well. Thanks for the help anyway.

---

### Post by max_dingemans on 2006-09-28
> **mwaddoups said:**
>  However, I have solved this problem by not running XGL as a separate session, which seems to have stopped random crashes I was having as well.

I'm curious as to how you did that? I seem to have the same problem you did.

---

### Post by mwaddoups on 2006-09-28
I followed this process, taken from [Beryl Forums - ATI and Compiz]("http://forum.beryl-project.org/topic-389-howto-compiz-gnome")

1. ```
sudo gedit /etc/gdm/gdm.conf-custom
```
Scroll to the bottom and under "[Servers]" put 
```
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true
```
Save and exit

2. ```
sudo gedit /etc/gdm/gdm.conf-custom
```
Use find to find "0=Standard" and replace that section to look like this:
```
#0=Standard
1=Standard
```
Use find again to find "GdmXServerTimeout" and change this value to 50.
Save and exit.

3. Reboot the PC and login to a normal gnome session. This fixed it for me, as it kept the theme I had before I installed XGL. I hope this works for you.

Mark

---

### Post by max_dingemans on 2006-09-28
Unfortunately Xgl crashes after I tried that. But eventually gdm comes back, and I can log in completely normally (standard gnome session).Thanks for the link though.

---

### Post by ironslave on 2006-09-28
ok i have beryl up and running on my ATI radeon 9200 mobility on the open source drivers i am having a couple of issues.... i know it's been addressed but my video card is supported

heres the setup of my xorg.conf

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
Option "DRI" "true"
#Option "XAANoOffscreenPixmaps"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
#Option "SubPixelOrder" "RGB"
Option "AccelMethod" "EXA"
Option "RenderAccel" "true"
#Option "AGPMode" "2"
Option "AGPFastWrite" "on" 
Option "EnablePageFlip"
Option "ColorTiling"
EndSection
```

and heres the error from beryl

```
** (beryl-manager:5706): WARNING **: Couldn't find a Selection Owner, perhaps no WM running?
Otherwise, manually kill your wm, and report the bug to the developers, it doesn't follow the standards.
Falling back to looking for a defined WM in xlsclients.
Window manager warning: Lost connection to the display ':0.0';
```

that happens whenever i try to apply setting in beryl or emerald.
i just reload beryl and change to that desktop.... but now the window decorations only work on the terminal!!!!

also when i first load the beryl-manager it gives me this

```
 Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
Couldn't load settings.  Reverting to defaults.
XGL Absent, checking for NVIDIA
libGL warning: 3D driver claims to not support visual 0x4b
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x4b
Initiating splash

```

and one more thing.... the beryl desktop only runs in 1024X768 and i a would like to be able to use 1280X800 any ideas?](*,)

---

### Post by ironslave on 2006-09-28
ohh... its civing me a crash when it attempts to detatch itself from a handler... not just in the setting manager 
like so: (gdb) Detaching from program: /usr/bin/beryl,(random process number)

also it keeps giving me the error: cant load settings revertting to default when i load some things....

---

### Post by rekahsoft on 2006-09-28
wow...just for clarification...are you guys saying that i don;t need fglrx to have some nice eye candy...does the opensource driver support direct rendering now? Why do i not need fglrx...am i using xgl when i install beryl...or is i using AIGLX? what does beryl do exactly, and what advantages does it have over compiz? I have a Radeon 200M Xpress which has had broken fglrx drivers for quit some time...sometimes the drivers work and sometimes they don't (most often they don't)...so basicly i am amazed to see that i can get some sexy eye candy without crappy fglrx??? correct me if i am wrong :) ;) :)

---

### Post by Tails on 2006-09-28
> **rekahsoft said:**
> wow...just for clarification...are you guys saying that i don;t need fglrx to have some nice eye candy...does the opensource driver support direct rendering now? Why do i not need fglrx...am i using xgl when i install beryl...or is i using AIGLX? what does beryl do exactly, and what advantages does it have over compiz? I have a Radeon 200M Xpress which has had broken fglrx drivers for quit some time...sometimes the drivers work and sometimes they don't (most often they don't)...so basicly i am amazed to see that i can get some sexy eye candy without crappy fglrx??? correct me if i am wrong :) ;) :)

well, I am using 200M also, I ahvent had much luck with those DRI (open-source driver)in the past few weeks of edgy, I just did my clean install of beta now, and will try again later.. :P

---

### Post by rekahsoft on 2006-09-28
> **Tails said:**
> well, I am using 200M also, I ahvent had much luck with those DRI (open-source driver)in the past few weeks of edgy, I just did my clean install of beta now, and will try again later.. :PSo the question is, does the open source ATI drivers support DRI with Radeon 200M cards??? Anybody got the answer for that one?

---

### Post by Tails on 2006-09-28
well, the answer is most likely no... :P

> 
tails@aptop:~$ cat /var/log/Xorg.0.log | grep DRI
(II) Loading extension XFree86-DRI
(WW) RADEON(0): Option "DRI" is not used
(EE) AIGLX: Screen 0 is not DRI capable


Here is my device part of xorg.conf

> 
Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Xpress 200M (RS480)"
        Driver          "radeon"
        BusID           "PCI:1:5:0"
        Option "DRI" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "EnablePageFlip" "true"
Option "backingstore" "true"
Option "AllowGLXWithComposite" "true"
Option "RenderAccel" "true"
Option "XAANoOffscreenPixmaps" "true"
Option "AGPSize" "32"
Option "AccelMethode" "XAA"
Option "SubPixelOrder" "NONE"
Option "DynamicClocks" "true"
Option "bioshotkeys" "true"
EndSection



o, well, off back and wait for ATI to support the aiglx.. >_>

---

### Post by rekahsoft on 2006-09-28
aw...:'( seriously there is no way? i can't even get fglrx to work...so is that it..i have to wait again? i have been waiting for months for the crappy ATI propriatary drivers to be fixed for the Radeon 200M...

---

### Post by stani on 2006-09-29
> **rekahsoft said:**
> aw...:'( seriously there is no way? i can't even get fglrx to work...so is that it..i have to wait again? i have been waiting for months for the crappy ATI propriatary drivers to be fixed for the Radeon 200M...

Maybe you know all this, but these are some checkpoints:

- did you disable composite in xorg.conf, otherwise fglrx will never work, look at my xorg.conf in the end

- you could compare my device settings to yours (FYI I have an ATI X1300) I don't now if the option "TripleBuffer" is necessary, but if you don't have a lot of memory on your card, turn it off.


With this configuration and some scripts to initialize a separate Xgl session (I still can login under normal KDE), I am running full speed beryl. It never crashes (at least during the last two days) and I can watch smooth animated movies on rotating cubes.I am surprised how stable it is already and I know use it as my default desktop.

```

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection
#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "ServerLayout"

#	InputDevice     "stylus" "SendCoreEvents"
#	InputDevice     "cursor" "SendCoreEvents"
#	InputDevice     "eraser" "SendCoreEvents"
	Identifier     "Default Layout"
	Screen         "Default Screen" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
	Option	    "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
EndSection

Section "Monitor"
	Identifier   "Generic Monitor"
	HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 160.0
	Option	    "DPMS"
EndSection

Section "Device"
	Identifier  "ATI RADEON 1300"
	Driver      "fglrx"
	Option	    "UseInternalAGPGART" "no"
	Option	    "KernelModuleParm" "agplock=0"
	Option	    "ForceMonitors" "lvds,crt1"
	Option	    "TripleBuffer" "true"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
	BusID       "PCI:1:0:0"
EndSection

Section "Screen"

	Identifier "Default Screen"
	Device     "ATI RADEON 1300"
	Monitor    "Generic Monitor"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "Composite" "disable"
EndSection

```

---

### Post by Tails on 2006-09-29
well, I got the fglrx working now....... finally....

what u have to do is to remove everything thats related fglrx (Including linux-restricted-modules)  <--- thats important...

then reinstall the ATI driver should get it works... :P

@stani, how do u install beryl + XGL?? because I couldnt find any beryl package with XGL......

---

### Post by anodizer on 2006-09-29
One quick question, does AIGLX works using fglrx with non X-series radeon, or it has problems with every radeon?

---

### Post by Tails on 2006-09-29
> **anodizer said:**
> One quick question, does AIGLX works using fglrx with non X-series radeon, or it has problems with every radeon?

aiglx doesnt work on any fglrx atm, if you got the radeon driver with DRI working, u can use aiglx....

it is just thta radeon dun work on 200M cards.. :P

> 
*There is no 3D for Xpress 200M Northbridge integrated gpus due to undisclosed memory initialisation (july 2006).*


from [http://dri.freedesktop.org/wiki/ATIRadeon](http://dri.freedesktop.org/wiki/ATIRadeon)

---

### Post by Tails on 2006-09-29
haha... Mission Accomplished..   XGL + beryl + fglrx.. :P

following the steps in here... [http://forum.beryl-project.org/topic-389-howto-compiz-gnome](http://forum.beryl-project.org/topic-389-howto-compiz-gnome)
but dun install cgwd and cgwd-themes

then install all the beryl stuffs in here...
[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)


add the beryl-manager to the gnome-session, reboot.... and you are done.. :D

---

### Post by lzfy on 2006-09-29
> 4)
Edit the device section in your xorg.conf to be like this
Section "Device"
Identifier "{your card model}" <-do not edit this line in your xorg.conf
Driver "radeon"
Option "DRI" "true"
#Option "XAANoOffscreenPixmaps"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
#Option "SubPixelOrder" "RGB"
Option "AccelMethod" "EXA"
Option "RenderAccel" "true"
#Option "AGPMode" "2"
Option "AGPFastWrite" "on"
EndSection

I have a PCI express card, do I still have to include the AGP lines? I tried it without but beryl crashes after a minute.

My card is a mobility Radeon x700.

---

### Post by lzfy on 2006-09-29
Ok another question. Can I use fglrx/Beryl/XGL with Edgy? Would that be easier?

thanks...

---

### Post by Tails on 2006-09-29
> **lzfy said:**
> Ok another question. Can I use fglrx/Beryl/XGL with Edgy? Would that be easier?

thanks...

read the post "just" above your last post.... :P

---

### Post by rekahsoft on 2006-09-29
ok...so i can not use the opensource drivers with Radeon 200M Cards...Tails how did you manage to get fglrx working...i can't install fglrx or beryl until i have fglrx working...i have tried everything i have found on the forums and am making a fresh install of edgy beta 1 today and was hoping to get fglrx working...help would be very very much apricaited !! :)

---

### Post by Tails on 2006-09-29
> **rekahsoft said:**
> ok...so i can not use the opensource drivers with Radeon 200M Cards...Tails how did you manage to get fglrx working...i can't install fglrx or beryl until i have fglrx working...i have tried everything i have found on the forums and am making a fresh install of edgy beta 1 today and was hoping to get fglrx working...help would be very very much apricaited !! :)

ok, here is what i did to get fglrx working...

Open up the Synaptics...

find "fglrx", remove.. fglrx*,  xorg-driver-fglrx*
then 
find "linux-restricted-modules" and remove linux-restricted-modules*      <----- yes, u have to remove this..

restore the "default" xorg.conf
and make sure the device section is using ati driver and NOT fglrx

restart the computer

and then follow this how-to...
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

then the fglrx should be working.. :D

---

### Post by anodizer on 2006-09-29
I managed to get Xgl and beryl, but everything is crappy now :/ An ugly GTK theme is used, which I can't even change it! (or the icon theme..)
Any help?

Here's a screenshot:

[img]http://img.photobucket.com/albums/v384/klaount/Screenshot-1.png[/img]

---

### Post by DSn0wMan on 2006-09-29
Beryl seems to be working, but I get the following errors when I start beryl-manager

josh@l33t-mobile:~$ libGL warning: 3D driver claims to not support visual 0x4b

(beryl-manager:4888): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
XGL Absent, checking for NVIDIA
libGL warning: 3D driver claims to not support visual 0x4b
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x4b

(emerald:4952): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.
Initiating splash
beryl: water: GL_ARB_fragment_program is missing
X connection to :0.0 broken (explicit kill or server shutdown).
XGL Absent, checking for NVIDIA
libGL warning: 3D driver claims to not support visual 0x4b
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x4b
Initiating splash
beryl: water: GL_ARB_fragment_program is missing

Any ideas?

Also, it would be nice to create a session separate from gnome that you can select from the login screen.

---

### Post by Tails on 2006-09-29
> **DSn0wMan said:**
> Beryl seems to be working, but I get the following errors when I start beryl-manager

josh@l33t-mobile:~$ libGL warning: 3D driver claims to not support visual 0x4b

(beryl-manager:4888): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
XGL Absent, checking for NVIDIA
libGL warning: 3D driver claims to not support visual 0x4b
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x4b

(emerald:4952): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
Couldn't load settings.  Reverting to defaults.
Couldn't load theme.  Reverting to defaults.
Initiating splash
beryl: water: GL_ARB_fragment_program is missing
X connection to :0.0 broken (explicit kill or server shutdown).
XGL Absent, checking for NVIDIA
libGL warning: 3D driver claims to not support visual 0x4b
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x4b
Initiating splash
beryl: water: GL_ARB_fragment_program is missing

Any ideas?

Also, it would be nice to create a session separate from gnome that you can select from the login screen.

seems like u using NVIDIA card??? if so.... go to this thread instead... [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Also, as for the seperate session, If you are using XGL then read this thread... :P
[http://ubuntuforums.org/showthread.php?t=267938](http://ubuntuforums.org/showthread.php?t=267938)

---

### Post by lzfy on 2006-09-29
So if I'm right this howto will allow you to use Beryl/Xgl/fglrx in a seperate KDE session.

Add one of these repos in "system>admin>software sources" or /etc/apt/sources.list

> deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy
deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy


For the latest beryl.

Run one of these commands to add Quinn's key.

> wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
wget [http://media.blutkind.org/xgl/quinn.key.asc](http://media.blutkind.org/xgl/quinn.key.asc) -O - | sudo apt-key add -
wget [http://compiz-mirror.lupine.me.uk/quinn.key.asc](http://compiz-mirror.lupine.me.uk/quinn.key.asc) -O - | sudo apt-key add -
wget [http://ubuntu.compiz.net/quinn.key.asc](http://ubuntu.compiz.net/quinn.key.asc) -O - | sudo apt-key add -


Creating a seperate Xgl session
> kdesu kate /usr/share/xsessions/xgl.desktop

Paste this command
> [Desktop Entry]
   Encoding=UTF-8
   Name=XGL
   Exec=/usr/bin/startxgl.sh
   Exec=compiz --replace decoration wobbly fade switcher minimize cube rotate zoom scale move resize place gnome-window-decorator &xmodmap -e "keycode 22 = BackSpace" &
   GenericName[en_US]=
   Icon=
   Type=Application

Make executable
> sudo chmod 755 /usr/share/xsessions/xgl.desktop

Start Xgl script
> kdesu kate /usr/bin/startxgl.sh

Paste this command
> Xgl :1 -fullscreen -ac -accel xv -accel glx:pbuffer &
DISPLAY=:1
exec startkde

Make executable
> sudo chmod 755 /usr/bin/startxgl.sh

Compiz script
> kdesu kate /usr/bin/startcompiz

Paste this command
> #!/bin/bash
killall kwin
wait
cgwd --replace gnome-window-decorator &
#gnome-window-decorator &
compiz gconf decoration fade dock widget miniwin minimize cube rotate zoom scale move resize place menu switcher &
xprop -root -f _XKB_RULES_NAMES 8s -set _XKB_RULES_NAMES xorg && setxkbmap -model pc105 -layout it -variant basic

Make executable
> sudo chmod 755 /usr/bin/startcompiz

Autostart
> sudo ln -s /usr/bin/startcompiz /home/username/.kde/Autostart/startcompiz

---

### Post by lzfy on 2006-09-29
I will try this now, anything that I should change?

---

### Post by DSn0wMan on 2006-09-29
> **Tails said:**
> seems like u using NVIDIA card??? if so.... go to this thread instead... [http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Also, as for the seperate session, If you are using XGL then read this thread... :P
[http://ubuntuforums.org/showthread.php?t=267938](http://ubuntuforums.org/showthread.php?t=267938)

Actually I am using ATI with the settings you recommended. I dont have XGL installed.

here is my xorg.conf:

Section "Device"
	Identifier	"ATI Technologies, Inc. M22 [Radeon Mobility M300]"
	Driver "radeon"
	Option "DRI" "true"
	#Option "XAANoOffscreenPixmaps"
	Option "ColorTiling" "on"
	Option "EnablePageFlip" "true"
	#Option "SubPixelOrder" "RGB"
	Option "AccelMethod" "EXA"
	Option "RenderAccel" "true"
	#Option "AGPMode" "2"
	Option "AGPFastWrite" "on" 
	BusID		"PCI:1:0:0"
	VideoRam	128000
EndSection

I found one other thing, the window sizes seem to get to big, and on a couple of occasions maximize button crashes my session.

---

### Post by stani on 2006-09-29
> **lzfy said:**
> So if I'm right this howto will allow you to use Beryl/Xgl/fglrx in a seperate KDE session.

Add one of these repos in "system>admin>software sources" or /etc/apt/sources.list



For the latest beryl.

Run one of these commands to add Quinn's key.



Creating a seperate Xgl session


Paste this command


Make executable


Start Xgl script


Paste this command


Make executable


Compiz script


Paste this command


Make executable


Autostart

Hmmm... zo heb ik het niet gedaan, want:
cgwd is nu emerald
compiz is nu beryl

---

### Post by lzfy on 2006-09-29
> Hmmm... zo heb ik het niet gedaan, want:
 cgwd is nu emerald
 compiz is nu beryl

Klopt, er moeten een aantal commands gewijzigd worden maar weet niet welke :) zou je de commands willen posten die je hebt gebruikt?

---

### Post by jocko on 2006-09-29
> **stani said:**
> Hmmm... zo heb ik het niet gedaan, want:
cgwd is nu emerald
compiz is nu beryl

Well, I think people can guess what you mean in this particular case, but don't you think it would be easier for most of us if you tried to write in **english** instead of... (dutch?)

---

### Post by Nonno Bassotto on 2006-09-29
The section "Device" in my xorg looks like
```

Section "Device"
	Identifier	"ATI Technologies, Inc. M9+ 5C61 [Radeon Mobility 9000 (AGP)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

```
I'm not using the proprietary driver, I'm just using the default driver with Ubuntu, but instead of "radeon" I have "ati". What does this mean? 3D acceleration works fine on my pc, so I always assumed the open driver supported my video card.

---

### Post by DSn0wMan on 2006-09-29
> **Nonno Bassotto said:**
> The section "Device" in my xorg looks like
```

Section "Device"
	Identifier	"ATI Technologies, Inc. M9+ 5C61 [Radeon Mobility 9000 (AGP)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

```
I'm not using the proprietary driver, I'm just using the default driver with Ubuntu, but instead of "radeon" I have "ati". What does this mean? 3D acceleration works fine on my pc, so I always assumed the open driver supported my video card.


I am not sure what the difference between "radeon" and "ati" driver are, but both seem to work well for me without installing anything extra.

---

### Post by Tails on 2006-09-30
> **Nonno Bassotto said:**
> The section "Device" in my xorg looks like
```

Section "Device"
	Identifier	"ATI Technologies, Inc. M9+ 5C61 [Radeon Mobility 9000 (AGP)]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

```
I'm not using the proprietary driver, I'm just using the default driver with Ubuntu, but instead of "radeon" I have "ati". What does this mean? 3D acceleration works fine on my pc, so I always assumed the open driver supported my video card.

yes it does, if you can get DRI working from open-source driver then, you are good to go already to install beryl + aiglx.... but there are some people still don't have DRI support in the open-source driver, i.e 200M... then those people will have no choice at the moment but to install fglrx and use XGL instead.. :P

---

### Post by afterxleep on 2006-09-30
I have a real crappy card, which is the Radeon IGP 320M known also as mobility U1.  I got Direct rendering out of the box on edgy and dapper using the open source radeon driver.  (There is no support on fglrx for this card).  It is slow, but works.

In case anyone might want to try as there are many around with this old cards running, I did this:

**Step 1.  Add repos**

```
$gksudo gedit /etc/apt/apt.conf
```

Add this repositories to the file.
```

deb [http://dev.realistanew.com/beryl](http://dev.realistanew.com/beryl) edgy beryl
deb [http://beryl-mirror.lupine.me.uk/beryl](http://beryl-mirror.lupine.me.uk/beryl) edgy main-edgy aiglx-edgy stable-edg
```

[B]
Step 2. Update, and install[/B]

```
$sudo aptitude update
$sudo aptitude dist-upgrade
$sudo aptitude install beryl-core beryl-plugins beryl-plugins-data emerald beryl-settings beryl-manager beryl beryl-dev emerald-themes
```


**Step 3. Add beryl-manager to gnome session**

Go to System > Preferences > Sessions > Startup Programs.  

Add this to start beryl after login

```
/usr/bin/beryl-manager
```


**Step 4.  Restart gdm**

```
$sudo /etc/init.d/gdm restart
```


At this point you should have it working.  Altough for me, performance was really bad, so I had to tweak the xorg.conf a little bit starting from recommendations around here..   What gave me the best results was:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon 320M (RS200 IGP)"
	Driver		"radeon"
	BusID		"PCI:1:5:0"
	Option "AGPMode" "4"
	Option "AGPFastWrite" "true"
	Option "EnablePageFlip" "true"
	Option "backingstore" "true"
	Option "AllowGLXWithComposite" "true"
	Option "RenderAccel" "true"
	Option "XAANoOffscreenPixmaps" "true"
	Option "AGPSize" "64"
	Option "AccelMethode" "XAA"
	Option "SubPixelOrder" "NONE"
	Option "DynamicClocks" "true"
	Option "bioshotkeys" "true"
EndSection
```


That gaves me enough performance to try it for a while.   This card is really slow on linux, and too much effects will make things really slow.  Please notice that it only gives me about 250fps on glxgears running on metacity.   Under beryl, i got about 80fps on glxgears and too much flickering.  

Compiz benchmark is about 50fps on 1024x768 and 40 on 1280x1024

If anyone got better results or have recommendations please let me know.

The issues I have are:

1. I cannot watch video.  Starts flickering, and then turns black.
2. Scroll is really slow.  For example, scrolling a web page is painful.
3. Sometimes, it takes a lot to open a simple picture viewer app, or even Home folder, when running under beryl.  Guess the answer is I have only 512RAM, and the crappy card is using 64Mb.

---

### Post by niels on 2006-09-30
I have just made a fresh install of Edgy Beta. I have a ThinkPad T40p with a ATI Mobility FireGL 9000 with 64MB.

I would like to try out some of the new 3D effects, but I don't know if my card is good enough or which method I should use.

I hope some of you can tell me the best way to get some 3D eyecandy.

Here is my xorg.conf:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

---

### Post by anodizer on 2006-09-30
Has anyone made AIGLX work with Radeon 9600 (RV350)? Or is there any updated list with open-source drivers supported chipsets?

edit: it worked!!

---

### Post by ironslave on 2006-09-30
i got my mobility 9200 (shows as 9000) running with the info on the first post 

Option "EnablePageFlip"
Option "ColorTiling" 

but it keeps crashing everytime i close windows, or open some programs....
it seems to happen when beryl tries disconnect itself from a process 

i tried using this :

Option "DRI" "true"
#Option "XAANoOffscreenPixmaps"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
#Option "SubPixelOrder" "RGB"
Option "AccelMethod" "EXA"
Option "RenderAccel" "true"
#Option "AGPMode" "2"
Option "AGPFastWrite" "on"
EndSection

but that made the emerald themes not load

---

### Post by DrSturgeon on 2006-09-30
I have an x300 in my ThinkPad T43, and the following settings seem to do the trick (along with the newest version of beryl):

```

Section "Device"
        Identifier      "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "AccelMethod"           "XAA"
        Option          "AccelDFS"              "1"
        Option          "GARTSize"              "64"
        Option          "EnablePageFlip"        "1"
        Option          "ColorTiling"           "1"
EndSection

```

No hardlocks.  It isn't fast, but it's usable.

---

### Post by Profusion on 2006-09-30
I got this working on my PC following the beginning thread directions. You must install the ATI driver with FGLRX with a Radeon X800 or higher. Following the manual driver install directions from the wiki guide provided here.. Using METHOD 2 [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide")

---

### Post by rekahsoft on 2006-09-30
> **Tails said:**
> ok, here is what i did to get fglrx working...

Open up the Synaptics...

find "fglrx", remove.. fglrx*,  xorg-driver-fglrx*
then 
find "linux-restricted-modules" and remove linux-restricted-modules*      <----- yes, u have to remove this..

restore the "default" xorg.conf
and make sure the device section is using ati driver and NOT fglrx

restart the computer

and then follow this how-to...
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

then the fglrx should be working.. :D
I just did exaclty as you said on my dapper system and igget the following outout from dmesg | grep fglrx```
dmesg | grep fglrx
[17179596.468000] fglrx: module license 'Proprietary. (C) 2002 - ATI Technologies, Starnberg, GERMANY' taints kernel.
[17179596.468000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179596.468000] [fglrx:firegl_init_module] *ERROR* firegl_stub_register failed[17179616.572000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179616.572000] [fglrx:firegl_init_module] *ERROR* firegl_stub_register failed[17179619.772000] [fglrx] Maximum main memory to use for locked dma buffers: 431 MBytes.
[17179619.772000] [fglrx:firegl_init_module] *ERROR* firegl_stub_register failed
``` What is going on? And how do i fix it?

---

### Post by MikeMLP on 2006-09-30
I've been trying to "upgrade" from compiz quinn to beryl.  I had been using compiz-quinn just fine on edgy with the open source driver, through AIGLX.  I  installed the beryl packages, removed the compiz packages, and... I can't get beryl to initialize.  I originally had a setting in startup to get it to work, but I had to go into another session to remove it so I could get back to my normal gnome session.  Each time I try to initialize it from the terminal using $ beryl-manager (or $ beryl) the system freezes and I must restart x.  This really baffles me since I just had the exact same software working, albeit an older version under a different name.  any ideas?

```
Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"

	Driver      "ati"
#	Option	    "VideoOverlay" "on"
#	Option	    "OpenGLOverlay" "off"
EndSection 
```

I didn't change my xorg.conf at all, but here is the ATI section of it for fun...
```
 $ cat /var/log/Xorg.0.log | grep AIGLX
(==) AIGLX enabled
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so

```
and AIGLX is working as well...

---

### Post by Nikos.Alexandris on 2006-10-01
It works!

(Under Dapper with ATI Radeon 9600).

 I followed the "second" how to provided on the Beryl Forum ( [http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome](http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome) ).

There are some problems which I reported in launchpad's bug tracker.

---

### Post by rekahsoft on 2006-10-01
what a happy day...i have finally got fglrx working and have beryl installed and working as welll...now i just need to get xgl working...anybody have a good how to? Thanks

---

### Post by rekahsoft on 2006-10-01
ok...tails how did you get fglrx + xgl + beryl working? cause when i installed xgl it switched back to the Mesa drivers...i am making a clean install and was wondering if you could post your steps and what you did...it would be very much apreciated :) Thanks

---

### Post by summoness on 2006-10-01
I may be wrong,but I thought that beryl/emerald was xgl/compiz.They are just the newer versions/ a fork.

---

### Post by rekahsoft on 2006-10-01
hmm..i have never heard of emerald but beryl is a fork of compiz...

---

### Post by niels on 2006-10-02
> **niels said:**
> I have just made a fresh install of Edgy Beta. I have a ThinkPad T40p with a ATI Mobility FireGL 9000 with 64MB.

I would like to try out some of the new 3D effects, but I don't know if my card is good enough or which method I should use.

I hope some of you can tell me the best way to get some 3D eyecandy.

Here is my xorg.conf:

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"dk"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizScrollDelta"	"0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon R250 Lf [Radeon Mobility 9000 M9]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1400x1050"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050"
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
	InputDevice	"Synaptics Touchpad"
EndSection

Section "DRI"
	Mode	0666
EndSection

```

I did it!

I just followed the instructions in post #6 step by step and now I have all the eyecandy I could ever dream of - and it seems to work smoothly!

Just one more question. Do i have to add something like beryl-start to the gnome startup?

---

### Post by apoclypse on 2006-10-02
> **rekahsoft said:**
> hmm..i have never heard of emerald but beryl is a fork of compiz...


Emarald is cgwd renamed to reflect the new motif (gems I guess) and also to stress that its non platform specific since alot of people still things its compiz-gnome-window-decorator or something eventhough the g was changed to generic quite a while back.

---

### Post by rekahsoft on 2006-10-02
so basicly there is a XGL for called emerald?

---

### Post by llamakc on 2006-10-02
That splash screen is so sweet!

After I rebooted I can't see my gnome-panel. It is running when I check with `ps aux` (plus I tried to start it from cli, and got the 'panel already detected').

The reboot fixed my gtk-theme issue but what about the panel?

This is with an ATI X300, radeon driver, AIGLX, all default plugins still checked (haven't figured out what to uncheck to improve performance yet).

Here's xorg.conf's device section:

```

Section "Device"
        Identifier      "ATI Technologies, Inc. RV370 5B60 [Radeon X300 (PCIE)]"
        Driver          "radeon"
        BusID           "PCI:5:0:0"
        Option          "EnablePageFlip"
        Option          "ColorTiling" "on"
        Option          "UseFBDev" "true"
        Option "XAANoOffscreenPixmaps" "true"
        Option          "DRI" "true"
        Option          "AccelMethod" "EXA"
        Option          "RenderAccel" "true"
        Option          "AGPFastWrite" "on" 
EndSection

```


Anybody else lose their panel?

---

### Post by llamakc on 2006-10-02
```

 killall gnome-panel && gnome-panel &

```Got my panel back, but my emerald is missing from the tray. beryl-manager is running though. I added beryl-manager to my sessions.  

I wonder why it isn't in the tray?

EDIT:

logging off & back on, gives me the icon in the tray, but I lose my gtk theme.

Rebooting gives me my gtk theme back but no gnome-panel visible.

---

### Post by horatiub on 2006-10-02
are the ATI X600 cards working with AIGLX or only XGL?

---

### Post by PRGUY85 on 2006-10-02
Hey there:

I followed this guide with my ATI Radeon 9600 XT. 

[http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome](http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome)

Yet, when I click on the XGL session, it starts and then falls back to the login manager.  I go to Gnome with Metacity and theres the Beryl Manager icon but I cannot switch to Beryl.  I type Beryl on a console terminal and get this:

XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

I am using the regular ati driver, no fglrx.  And I got direct rendering.  What should I do?

---

### Post by rekahsoft on 2006-10-02
You have to disable composit...just add the following to the end of your xorg.conf ```
Section "Extensions"
        Option  "Composite" "0"
EndSection
```. Also are u sure you have DRI working? and that u didn't install the nvidea drivers?

---

### Post by PRGUY85 on 2006-10-02
I did this and now it lets me log in to XGL.  Yet, when I activate Beryl through the manager, the splash appears and then it falls back to login window again.  I have DRI working, since glxinfo sends me a direct rendering: yes notification.  I have the regular ati/radeon drivers, no flgrx.

---

### Post by PRGUY85 on 2006-10-02
It started working out of nowhere and I changed theme, fixed settings on the beryl manager.  Yet, I used the scroll wheel once on my mouse and it log out and has not let me in on Beryl again.  I have seen it works, now I must find a way to make it work all the time...

---

### Post by pecos7 on 2006-10-02
> **rekahsoft said:**
> so basicly there is a XGL for called emerald?

No...!
Emerald is an application to change beryl theme.
On my notebook with an ATI 9700, I used XGL + beryl + emerald

---

### Post by PRGUY85 on 2006-10-02
Right now, its working like a charm.  Lets see if it continues like that.

---

### Post by llamakc on 2006-10-02
I guess I don't 'minimize' windows very often, and instead shade them.

I just minimized one and was wowed by the animation. Very nice job.

---

### Post by PRGUY85 on 2006-10-02
Hey my situation right now is that it works allright until at one moment it goes into the login screen.  Both times it has been because of mouse scrolling,though it happens with sporadic mouse scrolling not all the time.  What could this be?  The second time I used it for 30 min or so before it reverted to login screen.

Also, I already put the Fast render option.  Any other way to make this faster without sacrificing the effectS?

---

### Post by rekahsoft on 2006-10-02
does anybody know how to get fglrx + XGL + Beryl working on edgy beta 1?

---

### Post by PRGUY85 on 2006-10-02
Now glxinfo is showing no in direct rendering which is weird.  How can I activate it again if I haven't changed anything on the xorf.conf or drivers?

---

### Post by pecos7 on 2006-10-03
> **rekahsoft said:**
> does anybody know how to get fglrx + XGL + Beryl working on edgy beta 1?
I used the second howto in this post for dapper and it works also in edgy
[http://forum.beryl-project.org/topic...-how-for-gnome]("http://forum.beryl-project.org/topic...-how-for-gnome")

---

### Post by MikeMLP on 2006-10-03
> Now glxinfo is showing no in direct rendering which is weird. How can I activate it again if I haven't changed anything on the xorf.conf or drivers?

Huh... the same thing is happening to me.  I'm trying to get AIGLX working in edgy... this could explain why beryl won't initialize...

---

### Post by PRGUY85 on 2006-10-03
I installed the fglrx drivers and now its working though Direct Rendering is off.

---

### Post by sinppa_ on 2006-10-03
Whoah, I'm pretty confused with this whole beryl/emerald-thing :I Well,I somehow got those packages installed and so on, they seem to work when I start beryl & emerald. Now I would like to know how to add separate beryl-session to gdm. Like "normal gnome-session" and "beryl-session". I hope you understand what I'm trying to say :)

---

### Post by rekahsoft on 2006-10-03
> **pecos7 said:**
> I used the second howto in this post for dapper and it works also in edgy
[http://forum.beryl-project.org/topic...-how-for-gnome]("http://forum.beryl-project.org/topic...-how-for-gnome")

your link is broken...it should be to this: [http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome](http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome)

---

### Post by rekahsoft on 2006-10-03
> **sinppa_ said:**
> Whoah, I'm pretty confused with this whole beryl/emerald-thing :I Well,I somehow got those packages installed and so on, they seem to work when I start beryl & emerald. Now I would like to know how to add separate beryl-session to gdm. Like "normal gnome-session" and "beryl-session". I hope you understand what I'm trying to say :)

it shows how to do this is in the [how-to for gnome on the Beryl forums]("http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome") in method 2.

---

### Post by Agio on 2006-10-03
To PRGUY85

At the Beryl [howto]("http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome") they say that it is normal for that to happen. I had the same concern too =):

"Note for all cards: glxinfo will show that direct rendering is not working , dont worry thats normal when you are running xgl."

I've only had it for a few minutes but it seems to work quite well, ugly, but smooth. I'll give it a try to see how it does with every day use ;) 

ATI X300 PCI with fglrx.

---

### Post by rekahsoft on 2006-10-03
> **Agio said:**
> To PRGUY85

At the Beryl [howto]("http://forum.beryl-project.org/topic-4863-howto-xgl-and-beryl-how-for-gnome") they say that it is normal for that to happen. I had the same concern too =):

"Note for all cards: glxinfo will show that direct rendering is not working , dont worry thats normal when you are running xgl."

I've only had it for a few minutes but it seems to work quite well, ugly, but smooth. I'll give it a try to see how it does with every day use ;) 

ATI X300 PCI with fglrx.

WHAT???How is that normal...you have to have DRI for XGL to look ok at all!!

---

### Post by JeevesBond on 2006-10-04
What that means is that when XGL is running glxinfo will *report* that direct rendering is not working, what it reports and what's reality is different. XGL is very hacky. :)

---

### Post by Belibem on 2006-10-04
Xgl takes DRI just for its operation and it excludes all other applications from it. That's why xorg reports that there is no direct rendering when xgl is enabled, that is why games and other 3d apps can not go along xgl and that is why xgl will be obsoleted by aiglx.

---

### Post by rekahsoft on 2006-10-04
> **Belibem said:**
> Xgl takes DRI just for its operation and it excludes all other applications from it. That's why xorg reports that there is no direct rendering when xgl is enabled, that is why games and other 3d apps can not go along xgl and that is why xgl will be obsoleted by aiglx.

ok that makes sence...when will fglrx support AIGLX extensions?

---

### Post by Belibem on 2006-10-04
fglrx is a closed source product from ATI. They will support aiglx when they feel it financially efficient for them. And even when they do, only ATI would be able to update the driver every time there is a kernel update. However it seems that big companies are not rushing to do so. That could mean that every time you upgrade your kernel it may lead to several days without 3d support until new restricted drivers arrive. 

Luckily we have another option: the open source "radeon" driver. Especially if you have an an ATI card based on a R3xx or a R4xx chipset you should definitely give "radeon" driver a try! 
Apart from aiglx/beryl you get a lot of openlg apps (including popular games) working just fine. Check this out:
[http://dri.freedesktop.org/wiki/R300%20Application](http://dri.freedesktop.org/wiki/R300%20Application)

---

### Post by Melvil on 2006-10-04
This driver is buggy and slow for my r350

---

### Post by rekahsoft on 2006-10-04
and it does not provide DRI with my card the radeon 200M.

---

### Post by Kosmonaut on 2006-10-05
Hey!

I just want to confirm that this how-to works perfectly with an ati "radeon" 9200 mobility+KDE.
Thanks!

---

### Post by jkl' on 2006-10-05
Hi, all.

I've got a
[INDENT]01:00.0 VGA compatible controller: ATI Technologies Inc RV280 [Radeon 9200 SE] (rev 01)[/INDENT]
and I can't get beryl to work in xorg+the open source radeon driver in edgy. I used to have dapper installed on the same machine and compiz worked fine in aiglx (Xair). But now, when I start beryl-manager (or beryl alone), the screen freezes (except for the mouse cursor, which moves and even changes shape). I can switch to the text console, kill beryl-manager and beryl from there, and then start metacity and everything works fine again. In the terminal, from which I started beryl-manager, I can see beryl autodetection report (no xgl, no nvidia, aiglx). There are no errors.

I tried various combinations of options in Section "Device": some just froze the whole machine, most didn't seem to do anything. I used dpkg-reconfigure to generate a clean xorg.conf, and tried setting options in it. No luck.

Could Belibem or someone with a low-end Radeon post a **full** working xorg.conf? Should there be an "Extensions" section enabling Composite? Should there be some options in the "Screen" section (nvidia guides mention "AddARGBGLXVisuals")? Should there be an "AIGLX" option in the "ServerLayout" section? Which modules should be loaded?

Thanks for any help.

— Jan

---

### Post by Belibem on 2006-10-05
Hi 
AFAIK no other changes (except those in the device section) are required to get it working. In fact beryl should work with no changes in xorg at all. Those options are for speed optimization. 

Can you try those commands?
1)glxinfo | grep direct
it should return something like this
libGL warning: 3D driver claims to not support visual 0x4b
direct rendering: **Yes**

If you get a No then there is a problem with dri.

2)do:
lsmod

It should indicate that radeon and drm drivers are loaded

3)also try:
cat /var/log/Xorg.0.log
This may provide some clues to the problem

---

### Post by jkl' on 2006-10-05
Thanks, Belibem. Direct rendering was disabled, because during the upgrade to edgy, the mesa library had been kept at the version from quinn's repository, instead of being downgraded to the edgy version. I downgraded the package manually, and instantly got direct rendering enabled.

---

### Post by rekahsoft on 2006-10-05
> **jkl' said:**
> Thanks, Belibem. Direct rendering was disabled, because during the upgrade to edgy, the mesa library had been kept at the version from quinn's repository, instead of being downgraded to the edgy version. I downgraded the package manually, and instantly got direct rendering enabled.

so basicly if i lock the version when i have DRI working then i will be all good. btw the mesa library package is called libgl1-mesa right?

---

### Post by rekahsoft on 2006-10-05
> **rekahsoft said:**
> so basicly if i lock the version when i have DRI working then i will be all good. btw the mesa library package is called libgl1-mesa right?

nope...locking i does not work...how do i downgrade it so my DRI works again?

---

### Post by jkl' on 2006-10-06
> **rekahsoft said:**
> nope...locking i does not work...how do i downgrade it so my DRI works again?
I did it in aptitude (find the package, tap Enter, go down to the list of available versions, and select 6.5.1~20060817-0ubuntu2 for installation), but this should work from the command line:

sudo apt-get install libglu1-mesa=6.5.1~20060817-0ubuntu2

---

### Post by rekahsoft on 2006-10-06
ok...i found the problem...i needed to recompile the fglrx kernel sources.

---

### Post by krisbowen on 2006-10-13
I finally got it going very well and very smoothly. It has been stable for awhile now. everysingle tick box has been enabled!!!!

I followed this guide for getting Beryl. I followed Ubuntu Edgy wiki for Ati driver install.

modified the gdm.conf file with the 1=standard
and the

GdmXserverTimeout=50

changes

It is late and I have a wife that wants some attention. I will put up the links to the howto's tomorrow.

btw

Edgy on a Toshiba Satelltie M40 Celeron 1.6 ghz 
Ati Radeon xpress 200m 128mb (shared)
700+ mb RAM

---

### Post by krisbowen on 2006-10-13
how do you get a screeen shot this is so lovely!!!:-D

---

### Post by pinkelmer on 2006-10-13
I set up beryl + xgl to work with my MOBILITY RADEON 9600 Generic. It works, but it's not very snappy. I get 70 frames/s with the beryl benchmark (this is on compaq nc6000 laptop). Is it the expected performance, or is there any tuning usable to get it working more smoothly ?

---

### Post by dcherryholmes on 2006-10-13
I really wanted to run AIGLX and the open drivers, but after trying every permutation of xorg.conf I could find (all the ones suggested in this thread, and then some), I could not escape hard locks of my video card (x300).  Now I'm back on Xgl and fglrx.  Maybe it is a fugly extra layer on top of X, and maybe they are eeeeeeevil closed source drivers, but everything is running like butter again.

---

### Post by MrBlond83 on 2006-10-13
The bottom line is that the fglrx driver yield much better performance than the open source "radeon" driver. There is no other way to put it. Benchmarking shows that the FPS received using fglrx driver in OpenGL games is between 1.5-3 times the FPS received using the open source driver.
Which is why fglrx+XGL+Beryl runs much smoother than radeon+Xorg7.1+Beryl.

Maybe some day we will not need XGL for Beryl but at this time the open source drivers are not even close in performance.

---

### Post by krisbowen on 2006-10-13
I would agree about the open source drivers being crap.
I have Ati xpress 200m, with Aiglx beryl would render the cube (white) and allow a half turn before crashing.](*,) 

Switched to the fglrx that comes withe Edgy.....wobbliness:D 


BTW thanks to Pricechild, Amanarath, Belibem..the guys at Beryl Wiki... after a week of trying I have finally managed to catch up and have the cool toys!!!!:twisted:

---

### Post by krisbowen on 2006-10-13
Okay, i promised I would do this.

For an Ati Radeon Xpress 200M

Note: most of this is found on other How to's (Amaranth & conn from IRC channels, PriceChild from Ubuntu forum and Racer11 from Beryl-project.org)

The begining: I started with a vanilla Dapper install then upgraded to Edgy.

sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade

Add one of these repos in "system>admin>software sources" or /etc/apt/sources.list

Code:
 deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy
deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy



Run one of these commands to add Quinn's key.

Code:
wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
wget [http://media.blutkind.org/xgl/quinn.key.asc](http://media.blutkind.org/xgl/quinn.key.asc) -O - | sudo apt-key add -
wget [http://compiz-mirror.lupine.me.uk/quinn.key.asc](http://compiz-mirror.lupine.me.uk/quinn.key.asc) -O - | sudo apt-key add -
wget [http://ubuntu.compiz.net/quinn.key.asc](http://ubuntu.compiz.net/quinn.key.asc) -O - | sudo apt-key add -

Make sure to:
Sudo aptitude update

Now for the Ati Drivers:

Make sure the *restricted* repository is enabled in /etc/apt/sources.list or this guide will not work! 


sudo aptitude install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo aptitude install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

At this stage I probably should have rebooted, but I didn't ..up to you if you do.


Now go and get the toys:

sudo aptitude install  xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings emerald emerald-themes


-Modify /etc/gdm/gdm.conf-custom

Code:
sudo gedit /etc/gdm/gdm.conf-custom
-look for [servers] and paste this:

Code:
 [servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true


-Modify /etc/gdm/gdm.conf 

Code:
sudo gedit /etc/gdm/gdm.conf

-And change

Code:
#0=Standard
1=Standard

-Go to line 198 and change GdmXserverTimeout=10 to  (this one is very important!!!)

Code:
GdmXserverTimeout=50



 Make a startup script for xgl:

Code:
sudo gedit /usr/bin/startxgl.sh

-Paste this Code into the .sh :
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
# Start GNOME
exec gnome-session


-Make the script executable

Code:
sudo chmod 755 /usr/bin/startxgl.sh


-Make a xgl session for the login manager:
Code:
sudo gedit /usr/share/xsessions/xgl.desktop

Paste this code into the .desktop:

[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

Now at this stage you could go to you startup programs and add beryl et al to it,  I however did not, I just login to an XGL session at this stage.


next just make sure you have everything nice and new

Code:
sudo aptitude update

Once that is done reboot. Yes Reboot. Did I say reboot, oh sorry, I meant Reboot.;) 

Now at your login Screen choose Options and change session to a XGL session.  Once you confirm that you have cubage (Ctrl+alt left or right arrow ) and the excitement dies down...8) ... start your terminal (or press Alt+F2) and type beryl-manager.

Now click the red jewel and really start to enjoy the eye candy.


This was written as an compilation of several How to's see top for credits.

---

### Post by niels on 2006-10-15
Hi there,

As i wrote some weeks ago, I now have bryl with aixgl running. But I have a another problem. I can't see any movies...

I have tried totem, mplayer and VLC, but I don't get any picture. I can here the sound and sometimes gets glimpse of the movies.

What might the problem be, and how do i solve it?

EDIT:
Now video works with Totem and VLC (don't know why!), but Mplayer still doesn't work... And thats a problem, because I think it's the best for internet videos...

---

### Post by llamakc on 2006-10-15
I had the same problem. Making sure the movie's window had focus and moving it a bit with the mouse restored the video. Focus must remain on the movie window for me.

---

### Post by aamukahvi on 2006-10-20
Yay! Got it working with my pesky R8500 & Athlon 1700+ @ 1680x1050. A bit choppy but oh well, what'd you expect :mrgreen:

---

### Post by Anonii on 2006-10-21
> **Belibem said:**
> Radeon open source driver, aiglx, and Beryl

The following steps apply for all ATI cards supported by the radeon open source driver. To find out whether your ATI card is supported look here:
[http://dri.freedesktop.org/wiki/ATIRadeon](http://dri.freedesktop.org/wiki/ATIRadeon)
If your ATI card is not supported by the radeon driver consider using fglrx driver and xgl

1) Uninstall fglrx if it is installed (use synaptic or whatever you like)

2)
STEP 1 from [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)


3)
STEP 3 from [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)


4)
Edit the device section in your xorg.conf to be like this
Section "Device"
	Identifier	"{your card model}" [COLOR="Red"]<-do not edit this line in your xorg.conf[/COLOR]
	Driver		"radeon"
    	Option    	"DRI" "true"
    	Option    	"ColorTiling" "on"
    	Option    	"EnablePageFlip" "true"
    	Option    	"AccelMethod" "EXA"
        Option          "XAANoOffscreenPixmaps"
    	Option    	"RenderAccel" "true"
    	#Option    	"AGPMode" "[COLOR="Red"]x[/COLOR]"     [COLOR="Red"]<- x may be 2 or 4 depending on your system[/COLOR]
	Option		"AGPFastWrite" "on" 
EndSection


Note: line for agpmode is disabled  (to enable remove #) because it may cause your xorg to crash. Use it with caution!!!
Note2: instead of "AccelMethod" "EXA" you can use "AccelMethod" "XAA". XAA is seems to bit a bit faster but not as stable.
Note3: for more details about r300 specific options take a look here:
[http://www.xfree86.org/current/radeon.4.html](http://www.xfree86.org/current/radeon.4.html)

5)
STEP 5 from [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)


I get about 80-90fps in tremulous at 1280x1024, full detail and 250-300fps in beryl with this setup. I have an X800.

Greetings there, seems like your step 4, wont work on me. After my PC passes the boot stage and gets into the login screen, my PC will freeze and my monitor will close (from green light, to yellow light.). From there, the only thing I can do is reboot, go to single user, and either restore the old xorg, or recreate one with dpkg-reconfigure xserver-xorg.

Any ideas?

---

### Post by nariusb on 2006-10-21
Hi everyone,
I wonder if you can help me to fix below:
What would cause beryl manger not to load automaticly at start? It works great when I click on ruby icon and chose reload window manager.
I have this line in sessions start programs:
/usr/bin/beryl-manager 
I'm not able to get anything out of fglrinfo now, after beryl. Here's:
narius@narius:~$ fglrxinfo
Error: unable to open display :0


Also when booting up and just before login promp my screen is grey grit and resets normal for the login window.


 This is my /etc/X11/xorg.conf


# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]" 0 0
	InputDevice    "Generic Keyboard"
	InputDevice    "Configured Mouse"
	InputDevice    "stylus" "SendCoreEvents"
	InputDevice    "cursor" "SendCoreEvents"
	InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
	FontPath     "/usr/share/X11/fonts/misc"
	FontPath     "/usr/share/X11/fonts/cyrillic"
	FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath     "/usr/share/X11/fonts/Type1"
	FontPath     "/usr/share/X11/fonts/100dpi"
	FontPath     "/usr/share/X11/fonts/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load  "i2c"
	Load  "bitmap"
	Load  "ddc"
	Load  "dri"
	Load  "extmod"
	Load  "freetype"
	Load  "glx"
	Load  "int10"
	Load  "type1"
	Load  "vbe"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "CoreKeyboard"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc104"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Device" "/dev/input/mice"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "ZAxisMapping" "4 5"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "stylus"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "stylus"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "eraser"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "eraser"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
	Identifier  "cursor"
	Driver      "wacom"
	Option	    "Device" "/dev/wacom"          # Change to 
	Option	    "Type" "cursor"
	Option	    "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
	Identifier   "IBM T85A"
	HorizSync    28.0 - 64.0
	VertRefresh  43.0 - 60.0
	Option	    "DPMS"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Driver      "ati"
	BusID       "PCI:1:0:0"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSection

Section "Screen"
	Identifier "Default Screen"
	Device     "ATI Technologies, Inc. RV350 AS [Radeon 9600]"
	Monitor    "IBM T85A"
	DefaultDepth     24
	SubSection "Display"
		Depth     1
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     4
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     8
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     15
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     16
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth     24
		Modes    "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
        Option  "Composite" "0"
EndSection

---

### Post by miobio on 2006-10-21
Hello everybody
 
 It's an entire afternoon that i'm playing around with my Kubuntu edgy (updated from dapper yesterday) to get Xgl + compiz to work again (used to work under dapper).
 
 The xgl server seems to run properly BUT!
 
 When i launch beryl-manager i get this strange error:
 
 "support for non power of two textures missing"
 
 after this, beryl doesn't start and i loose the window manager.
 
 
 Do you have any ideas? If you think u need any kind of config file or stuff like that tell me and i'll paste it.
 
 My video card is a Radeon Mobility X600 (M24).
 
 I guess it could be an Xorg 7.1 problem seen the fact that everything was working before  
 
 
 Please HELP!!!
 
 Thanks

---

### Post by skyshard on 2006-10-21
> **krisbowen said:**
> Okay, i promised I would do this.

For an Ati Radeon Xpress 200M

Note: most of this is found on other How to's (Amaranth & conn from IRC channels, PriceChild from Ubuntu forum and Racer11 from Beryl-project.org)

The begining: I started with a vanilla Dapper install then upgraded to Edgy.
```

sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade
```

Add one of these repos in "system>admin>software sources" or /etc/apt/sources.list

```
 deb [http://www.beerorkid.com/compiz](http://www.beerorkid.com/compiz) edgy main-edgy
deb [http://media.blutkind.org/xgl/](http://media.blutkind.org/xgl/) edgy main-edgy
deb [http://compiz-mirror.lupine.me.uk/](http://compiz-mirror.lupine.me.uk/) edgy main-edgy
deb [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) edgy main-edgy
```



Run one of these commands to add Quinn's key.

```
wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -
wget [http://media.blutkind.org/xgl/quinn.key.asc](http://media.blutkind.org/xgl/quinn.key.asc) -O - | sudo apt-key add -
wget [http://compiz-mirror.lupine.me.uk/quinn.key.asc](http://compiz-mirror.lupine.me.uk/quinn.key.asc) -O - | sudo apt-key add -
wget [http://ubuntu.compiz.net/quinn.key.asc](http://ubuntu.compiz.net/quinn.key.asc) -O - | sudo apt-key add -
```

Make sure to:
```
Sudo aptitude update
```

Now for the Ati Drivers:

Make sure the *restricted* repository is enabled in /etc/apt/sources.list or this guide will not work! 


```
sudo aptitude install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo aptitude install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

At this stage I probably should have rebooted, but I didn't ..up to you if you do.


Now go and get the toys:
```

sudo aptitude install  xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings emerald emerald-themes

```

-Modify /etc/gdm/gdm.conf-custom

```
sudo gedit /etc/gdm/gdm.conf-custom
```
-look for [servers] and paste this:

```
 [servers]
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true
```


-Modify /etc/gdm/gdm.conf 

```
sudo gedit /etc/gdm/gdm.conf

```
-And change

```
#0=Standard
1=Standard
```

-Go to line 198 and change GdmXserverTimeout=10 to  (this one is very important!!!)

```
GdmXserverTimeout=50
```



 Make a startup script for xgl:

```
sudo gedit /usr/bin/startxgl.sh

-Paste this Code into the .sh :
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
# Start GNOME
exec gnome-session
```


-Make the script executable

```
sudo chmod 755 /usr/bin/startxgl.sh
```


-Make a xgl session for the login manager:

```
sudo gedit /usr/share/xsessions/xgl.desktop
```

Paste this code into the .desktop:
```

[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
```

Now at this stage you could go to you startup programs and add beryl et al to it,  I however did not, I just login to an XGL session at this stage.


next just make sure you have everything nice and new

```
sudo aptitude update
```

Once that is done reboot. Yes Reboot. Did I say reboot, oh sorry, I meant Reboot.;) 

Now at your login Screen choose Options and change session to a XGL session.  Once you confirm that you have cubage (Ctrl+alt left or right arrow ) and the excitement dies down...8) ... start your terminal (or press Alt+F2) and type beryl-manager.

Now click the red jewel and really start to enjoy the eye candy.


This was written as an compilation of several How to's see top for credits.

added code tags so the smileys wouldnt show up...

---

### Post by sbentzen on 2006-10-22
i would like a quick straight answer, is the ati mobility 9200 radeon for mac supported with beryl and aiglx? (not testing user, just downloaded the rc)

---

### Post by Iradiatul on 2006-10-24
Hi

I have a compaq nx6325 with ATI Xpress M200 and Ubuntu Edgy installed.
I followed krisbowen instructions but unfortunately without to much luck.
After the restart i have a white/gray/black screen in a very strange model/unreadable instead of the login screen of the usual Xorg. 
I had to go to vi and edit gdm.conf and gdm.conf-custom (reedit them to the original settings), and then the Xorg could start normally, and without beryl offcourse.

I am trying already for two weeks (from time to time), i read a lot but i'm new to linux and i really wish i could solve this problem.

Please lead me in a good directions with any hints you could.
Thank You

---

### Post by PriceChild on 2006-10-26
*moves*

---

### Post by freeman512 on 2006-10-30
I have the same problem... have you find any solutions ?


> **anodizer said:**
> I managed to get Xgl and beryl, but everything is crappy now :/ An ugly GTK theme is used, which I can't even change it! (or the icon theme..)
Any help?

Here's a screenshot:

[img]http://img.photobucket.com/albums/v384/klaount/Screenshot-1.png[/img]

---

### Post by freeman512 on 2006-10-30
I have found a solution -> [http://forum.beryl-project.org/topic-3243-gtk-themes-don-function-with-xgl](http://forum.beryl-project.org/topic-3243-gtk-themes-don-function-with-xgl)

---

### Post by edemark on 2006-11-07
Hi all

I do not know what is the problem of my machine but i am just unable to get beryl work
I followed this thread to set it up but i only get this error message:

 XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

any idea what am i missing? 
thanks in advence

---

### Post by justifier on 2006-11-09
YES WOOOOT thank you so so sos so so so much got it working on a HP compaq nc4010 :D:D:D wooot damn this is sexy

---

### Post by madelephant on 2006-11-10
Hey everyone-

I followed the ATI guide posted by skyshard (very clear & easy to follow) and after I did the final reboot I am met by a screen of white/black/gray blocks and the loading mouse pointer.  I am stuck from here, not sure what to try next.  Guessing it might be driver related?

I'm running on a ATI Radeon XPRESS 200m card.

Most likely the same problem Iradiatul is having-
>  	Hi

I have a compaq nx6325 with ATI Xpress M200 and Ubuntu Edgy installed.
I followed krisbowen instructions but unfortunately without to much luck.
After the restart i have a white/gray/black screen in a very strange model/unreadable instead of the login screen of the usual Xorg.
I had to go to vi and edit gdm.conf and gdm.conf-custom (reedit them to the original settings), and then the Xorg could start normally, and without beryl offcourse.

I am trying already for two weeks (from time to time), i read a lot but i'm new to linux and i really wish i could solve this problem.

Please lead me in a good directions with any hints you could.
Thank You

---

### Post by madelephant on 2006-11-10
I fixed my problem by adding this to /etc/X11/xorg.conf-

Section "Extensions"
Option "Composite" "false"
EndSection

---

### Post by kesman on 2006-11-15
> **edemark said:**
> Hi all

I do not know what is the problem of my machine but i am just unable to get beryl work
I followed this thread to set it up but i only get this error message:

 XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension

any idea what am i missing? 
thanks in advence
I have this exact same problem too. When I launch beryl-manager it says what mentioned above, and then falls back to metacity window manager. When I then try to change back to beryl from the taskbar icon, it says:

```
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: No composite extension
```

I have 
Section "Extensions"
Option "Composite" "disable"
EndSection

at the end of my xorg.conf.
What's the problem? :D Everyone else seems to get this working in no time..
I have an acer laptop with x700 radeon in it. On dapper fglrx+beryl worked perfectly.

Edit:
Well, I enabled the composite extension with "enable" instead of "disable", and now beryl started. Yet there's still an error popping out telling me that:

libGL warning: 3D driver claims to not support visual 0x4b
Initiating splash
beryl: water: GL_ARB_fragment_program is missing

but beryl's now working.

---

### Post by ericesque on 2006-11-15
maybe it is time to try beryl again.  last time it didn't like me.  So many things to try, so little time.

---

### Post by Bingo Jesus on 2006-11-15
> **madelephant said:**
> Hey everyone-

I followed the ATI guide posted by skyshard (very clear & easy to follow) and after I did the final reboot I am met by a screen of white/black/gray blocks and the loading mouse pointer.  I am stuck from here, not sure what to try next.  Guessing it might be driver related?

I'm running on a ATI Radeon XPRESS 200m card.

Most likely the same problem Iradiatul is having-

I'm also suffering from this problem, but seeing as I'm new to Ubuntu I wasn't sure how to fix it apart from a fresh Ubuntu installation.

I'm also running an ATI Radeon Xpress 200M.

---

### Post by kesman on 2006-11-16
Oh and by the way, I also get this from Xorg's log:
```

$ cat /var/log/Xorg.0.log|grep AIGLX|more
(==) AIGLX enabled
(WW) AIGLX: 3D driver claims to not support visual 0x23
(WW) AIGLX: 3D driver claims to not support visual 0x24
(WW) AIGLX: 3D driver claims to not support visual 0x25
(WW) AIGLX: 3D driver claims to not support visual 0x26
(WW) AIGLX: 3D driver claims to not support visual 0x27
(WW) AIGLX: 3D driver claims to not support visual 0x28
(WW) AIGLX: 3D driver claims to not support visual 0x29
(WW) AIGLX: 3D driver claims to not support visual 0x2a
(WW) AIGLX: 3D driver claims to not support visual 0x2b
(WW) AIGLX: 3D driver claims to not support visual 0x2c
(WW) AIGLX: 3D driver claims to not support visual 0x2d
(WW) AIGLX: 3D driver claims to not support visual 0x2e
(WW) AIGLX: 3D driver claims to not support visual 0x2f
(WW) AIGLX: 3D driver claims to not support visual 0x30
(WW) AIGLX: 3D driver claims to not support visual 0x31
(WW) AIGLX: 3D driver claims to not support visual 0x32
(II) AIGLX: Loaded and initialized /usr/lib/dri/r300_dri.so

```

What's that? My Beryl's working quite well, just a bit slow that's all.

---

### Post by VCSkier on 2006-12-06
> **Belibem said:**
> Radeon open source driver, aiglx, and Beryl

The following steps apply for all ATI cards supported by the radeon open source driver. To find out whether your ATI card is supported look here:
[http://dri.freedesktop.org/wiki/ATIRadeon](http://dri.freedesktop.org/wiki/ATIRadeon)
If your ATI card is not supported by the radeon driver consider using fglrx driver and xgl

1) Uninstall fglrx if it is installed (use synaptic or whatever you like)

2)
STEP 1 from [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)


3)
STEP 3 from [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)


4)
Edit the device section in your xorg.conf to be like this
Section "Device"
	Identifier	"{your card model}" [COLOR="Red"]<-do not edit this line in your xorg.conf[/COLOR]
	Driver		"radeon"
    	Option    	"DRI" "true"
    	Option    	"ColorTiling" "on"
    	Option    	"EnablePageFlip" "true"
    	Option    	"AccelMethod" "EXA"
        Option          "XAANoOffscreenPixmaps"
    	Option    	"RenderAccel" "true"
    	#Option    	"AGPMode" "[COLOR="Red"]x[/COLOR]"     [COLOR="Red"]<- x may be 2 or 4 depending on your system[/COLOR]
	Option		"AGPFastWrite" "on" 
EndSection


Note: line for agpmode is disabled  (to enable remove #) because it may cause your xorg to crash. Use it with caution!!!
Note2: instead of "AccelMethod" "EXA" you can use "AccelMethod" "XAA". XAA is seems to bit a bit faster but not as stable.
Note3: for more details about r300 specific options take a look here:
[http://www.xfree86.org/current/radeon.4.html](http://www.xfree86.org/current/radeon.4.html)

5)
STEP 5 from [http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)


I get about 80-90fps in tremulous at 1280x1024, full detail and 250-300fps in beryl with this setup. I have an X800.
I apprecieate this, as I think we need more/better advice and help for people using the open source "radeon" driver and AIGLX.  I do have a couple comments though.

First of all, I think you may have EXA and XAA mixed up.  XAA is the default acceleration method that is reportedly stable.  EXA, OTOH, is the newer method that is potentially faster, and potentially less stable.  This can be verified via $ man radeon.  Also, as xsacha explained to me on #beryl, the "**ANoOffscreenPixmaps" option needs to match the acceleration method; if you are using EXA, you will need "EXANoOffscreenPixmaps", and if you are using XAA, you will need "XAANoOffscreenPixmaps".  This IIRC, among other things, prevents the white titlebars on maximized windows.

I also have a question though.  How many of the options are applicable to PCI cards?  A friend of mine has a AMD64 desktop with a ATi Radeon 9250 PCI bus card and we are trying to configure his xorg.conf in Ubuntu Edgy to give him acceptable performance in beryl through AIGLX.  The chipset is rv280.  Even with just a Firefox window open, frame rates will dip below 15 fps, maybe even below 10 fps, which is unacceptable, considering his graphics card has 256 MB DDR RAM, he has a speedy dual-core processor, and a GB of system RAM.

We've tried many different combinations of xorg.conf options, and none of them have helped. Do any of you have any other experience or recommendations, or could this be a bug related to his particular card or chipset?  Do any of you have any other advice or ideas?  Thanks!

---

### Post by alan_daniel on 2006-12-16
> **DrSturgeon said:**
> I have an x300 in my ThinkPad T43, and the following settings seem to do the trick (along with the newest version of beryl):

```

Section "Device"
        Identifier      "ATI Technologies, Inc. M22 [Radeon Mobility M300]"
        Driver          "radeon"
        BusID           "PCI:1:0:0"
        Option          "AccelMethod"           "XAA"
        Option          "AccelDFS"              "1"
        Option          "GARTSize"              "64"
        Option          "EnablePageFlip"        "1"
        Option          "ColorTiling"           "1"
EndSection

```

No hardlocks.  It isn't fast, but it's usable.

What did you do to get this working outside of the other steps at the beginning of this thread? I also have a T43, but I noticed that when I began editing the xorg.conf, my driver was listed as "ati"

Is that a problem? Do I need to install the radeon driver?

Thanks for any help

---

### Post by quaggo on 2006-12-18
I followed the steps provided in post #7 on my Ubuntu "edgy" clean install. My laptop is a Dell Latitude D600. Video card is a Radeon R250 Lf [FireGL 9000]. After the clean install of Edgy, I believe the open source driver is installed by default. So, I just followed the steps from post #7 (fglrx was not already installed as far as I could tell)

At any rate, the good news is that I can start up beryl using the beryl-manager command from a terminal however the desktop area is all white (instead of my desktop picture). Also, the right side of the screen (from where the seperator starts and to the far right edge of the screen) is like an empty column of white. I can rotate the cube and the right side of each deskotp is liek this, only once the cube has been rotated then the column on the right is all black on all desktops. So, this means I cannot access teh menu options at the top right , or see the clock or date, etc.  The window effects and such work fine though on teh "working" part of the screen, and I can load the themes, etc. from emerald.

::::::::::::::::::::::::::::::::::::::::::::
In my terminal when I run beryl-manager I come up with the following:

libGL warning: 3D driver claims to not support visual 0x4b
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
libGL warning: 3D driver claims to not support visual 0x4b
initiating splash
beryl: water: GL_ARB_fragment_program is missing
Reloading all options
::::::::::::::::::::::::::::::::::::::::::::

***UPDATE*** 

I found out that by lowering my resolution setting in the ubuntu preferences to 1024X768 or lower, I will get the proper display. But being that I am on a laptop this really doesn't work out very well for me. I need to get this working in a 1400x1050 or better resolution. Any thoughts?

Does anyone know what step I should take next in troubleshooting this problem? Sorry, im' a linux/ubuntu noob with a desire to learn, and I figure getting something like this will definately help me to learn fast. I already have become quite fluent with using the terminal and commands  :-)

Thanks in advance for any help that may be provided!

---

### Post by quaggo on 2006-12-20
Ok..I found someone on the net that got this working. Basically, I have a Dell D600 Laptop with an ATI Radeon 250  9000 series video chip. I have had lots of problems with getting Beryl to work properly in Edgy. The following directions FINALLY got Beryl to work for me using AIGLX. The directions cover both AIGLX and XGL. I am going to try XGL next but I -HAVE- tested the AIGLX steps and they DO work..however..the OS will run very slow. (hence, my next attempt at using XGL :)

here's the beef:
(much props to Aleksandar Bilanovic for putting this together, the original source is at the following URL)

[http://blogs.sun.com/bilke/entry/beryl_ubuntu_edgy_on_dell](http://blogs.sun.com/bilke/entry/beryl_ubuntu_edgy_on_dell)

================
open terminal and assume root privileges:

sudo su -

change to tmp dir as we are going to download some packages manually:

cd /var/tmp

add beryl and emerald ubuntu repository to sources.list and update packages list:

echo "deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main" >> /etc/apt/sources.list
gpg --keyserver subkeys.pgp.net --recv 3FF0DB166A7476EA
gpg --export --armor 3FF0DB166A7476EA | apt-key add -
apt-get update

install beryl and emerald themes:

apt-get install beryl emerald-themes

from this point you can choose whether to proceed with flgrx/Xgl or radeon/AIGLX. Let's first see how it works with flgrx/Xgl (for radeon/AIGLX scroll down):

install fglrx driver:

apt-get install xorg-driver-fglrx

instead of installing xgl server from the ubuntu repository use misha680's patched xserver-xgl:

wget [http://misha680.googlepages.com/xgl-edgy.zip](http://misha680.googlepages.com/xgl-edgy.zip)
unzip xgl-edgy.zip
dpkg -i xserver-xgl_7.0.0.git.20060725-0ubuntu2.1.fglrx.r200_i386.deb # or whatever the name might be in the time you are installing

switch from ati to fglrx video driver:

sed -i -e 's/"ati"/"fglrx"/' /etc/X11/xorg.conf

disable composite:

cat >> /etc/X11/xorg.conf << EOS
Section "Extensions"
   Option "Composite" "false"
EndSection
EOS

next step is to create launcher script for starting xgl server. Create file /usr/bin/startxgl with the following contents:

#!/bin/sh
Xgl :1 -fullscreen -ac -accel xv:pbuffer -accel glx:fbo &
DISPLAY=:1
exec dbus-launch --exit-with-session gnome-session

make it executable:

chmod +x /usr/bin/startxgl

create login session entry /usr/share/xsessions/xgl.desktop with the following contents:

[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Comment=Start an Xgl Session
Exec=/usr/bin/startxgl
Icon=
Type=Application

Add beryl-manager in startup programs. Click on System -> Preferences -> Sessions, choose Startup Programs tab, click on Add and type beryl-manager, click OK and Close

That's it. I would suggest you to reboot now, since AFAIK rmmod radeon && modprobe fglrx can lead to system lock. After reboot choose Xgl session in GDM. Dandy, isn't it :) ?

Radeon/AIGLX:

First what we need to do is to make sure that we don't have fglrx drivers installed. It's mandatory to remove them before going further with installation and setup of AIGLX. To uninstall them execute in root shell:

apt-get remove xorg-driver-fglrx
dpkg -P xorg-driver-fglrx

Edit your /etc/X11/xorg.conf and add following to Section Device:

Option "DRI" "true"
Option "ColorTilling" "on"
Option "EnablePageFlip" "true"
Option "AccelMethode" "EXA"
Option "XAANoOffscreenPixmaps" "true"
Option "RenderAccel" "true"
Option "AGPMode" "8"
Option "AGPFastWrite" "on"

and this to Section Section "ServerLayout":

Option "AIGLX" "true"

Create file /etc/drirc with the following content:

<driconf>
  <device screen="0" driver="r200">
   <application name="all">
    <option name="allow_large_textures" value="2" />
   </application>
  </device>
</driconf>

Add beryl-manager in startup programs. Click on System -> Preferences -> Sessions, choose Startup Programs tab, click on Add and type beryl-manager, click OK and Close

Restart X/GDM and give it a try. Slow, but smashing, isn't it :) ?

---

### Post by erik.teichmann on 2007-02-08
Well hot dang.

I popped the Edgy LiveCD in today to play with it. Ran across this little howto and decided to give it a whirl.

And what do you know. It actually worked. 5 minutes and only one CTRL-ALT-BACKSPACE later, I'm running Beryl with the open source radeon driver. On a LiveCD. 

This is really neato. I didn't realize the radeon driver had matured this much. I'd been trying the keep the 3d going on my Thinkpad R51 (that's the R250 M9) with fglrx for months. I had a little script that would have to redownload and cruft a little file into place when the driver got hosed (which was often). It's great to have a workable OSS driver for this, because I hate supporting ATI at all when they just dump support for a whole range of cards.

This. Is. Awesome.

I think I'll actually have to upgrade my system to edgy now.

--erik

---

### Post by hito1 on 2007-02-09
My xorg.conf states that the driver used is "ati", how do I change it to "radeon"?

Also, it doesn't have any of those options tha post #7 talks about, just Identifier, Driver and BusID:
```

Section "Device"
	Identifier	"ATI Technologies, Inc. RV280 [Radeon 9200 SE]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
```

Thanks. :)

---

### Post by VCSkier on 2007-02-13
just backup the file, and then edit the file carefully.  beware though, alot of people have problems w/ acceleration w/ radeon on your card...  let us know how it works though.

---

### Post by Werre on 2007-02-22
> **Belibem said:**
> Radeon open source driver, aiglx, and Beryl

Thanks. Seems to work on HP nc8000 laptop (9600 mobility).
Much much slower than fglrx, but no need for xgl kludges any more.

I have to try to tune it to get acceptable performance but will stick to the open source driver.

---

### Post by nardis_Miles1 on 2007-03-04
I have beryl-xgl working on a compaq presario laptop (amd64 architecture (turion) with onboard ati radeon express 200M, running the ATI linux driver). Because this is a 64 bit machine, I have not had the white screen issue, although my children did on theirs (fixed)

At this point, I'm working on improving the set of fonts available to xemacs. I have used the -fp /usr/share/fonts/X11/misc in the Xgl command (in startxgl.sh), which works, and makes xemacs workable, but barely. I tried inserting /usr/share/fonts/X11/75dpi:unscaled, Xgl croaked. I put in the Type1 path as well, this worked, but made things look much worse. Finally, I tried putting in paths to the truetype fonts and Xgl also croaked. 

Does anyone have insight into how Xgl works with various font-types?

Thanks in advance for any feedback.

---

### Post by olieviya on 2007-03-06
I have tried installing Beryl using this guide: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

But I get a fully white screen when I start up in Xgl and enable Beryl, help please? :)

```
olivia@olivia-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7145
04:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
05:04.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:05.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
olivia@olivia-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6011 (8.28.8)

```

---

### Post by Ryzzen on 2007-03-06
> **olieviya said:**
> I have tried installing Beryl using this guide: [http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html](http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html)

But I get a fully white screen when I start up in Xgl and enable Beryl, help please? :)

```
olivia@olivia-laptop:~$ lspci
(lots of stuff)
OpenGL version string: 2.0.6011 (8.28.8)

```

There's a couple different solutions to this.

1. Run Beryl using:
```
beryl-manager --no-force-window-manager
beryl-xgl --use-copy
```

or

2. Run Beryl using:
```
LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl
```

or

3. Downgrade to a previous version of Beryl:
- Open Synaptic Package Manager.
- Search for *beryl*.
- Press Ctrl + E and select version 0.1.99.2.
- Do this for **beryl**, **beryl-core**, **beryl-manager**, **beryl-plugins**, **beryl-plugins-data**, - **beryl-settings**, **beryl-settings-binding**, **libberyldecoration0** and **libberylsettings0**. Do not do this to any of the Emerald themes.

[Taken from this thread: [http://ubuntuforums.org/showthread.php?t=362381](http://ubuntuforums.org/showthread.php?t=362381) ]

Also, if you do find yourself stuck with a white screen, press Ctrl + Alt + Backspace to log out of X.

Or try Ctrl + Alt + F1 to get to a terminal, and type:

```
killall beryl

or

killall beryl-xgl
```

---

### Post by Enedok on 2007-03-06
So, after dualboot with windows and a dual reinstall of ubuntu because of ntfs problems I got my hands on [Ultimate Ubuntu Gamers Edition]("http://ubuntusoftware.info/ubuntu_ultimate_gamers/") and wiped out xp :mrgreen: 

Beryl worked the second I started the program from the meny :mrgreen: and worked flawless except some videoproblems if it was not on the top. Now thats not my problem right now since I had to install a new driver to get some of the games that followed to run better than 0.02 FPS:) I used Automatix to do that.

To bad that beryl don't follow me up on that. It runs with the small icon but no matter what settings I do under Advanced beryl options the windows flickes in the edges and goes back to normal theme.

So beryl does work, its just some settings with the driver. Has someone overcome an issue like this that can help another fellow who left windows?

---

### Post by techstop on 2007-03-10
Hi there. I used the guide from post #7 (linked to from the sticky), except I used the ati driver instead of the radeon driver, ati was already installed and working. I started beryl-manager and beryl was working great, until I rebooted. Then I got to the ubuntu splash screen, and the monitor just stayed black. I couldn't get to the tty terminals either. It seems a few other people have this as well ("Black Screen of Death").

So, I undid all the changes I made to xorg.conf, rebooted, and the desktop was now working and I could get past the splash screen where it was stuck before. I logged into the desktop, and to my surprise, beryl was working! I don't know which line it was from xorg.conf that was borked, but they all appear to be unnecessary, for me at least (I kept the original lines in there). I hope this helps someone, it was frustrating for a while there.

PS. The ATI card is a 9600XT, and the desktop seems a lot quicker and smoother than the 6600GT I have in my other computer. The nvidia card uses the latest nvidia drivers (9755). I'm a bit disappointed in the choppiness on the nvidia machine.

---

### Post by schwartzki on 2007-03-24
Ok guys, I am fairly new to beryl but I have it running on my machines (after a few kernal panics) but now the problem I am having is performance issues, choppy even tho beryl is running

In terminal beryl is showing:
bschwartzki@schwartzki-desktop:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0


Here is an copy of my xorg.conf file:

Section "Device"
	Identifier	"ATI Technologies, Inc. ATI Default Card"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
Option "DRI" "true"
Option "ColorTiling" "on"
Option "EnablePageFlip" "true"
Option "AccelMethod" "XAA"
Option "XAANoOffscreenPixmaps"
Option "RenderAccel" "true"
#Option "AGPMode "x8"
Option "AGPFastWrite" "on"
EndSection

Section "Monitor"
	Identifier	"FPD2275W"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. ATI Default Card"
	Monitor		"FPD2275W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1680x1050" "1440x1440" "1400x1050" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection

I am running a ATI Radeon X1650Pro 256MBGDDR3
System is running a gig of ram and while beryl is running performance is off.

Thanks for any help

---

### Post by schwartzki on 2007-03-25
any thoughts?

---

### Post by grindercee on 2007-04-14
I was reading and saw that some say they don't have a problem with fglrx. That is great but those that do have problems don't want to hear it unless you can help us so shut your face.

---

### Post by alan_daniel on 2007-04-14
> **grindercee said:**
> I was reading and saw that some say they don't have a problem with fglrx. That is great but those that do have problems don't want to hear it unless you can help us so shut your face.

I am one of those who got fglrx working. I can try to help. What kind of video card are you using? Also, what version of ubuntu/kubuntu?

And I know it can be frustrating to get this to work. I had been trying for over a year before I finally just stumbled into the correct answer, but it's not the fault of the people who have succeeded that you are having problems. If you ask the questions (particularly nicely), people will help.

---

### Post by patsimon12 on 2007-04-18
I have found that the open source drivers are fine for beryl, but as soon as you want to play quake3 (or other games that need OpenGL on the card) - forget it.

---

### Post by jargoman on 2007-05-10
For people who want the separate xgl login but have freezes on logout.

$ sudo gedit /etc/gdm/gdm.conf-custom

then under daemon add
AlwaysResetServer=true

---

### Post by aljaber on 2007-06-22
hello all,

I've just installed Ubuntu on my Dell 6400 computer (ATI x1400) 

I installed beryl, followed some instructions in this post and some other French Ubuntu forum, but beryl still doesn't work.

I really want it to work so if someone can help, it'll be highly appreciated :p

---

### Post by rocketbomb on 2007-08-04
[www.techindepth.net]("http://www.techindepth.net") check this

---

### Post by dbsub9 on 2007-09-06
and one more thing.... the beryl desktop only runs in 1024X768 and i a would like to be able to use 1280X800 any ideas?

Is this true?  I hate being stuck at 1024x768 as my max resolution. I was wondering what was causing this.  I just had to reinstall Ubuntu and in my prior installation I was at 1600x1200.

Thanks,
db

---

### Post by thejeswi.nk on 2007-09-13
Even I have the same problem as madelephant and Iradiatul. Does anybody have a solution?
> **madelephant said:**
> Hey everyone-

I followed the ATI guide posted by skyshard (very clear & easy to follow) and after I did the final reboot I am met by a screen of white/black/gray blocks and the loading mouse pointer.  I am stuck from here, not sure what to try next.  Guessing it might be driver related?

I'm running on a ATI Radeon XPRESS 200m card.

Most likely the same problem Iradiatul is having-

---

