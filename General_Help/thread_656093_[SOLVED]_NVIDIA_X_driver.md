---
title: "[SOLVED] NVIDIA X driver"
date: 2008-01-02
forum: General Help
---

### Post by ant1060 on 2008-01-02
Hi everyone.

Happy New Year :)

I have searched high and low to find a solution to this. There is also no luck on Google although some other people have also been experiencing the same problem.

I am using the NVIDIA driver ( I see the NVIDIA screen on startup) and the driver is marked as being "nvidia" in my xorg.conf. However, when I want to start up the gui nvidia-settings, I keep receiving the error message :

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

I have restarted the system any number of times, but no luck.  It means I am not able to get into the nvidia settings to enable TwinView and dual monitor display.

Can anyone help please? Many thanks in advance.

---

### Post by Nunu on 2008-01-02
Have u ran nvidia=xconfig under root yet, I know this is a stupid question but i had the same thing till i did that and it resolved the issue. My two LCD's have never been happier.

---

### Post by fenixartzz on 2008-01-02
i dont know if this will be of much help but thing i observed was 
when i did apt-get nvidia-glx-new it removed nvidia-settings or whatever is their config gui app
and when i try to isntall settings app it removes nvidia-glx-new
may be its issue with you too that you might not be having the settings app

---

### Post by Nunu on 2008-01-02
The reason for that is because it is a newer driver then the one that ships with the distro. thats why it removes it when you install the "new" driver. 

Ok then what you need to do to get the nvidia drivers working fine and dandy is install nvidia-glx-new. After it is installed go to the restricted driver manager and enable it in there. by default it will be disabled. The machine will then ask to reboot. once you have logged in again you will get a message saying that the driver you installed will not be supported. don't worry to much about that. Next go to terminal and type in sudo -s. It will ask you for the password to continue. 

after you logged in as root. just go nvidia-xconfig. it will show you some lines in the terminal. wait for the command prompt and then type in nvidia-settings. the nvidia display settings will pop up and you can then enable the duel screens from there.

---

### Post by Mr Fredrick on 2008-01-02
Hi Nunu,

First, thanks for your help!

I have the exact same problem as the OP and I have tried out the steps as you outlined to fix it but still I get a Dialog telling me that the nVidia Drivers are not installed when I attempt to run nvidia-settings (as root). However, when I check the Restricted Driver Manager its says that the driver is installed and enabled!!

Is there any other way I can overcome this problem?

Also, this is my output when I run "compiz" in a terminal:

me@me-laptop:~$ compiz
Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
Enabling Xgl with nVidia drivers...
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
/usr/bin/compiz.real (cube) - Warn: Failed to load slide: freedesktop

---

### Post by Nunu on 2008-01-02
No Problem at all. Always glad to help. If you run nvidia-xconfig before you run nvidia-settings do you get any error messages? This is what i struggled to get right. i never ran xconfig so it does not update the XORG.CONF file. 

Remember to run nvidia-xconfig while you are logged on as root.

---

### Post by Mr Fredrick on 2008-01-02
Right, I just went through everything again:

1- logged on as root (sudo -s)
2- ran "nvidia-xconfig"
3- ctrl+alt+backspace (to reboot xserver)
4- logged on as root (sudo -s)
5 - ran "nvidia_settings"

got the following message in a dialog box:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

Any thoughts?

PS. I appears that my settings are not being persisted, if you know what I mean.

---

### Post by Nunu on 2008-01-02
No sorry that is new one to me, i am leaving work in the next hour, i will play with it on my machine at home as work has sentenced me to a lifetime of MS.  Could you maybe post your  XORG.CONF content in this post so that i can have look at it.  Like i said i don't have an ubuntu box with me but as far as i know it should be under /etc/X11.  I will post back here if i find something that could help.

---

### Post by Nunu on 2008-01-02
> **Mr Fredrick said:**
> Right, I just went through everything again:

