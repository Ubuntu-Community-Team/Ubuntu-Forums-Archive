---
title: "Screen Resolution: 1440x900?"
date: 2007-04-22
forum: General Help
---

### Post by Askeptykal on 2007-04-22
So, I just installed Ubuntu, and so far I'm liking what I'm seeing. However, where my screen resolution SHOULD be set to 1440x900, that option isn't available. 1024x768 is the highest I can get, and it is just killing my eyes. I've been searching for a way to set the resolution to 1440x900, but I'm totally new to Linux, and I have no idea what anybody is talking about. Could anybody please show me, in plain English, what I can do to remedy this problem?

---

### Post by pebo on 2007-04-22
Look at this thread: [http://ubuntuforums.org/showthread.php?t=410107&highlight=1440x900](http://ubuntuforums.org/showthread.php?t=410107&highlight=1440x900)
Good luck

---

### Post by Askeptykal on 2007-04-22
That didn't help at all... it just says to add your desired screen resolution to all of the Modes lines... but I can't do that. All of my modes say the following:

Modes "1440x900"

But that's the screen resolution I'm trying to get. I'm really not understanding any of this at all.

---

### Post by hikaricore on 2007-04-22
I'm guessing this is a laptop with an intel video chipset or something of the sort?
There are known issues with odd video modes and there are possible solutions for them.  You should probably let us know more about your hardware.

---

### Post by jcmkk3 on 2007-04-22
What sort of graphics card are you using?  If you are using an nVidia card like I am you can use the following procedure:

- Go to System -> Administration -> Restricted Drivers Manager
- Enable your graphics card
- Reboot
- That may do it, but if it doesn't follow the next steps.
- Add >         Option "ExactModeTimingsDVI"
                            Option "ModeValidation" "NoDFPNativeResolutionCheck"
 to the device section of /etc/X11/xorg.conf
- You'll have to restart X to make the new settings take effect Ctrl-Alt-Backspace
- If the resolution is now not correct, run nvidia-settings and change the resolution to 1440x900

---

### Post by specv on 2007-04-22
look into 915resolution there are plenty of howto's and that will fix your problem

---

### Post by Askeptykal on 2007-04-22
Like I said, I'm new to Linux/Ubuntu, so I'm not really sure where I can really find the hardware information you're looking for. The Device Manager doesn't tell me very much... if it helps, my video card is a Mobile 945GM/PM/GMS/940GML Express Integrated Graphics Controller.

---

### Post by Askeptykal on 2007-04-22
> **specv said:**
> look into 915resolution there are plenty of howto's and that will fix your problem

I did look into that, but it only confused me more :roll:

---

### Post by The Creator on 2007-04-22
you could run the command 

"sudo dpkg-reconfigure xserver-xorg" into the terminal and select the resolutions you want. Use caution, do not select them all because the login screen uses the highest one available and you do not want to blow up your monitor. Just hit enter until you get to the resolution part and enter after and dont worry about the rest of the dialogs.

---

### Post by Askeptykal on 2007-04-22
> **The Creator said:**
> you could run the command 

"sudo dpkg-reconfigure xserver-xorg" into the terminal and select the resolutions you want. Use caution, do not select them all because the login screen uses the highest one available and you do not want to blow up your monitor. Just hit enter until you get to the resolution part and enter after and dont worry about the rest of the dialogs.
I've tried that before. On the third screen, I get the following dialog:

> Users of PowerPC machines, and users of any computer with multiple video  &#8593;  
 &#9474; devices, should specify the BusID of the video card in an accepted        &#9646;  
 &#9474; bus-specific format.                                                      &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; Examples:                                                                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;  ISA:1                                                                    &#9618;  
 &#9474;  PCI:0:16:0                                                               &#9618;  
 &#9474;  SBUS:/iommu@0,10000000/sbus@0,10001000/SUNW,tcx@2,800000                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; For users of multi-head setups, this option will configure only one of    &#9618;  
 &#9474; the heads.  Further configuration will have to be done manually in the X  &#9618;  
 &#9474; server configuration file, /etc/X11/xorg.conf.        
 You may wish to use the "lspci" command to determine the bus location of  &#9618;  
 &#9474; your PCI, AGP, or PCI-Express video card.                                 &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; When possible, this question has been pre-answered for you and you        &#9646;  
 &#9474; should accept the default unless you know it doesn't work. 

I press Enter on this screen and nothing happens...

---

### Post by The Creator on 2007-04-22
have you rebooted after?

---

### Post by Askeptykal on 2007-04-22
Yes. Nothing.

---

### Post by The Creator on 2007-04-22
did you try editing your xorg.conf file? if yes then i am stumped... sorry.

---

### Post by Askeptykal on 2007-04-22
I've looked into editing it, but I really have no idea what to change.

---

### Post by The Creator on 2007-04-22
you should see somthing about resolutions in the file somewhere and it should start listing resolutions you have access to. Just in the same format add the desired resolution to the file using a text editor.

If you upload the contents of your file and post it i will even edit it for you :)

---

### Post by Askeptykal on 2007-04-22
```
Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-72
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    16
        SubSection "Display"
                Depth           1
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

---

### Post by The Creator on 2007-04-22
this is already properly formatted. it should work... i am lost now. i am more of a os x guru who can get around in the linux terminal due to the fact that they are both unix based.

---

### Post by hikaricore on 2007-04-22
I'm not really familiar with your graphic chipset, but from what I know of intel laptops, I really believe the solution to the issue would be the 915resolution package.
Even if it confuses you, you really need to look further into that option because as far as any of us can tell your xorg.conf file is flawless.

---

### Post by The Creator on 2007-04-22
i second that.

---

### Post by ashz on 2007-04-22
follow this guide...

[http://knowledge76.com/index.php/Resolution_1440x900_with_Intel_945GM](http://knowledge76.com/index.php/Resolution_1440x900_with_Intel_945GM)

TFFG = Thank F^&K For Google!!

Cheers
Ash

---

### Post by dcstar on 2007-04-22
Here are the relevant lines from my xorg.conf file that I use to get 1440x900 (at 60Hz & 75Hz):
```

Section "Monitor"
	Identifier	"BenQ FP92W"
	Option		"DPMS"
	HorizSync	30-83
	VertRefresh	56-76
[B]	Modeline "1440x900_60.00"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
	Modeline "1440x900_75.00"  136.49  1440 1536 1688 1936  900 901 904 940  -HSync +Vsync[/B]
EndSection
```
```

.........
	SubSection "Display"
		Depth		24
		Modes		**"1440x900"** "1024x768" "800x600" "640x480"

	EndSubSection
```

You may find that adding these helps with your issue.

---

### Post by Askeptykal on 2007-04-22
Uhh... well now something's wrong. I can't seem to open up the xorg.conf file anymore... if I open try using the terminal, the termal shows nothing. When I try to open it using the Text Editor, it can't find the file if I type in the name, but if I find it on a list and open it that way, it opens the file as read-only... now what do I do?

---

### Post by Askeptykal on 2007-04-22
Oops, nevermind, I figured out what I was doing wrong. My bad.

dcstar, still didn't do it. I guess I'll get to work on the 915resolution package.

---

### Post by Askeptykal on 2007-04-22
I finally got it!

Who would have guessed that it would have been as simple as typing ```
sudo apt-get install 915resolution
``` into the terminal? Now I'm happy, and my eyes don't hurt anymore!

Thanks for your help, everybody! I really appreciate it!

---

### Post by ashz on 2007-04-22
lmao its what we have all been telling u all along..finally u did it :P.. seriously though i understand its still all a little daunting to me!!

---

