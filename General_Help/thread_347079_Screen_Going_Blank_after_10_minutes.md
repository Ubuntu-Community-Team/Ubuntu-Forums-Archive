---
title: "Screen Going Blank after 10 minutes"
date: 2007-01-26
forum: General Help
---

### Post by azazel00 on 2007-01-26
Hello again,

Im having a problem with ubuntu. The screen is going "blank" after ten minutes of inactivity. It's becoming a bit of an annoyance when Im watching movies and such.

I edited my Power Management settings and my Screensaver settings. But so far, I get the same thing. (I attached the setting screenshots)

Am I missing something? Are there any sort of advanced options?

Regards,
az

---

### Post by david_2001 on 2007-01-26
The last time that I had this problem it was due to having screen blanking enabled in the BIOS settings.

---

### Post by azazel00 on 2007-01-26
No luck.. there were 2 power management services listed in Administration -> Services.. I disabled both.. but nadda.. same thing

I also went to the mobo, and set the video setting to "Always on"... but it still goes blank. :S

---

### Post by david_2001 on 2007-01-27
That's got me stumped.  Next, I would try the following:

[LIST=1]
[*]In System | Administration | Services disable apmd but leave acpid enabled.  (My motherboard is recent, doesn't have any conflicts with acpid, and if your're using acpi there shouldn't be any need for apm.  Power management won't work without one of the two active.)
[*]Restart and go to the BIOS settings screen.
[*]Reset the BIOS settings completely, i.e. use the Load [Optimized] Defaults option, and then disable just the screen blanking option.
[*]Save and Exit the BIOS settings.
[*]If this didn't work, check that my xorg.conf is reasonable, i.e. that DPMS is enabled for my monitor but that Standby / Suspend / Off times are not specified.  You can check this without opening xorg.conf using xset:
[/LIST]

> david@darkstar:~$ xset q
[Cut]
[B]DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On[/B]
[Cut]
david@darkstar:~$ 

---

### Post by noynac on 2007-01-27
About a month ago, I began having the same problem. I did a little research and found a thread on another forum that claimed the problem had something to do with the nVidia driver. At the time, I expected that an update to Ubuntu would fix the problem but that hasn't happened. I finally decided just to put up with the blank screen.

---

### Post by azazel00 on 2007-01-27
I've been doing some testing (more like some waiting) and have been able to narrow down the problem.

It turns out that I only get this problem when I'm using my XGL session. If I log into GNOME, all works fine.

This is the xset output when Im in GNOME and, as you can see, DPMS is enabled:
```
azazel@ubuntux:~$ xset q
...
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600
...
DPMS (Energy Star):
  Standby: 1200    Suspend: 1800    Off: 3600
  DPMS is Enabled
  Monitor is On
File paths:
  Config file:  /etc/X11/xorg.conf
  Modules path: /usr/lib/xorg/modules
  Log file:     /var/log/Xorg.0.log
```

Now, when I log into my XGL session, all hell breaks loose:
```
azazel@ubuntux:~$ xset q
...
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  600    cycle:  600
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
...
Bug Mode: compatibility mode is disabled
DPMS (Energy Star):
  Display is not capable of DPMS

```

It seems like my monitor isnt detected properly or something like that.
Additionally, if you look at the pictures I have attached, you'll notice that when Im in GNOME I can configure my VGA settings, but when I log into XGL, I can't configure anything.

I guess the answer could be "stop using xgl", but I really want to resolve this, as AIGLX doesnt work properly for me.

Regards,
az

---