1- logged on as root (sudo -s)
2- ran "nvidia-xconfig"
3- ctrl+alt+backspace (to reboot xserver)
4- logged on as root (sudo -s)
5 - ran "nvidia_settings"

got the following message in a dialog box:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

Any thoughts?

PS. I appears that my settings are not being persisted, if you know what I mean.

Sorry Just one thing did you only restart X or rebooted the machine completely from scratch? Sometimes by just restarting X it won't load the new drivers. also remember to keep a backup copy of your XORG.CONF before changing display settings, just in case.

---

### Post by Mr Fredrick on 2008-01-02
OK, I shall post my xorg.conf and await your reply.

Note: Its getting late here and already past my bedtime, your behind us, so maybe this matter can wait until tomorrow, thats OK with me.

and thanks.

---

### Post by Mr Fredrick on 2008-01-02
Here is the output from running "cat /etc/X11/xorg.conf"

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:29:35 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 84.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G72M [GeForce Go 7400]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [GeForce Go 7400]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050"
    EndSubSection
EndSection

---

### Post by ant1060 on 2008-01-02
Hi Nuno,

I would also like to thank you for your help!

Just like Mr Frederick, I am continuing to have identical problems.  I followed your ideas exactly, ran (as root) nvidia-xconfig and I still am getting the same error message as at the outset.  "You do not appear to be......" (see my first post).

The nvidia-settings gui will not start to work and so I am still unable to access my TwinView settings etc.

Any more ideas?

Thanks again so much for your time.:)

---

### Post by Mr Fredrick on 2008-01-02
ant1060,

I would help if you posted Nuno the output of your xorg.conf too.

---

### Post by ant1060 on 2008-01-02
Hi Nunu & Mr Frederick,

Here is the outcome of my cat /etc/X11/xorg.conf in case it helps.  As you see, it is very similar to Mr F's and seems to have the correct nvidia driver loaded.....

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Thu Dec 13 19:09:35 PST 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc101"
    Option         "XkbLayout" "belgium"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G72M [Quadro NVS 110M/GeForce Go 7300]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1280x800"
    EndSubSection
EndSection

---

### Post by milan2008 on 2008-01-02
Try using this driver install script and see if it works better:
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Mr Fredrick on 2008-01-02
Well I didn't go to bed, I stayed up and gave it one last try with Envy!!

I did this with fear and trepidation since I am a complete Ubuntu newbie and I wasn't sure what it would do, but it is a very impressive piece of software. So thanks for your advice and program, milan2006. 

However, although it placed two new menu items in my Applications>System Tool's menu, I still get the original error message when I attempt to run "Nvidia Settings" and running "compiz" at the command line still reports that the driver is missing.

Note: I think that is is actually installed but somehow it just doesn't think so!!

And so, to bed.

---

### Post by Nunu on 2008-01-02
Sorry to hear that, Here is my xorg.conf...

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder3)  Wed Sep 12 14:30:30 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 64.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Proview 789"
    HorizSync       30.0 - 80.0
    VertRefresh     60.0 - 75.0
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
EndSection

[B]Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GS"
EndSection[/B]

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Modes      "1280x1024" "1280x960" "1024x768" "832x624" "800x600" "720x400" "640x480" "256x256"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "metamodes" "CRT-0: 1280x1024 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1280x960 +0+0, CRT-1: nvidia-auto-select +1280+0; CRT-0: 1024x768 +0+0, CRT-1: nvidia-auto-select +1024+0; CRT-0: 832x624 +0+0, CRT-1: nvidia-auto-select +832+0; CRT-0: 800x600 +0+0, CRT-1: nvidia-auto-select +800+0; CRT-0: 640x480 +0+0, CRT-1: nvidia-auto-select +640+0"
EndSection


One thing that is a but of a worry is the device, both Ant1060 and Mr Fredrick have one major difference in hardware compared to mine, and that is the fact that both of you are running the go chip set which is mobile technology if I am not mistaken. Myself on the other hand is running on a desktop PC, I wonder if this could not be the cause of the problems that you are experiencing.

---

### Post by ant1060 on 2008-01-02
Thanks to everybody for trying to help.
I also used Envy and, like Mr F, still have the error message despite the configuration happening completely OK.
I should perhaps add that when I was running Feisty, I could run Twin View with no problems.
BTW, I notice you are using Xinerama, Nunu.... but we were hoping for TwinView...
Any further thoughts, anyone?
Thanks in advance.

---

### Post by Mr Fredrick on 2008-01-02
Woke up,
Got out of bed,
Dragged a comb across my head, (The Beatles)
*And then I tried fixing this problem, yet again.*

I attempted to directly edit my xorg.conf file and make this section:

[B]Section "Device"
Identifier "nVidia Corporation G72M [GeForce Go 7400]"
Driver "nvidia"
EndSection[/B]

look more like Nunu's.

To no avail, system reverted right back to primative graphics with low resolution. I've now fixed that and I'm back to 1680x1050. As I said before I'm positive that the driver is really loaded because all my desktop effects work properly, its just that both "nvidia-settings" and "compiz" don't report that it is loaded.

---

### Post by ODF on 2008-01-02
I have the same problem here with a 8800 GTS, The restricted drivers are enabled the 'new drivers' of Nvidia are also installed. Did every step in this thread but i still get this message.

```
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 
```

It was working before until I noticed it wasn't anymore. Is that possible I made this by 'trying' to make Wine and Steam work ?

The difference here is that my compiz is working.

I appreciate all the help in this thread.

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder26)  Wed Sep 12 14:29:17 PDT 2007

# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "ca"
    Option         "XkbVariant" "fr-legacy"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "Generic Monitor"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTS]"
    Driver         "nvidia"
    Option "DPI" "100 x 100"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8800 GTS]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