### Post by david_2001 on 2007-01-27
It might help with the diagnosis if you post your entire /etc/X11/xorg.conf.  The xset output you quote shows screen blanking timeouts, one of which is 600s = 10 minutes!  Compare your timeout under "Screen Saver" with the equivalent from my setup (I use the nvidia drivers for my GeForce 7100GS card but don't have anything fancy like beryl installed):
> Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
[Cut]
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On
In the meantime, I'm wondering whether you might have more than one active screen saver.  Try this in a terminal (note that there is no hyphen before the "aux"):
```
ps aux | grep saver
```
Do you get something like:
> david@darkstar:~$ ps aux | grep saver
david     5465  0.0  0.7  19816  7888 ?        Ss   17:10   0:01 gnome-screensaver
david    19343  0.0  0.0   2812   764 pts/1    S+   22:39   0:00 grep saver
david@darkstar:~$ 
or something like:
> david@darkstar:~$ ps aux | grep saver
david     5465  0.0  0.7  19816  7888 ?        Ss   17:10   0:01 gnome-screensaver
david    19383  0.4  0.2   5320  2332 ?        S    22:40   0:00 xscreensaver -nosplash
david    19397  0.0  0.0   2808   768 pts/1    S+   22:41   0:00 grep saver
david@darkstar:~$ 
(We'll deal with XGL later.)

---

### Post by azazel00 on 2007-01-27
```
azazel@ubuntux:~$ ps aux | grep saver
azazel    5351  0.0  0.2  15468  2728 ?        Ss   18:31   0:01 gnome-screensaver
azazel   10038  0.0  0.0   2800   748 pts/0    R+   20:45   0:00 grep saver

```

xorg.conf:
```
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
	Load	"bitmap"
	Load	"dbe"
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
	Option		"XkbLayout"	"us"
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
	Identifier	"NVidia FX5900XT"
	Driver		"nvidia"
	BusID		"PCI:1:0:0"
	#Option		"UseFBDev"		"true"
	Option "RenderAccel" "true"
	Option "AllowGLXWithComposite" "true"
	Option "NvAGP" "1"
	Option  "XAANoOffscreenPixmaps"
	Option "AddARGBGLXVisuals" "True"
EndSection

Section "Monitor"
	Identifier	"Envision"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVidia FX5900XT"
	Monitor		"Envision"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1024x768" "800x600" "640x480"
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

Section "Extensions"
	Option "Composite" "Enable"
EndSection
```

Thanks for helping out here, mate

az

---

### Post by david_2001 on 2007-01-28
Hmmm.  Your xorg.conf looks normal but are you sure that the HorizSync and VertRefresh ranges for your monitor are correct?  I couldn't find one with that sort of specification on the Envision website, though I didn't check all of the possibilities.  Just glancing at a monitor screen that's displaying 1280x1024 @ 60Hz will give many people - me included - a headache.  (This is, of course, just a distraction :wink:.)

Try adding the following to your xorg.conf to explicitly turn off the blanking time:
```
Section "ServerFlags"
   Option "BlankTime" "0"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection
```
If that doesn't work then:
[LIST]
[*]What do you do special in your XGL session?
[*]Are you using Compiz or Beryl?
[*]Does whichever have a screensaver plugin installed?
[*]Was the "ps aux | grep saver" run in an XGL or ordinary X session?  If the latter, can you try it in an XGL session.
[/LIST]

---

### Post by azazel00 on 2007-01-28
I am using Beryl on XGL, due to problems I had previously with AIGLX. The problem occurs when Im using XGL (either on its own or with beryl started). I finally decided to scratch XGL and go back to AIGLX. It's working properly so far. No blank screens or anything.

I guess for the time being, it's my best option.

Thanks for the advise,
azazel

---

### Post by GaryAndersonMissed on 2007-01-29
Just posting to say thank you to David_2001.

I am running my xgl session on :1.... and inserting that section into xorg fixed my issue.

Thanks again.

---

### Post by david_2001 on 2007-01-29
Excellent! 8-)

---

### Post by david_2001 on 2007-01-29
> **azazel00 said:**
> I am using Beryl on XGL, due to problems I had previously with AIGLX. The problem occurs when Im using XGL (either on its own or with beryl started). I finally decided to scratch XGL and go back to AIGLX. It's working properly so far. No blank screens or anything.

I guess for the time being, it's my best option.

Thanks for the advise,
azazel

Sometimes it works, sometimes we just have to wait a little before it works but that's just Linux :(.

---

### Post by feanil on 2007-02-12
I'm using XGL with Beryl and and your snippet for the server flags settings fixed my problems.  Thanks David

---

### Post by steeef on 2007-03-25
Another thank you to David. I triple-checked all power management options before I tried this, and it works like a charm. Thanks!

---

### Post by iamajd on 2007-04-10
Finally!!
A solution!
Thank you so much David!

---

### Post by shanepardue on 2007-04-13
That method disables my monitor from ever powering off and the screensaver works but it's behind 
the panels so my screen isn't really locked. It does disable blanking, but causes even more 
problems. I know it's an XGL issue as it doesn't happen in a normal x session.

Any tips are greatly appreciated!

---

### Post by maximebuy on 2007-10-29
I have the same problem: the screen turns blank exactly after 10 minutes, the setting of gnome screen saver and gnome power manger make no change. My system is 7.10 and Compiz is actived by using xgl. I check the xorg.conf file, the dpms is enable. So I add the option words from david_2001. It works! Thanks! But i cannot use gnome power manger to set the time to turn off the display. Anyone has idea?

---

### Post by TRANQU111TY on 2008-01-28
I'm in the same boat with you guys. I'm no expert but could you perhaps change the BlankTime value to say perhaps 3600 to make the screen blank after an hour instead of 10 minutes?

```
Section "ServerFlags"
   Option "BlankTime" "3600"
   Option "StandbyTime" "0"
   Option "SuspendTime" "0"
   Option "OffTime" "0"
EndSection
```

I'm going to try it out.

---