```

---

### Post by Mr Fredrick on 2008-01-02
Hi ODF,

> It was working before until I noticed it wasn't anymore. Is that possible I made this by 'trying' to make Wine and Steam work ?

I doubt that this has caused the problem as I have never "tried" to use either!!

Could you post the output that you get when you enter "compiz" at a prompt in a terminal.

Thanks.

---

### Post by Nunu on 2008-01-03
Reading through the Post I started thinking that maybe the driver that we download changed. I just finished building an Ubuntu Box for a relative of mine, and installed the driver for his 5200 FX. and it worked like a charm with compiz installed... kills the driver version theory. BTW he is using twin view and not a spanned desktop like i am. 

I have to be honest when i say that this one has me scratching my head.

---

### Post by Nunu on 2008-01-03
Has any one tried adding the twinview mode manually in the xorg.conf file?

---

### Post by positronic on 2008-01-03
I am in the same boat,  Trying to get a geforce 7300 gt working 

I have followed all the same steps as NUNU when I type nvidia-settings I get

You do not appear to be using the NVIDIA x DRIVER edit configuration file etc

Rebooting or restarting X doesn't load the drivers and they show as loaded in the restricted driver management

Upon a complete reboot I get the dialogue 'Ubuntu is running in low-graphics mode'
Your screen and graphics card could not be detected.   And it is in a low graphics mode

I have just gone into restricted driver management gain 

NVIDIA accelerated graphics driver (latest cards) ticked as Enabled Status 'in use'

System > Preferences > Screen resolution gives me: two resolutions 800 x 600 and 640 x 480 

The monitor I'm using Samsung syncmaster 245b should go up to 1920x1200

To re-instate I'm running gutsy (7.10) and have a geforce 7300 GT and Samsung 245b 24" monitor (in fact two of them I will move onto sharing the desktop when I get the graphics card working).

---

### Post by positronic on 2008-01-03
"[QUOTE=ant1060;4058419]Thanks to everybody for trying to help.
I also u:confused::confused::confused::confused:sed Envy and, like Mr F, still have the error message despite the configuration happening completely OK.
I should perhaps add that when I was running Feisty, I could run Twin View with no problems."

QUOTE:
"maybe I should downgrade - really don't want to
BTW, I notice you are using Xinerama, Nunu.... but we were hoping for TwinView...
Any further thoughts, anyone?"

It just doesn't seem to recognise the driver.  Maybe I should go back to the nvidia site and carry on trying to load in the package driver for the card (7300 GT).  It had dependency problems.

Can somebody please help me with this ... There are a few of us on here with the same problems (sayng proprietry drivers in use but 'safe mode' graphics.  I chose NVIDIA because the compatibility lists say it is the most compatible.

Again I am running GUTSY 7.10 on a clean install and an nvidia 7300 GT.

---

### Post by Nunu on 2008-01-03
I cannot replicate the issue i have even gone as far as to rebuild my PC to see if i can get this issue with no luck. 

I install the nvidia-new driver
Enable it
Reboot
Run Nvidia-xconfig
Restart X
Run Nvidia-settings

And it works even after installing compiz

---

### Post by Mr Fredrick on 2008-01-03
Hi positronic,

Please note that my problem isn't that the driver won't load, instead its that whenever I issue the command "nvidia-settings" or "compiz" at the prompt I'm told that it isn't loaded.

Have you tried Envy?

---

### Post by positronic on 2008-01-03
Yes I tried envy - it didn't work.

Swapped my NVIDIA card for an ATI card .. problem over - monitor now running at maximum resolution.

Thanks anyway

I do believe we were looking at the same problem

:grin:

---

### Post by FuturePilot on 2008-01-03
> **ant1060 said:**
> Hi everyone.

Happy New Year :)

I have searched high and low to find a solution to this. There is also no luck on Google although some other people have also been experiencing the same problem.

I am using the NVIDIA driver ( I see the NVIDIA screen on startup) and the driver is marked as being "nvidia" in my xorg.conf. However, when I want to start up the gui nvidia-settings, I keep receiving the error message :

"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

I have restarted the system any number of times, but no luck.  It means I am not able to get into the nvidia settings to enable TwinView and dual monitor display.

Can anyone help please? Many thanks in advance.
The problem is that you seem to be running XGL. XGL is basically a GL accelerated Xserver and it has some problems like this when using it with a Nvidia card. However you don't need XGL if you have a Nvidia card. I would just remove XGL. Are you using it for any particular reason?

---

### Post by ant1060 on 2008-01-03
Hi Future Pilot,

Thanks for replying.

Why do you believe that I am running xgl?  There's 'glx' in my xorg.conf (see p2 of these posts). What should I actually do (step by step) in your view to cure my problem?

Thanks again :)

---

### Post by FuturePilot on 2008-01-03
> **ant1060 said:**
> Hi Future Pilot,

Thanks for replying.

Why do you believe that I am running xgl?  There's 'glx' in my xorg.conf (see p2 of these posts). What should I actually do (step by step) in your view to cure my problem?

Thanks again :)

Oh sorry, my mistake. There's actually a few people having the same problem in this thread and I got some of the posts mixed up :redface: (sometimes I read too fast :p )

Ok well first lets see if you have XGL installed. Can you post the output of
```
apt-cache policy xserver-xgl
```

---

### Post by Mr Fredrick on 2008-01-03
Hi FuturePilot,

Here is the output you requested:

me@me-laptop:~$ apt-cache policy xserver-xgl
xserver-xgl:
  Installed: 1:1.1.99.1~git20070727-0ubuntu3
  Candidate: 1:1.1.99.1~git20070727-0ubuntu3
  Version table:
 *** 1:1.1.99.1~git20070727-0ubuntu3 0
        500 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Packages
        100 /var/lib/dpkg/status

Q- Why am I running XGL (you ask)?
A - Because I thougth I had to to get desktop effects going (remember I'm a complete newbie to anything Unix) and I've found the whole installation and graphics setup a little bit confusing

If I don't have to run it how do I "unload" it?

Thanks.

---

### Post by FuturePilot on 2008-01-03
> **Mr Fredrick said:**
> Hi FuturePilot,

Here is the output you requested:

me@me-laptop:~$ apt-cache policy xserver-xgl
xserver-xgl:
  Installed: 1:1.1.99.1~git20070727-0ubuntu3
  Candidate: 1:1.1.99.1~git20070727-0ubuntu3
  Version table:
 *** 1:1.1.99.1~git20070727-0ubuntu3 0
        500 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/universe Packages
        100 /var/lib/dpkg/status

Q- Why am I running XGL (you ask)?
A - Because I thougth I had to to get desktop effects going (remember I'm a complete newbie to anything Unix) and I've found the whole installation and graphics setup a little bit confusing

If I don't have to run it how do I "unload" it?

Thanks.
To remove it
```
sudo apt-get remove --purge xserver-xgl
```
Then you'll have to log out and log back in so that X gets restarted.

---

### Post by Mr Fredrick on 2008-01-03
Hi FuturePilot,

Matey..., your the best,[COLOR="Red"]** it worked**[/COLOR], so thanks (and also thanks to Nunu and the others in this thread who have tried to help).

Now many strange behaviors, such as games not running full-screen,that I have been plagued with have also been resolved. 

I always felt since my initial installation that either I had installed/loaded too many packages or too few but I couldn't figure out exactly what or which one. I've spent days glued to my machine reading up on OpenGL, compiz, XGL, Gnome, XServer, etc, etc, in and attempt to understand how the entire thing fits together,all to no avail. All I needed was one line of code from you.

Regards,

Mr Fredrick.

---

### Post by Nunu on 2008-01-04
Awesome Cakes, Thanks FP. I don't know about you but i like to build myself a little knowledge base as i go along and help or be helped resolving issues. This one is definitely going to the KB. FuturePilot your a scholar and a gentleman Many thanks. :)

---

### Post by ant1060 on 2008-01-04
Hi Future Pilot, Nunu and Mr Frederick,

My machine is now also OK and running as it should!  I have never seen the Nvidia settings manager before, so now I can explore it and get my second screen running!

BTW : how did xgl get there in the first place?  I don't ever remember installing it, and now I am worried that it will come back automatically in some update and, rather than update, will up**set** the linux-cart all over again!

THANK YOU ALL SO MUCH:)  

Best wishes to you all.
Ant (Bruxelles, Belgique)

---

### Post by Nunu on 2008-01-04
> **ant1060 said:**
> Hi Future Pilot, Nunu and Mr Frederick,

My machine is now also OK and running as it should!  I have never seen the Nvidia settings manager before, so now I can explore it and get my second screen running!

BTW : how did xgl get there in the first place?  I don't ever remember installing it, and now I am worried that it will come back automatically in some update and, rather than update, will up**set** the linux-cart all over again!

THANK YOU ALL SO MUCH:)  

Best wishes to you all.
Ant (Bruxelles, Belgique)

It shouldn't. Maybe FP can correct me if i am wrong, but from what i could find on the XGL, it will install when it does not like the driver you are using to try and get the best graphics for gnome. If you are using a configured driver and the system is happy using it, it won't change anything on it unless you tell it to and should be content running normal GL .

---

### Post by oni5115 on 2008-01-07
I'd also like to post a thanks to Future Pilot.  I was having the exact same issue on my laptop with my GeForce Go 7800 GTX.  I had compiz working and everything, but the nvidia settings just would not load for me.  Removing XGL fixed it.

---

### Post by blis102 on 2008-04-24
I was having the same problem and the fix above worked great. Now I can maximize a window in either monitor.

The only problem I found was that by removing the xgl, I can no longer get desktop effects to work.

Is there a way around this? Any ideas?

---

