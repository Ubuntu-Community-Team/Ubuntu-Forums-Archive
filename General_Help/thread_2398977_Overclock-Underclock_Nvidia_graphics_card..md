---
title: "Overclock-Underclock Nvidia graphics card."
date: 2018-08-20
forum: General Help
---

### Post by debderivs on 2018-08-20
Hi,

What programs are available to overclock/underclock and reduce fan speed for Nvidia graphics
cards on Linux?

I have found "nvclock-gtk_0.8b4+cvs20100914-5_i386.deb", but when trying to install it, apt
gives an error, it says it can´t find the package. I also tried the Software installer, but it 
doesn´t work either, it shows the Installing animation text, but afterwards I can´t find it in 
the system.

What´s wrong with this package? This is a machine with an old 9800 card which works fine
with its 340 Legacy drivers. How can I install this nvclock?

Thanks.

Regards.

---

### Post by Frogs Hair on 2018-08-20
The latest version of nvclock-gtk is for 14.04. I can't address why there were no updates after 2013. If the card has fans-speed capability nvidia-settings may have an option to control it. There are instructions for other methods to over-clock nvidia cards available with a search that require some command line configuring and would be use at your own risk. Make sure any instructions you find apply to the graphics card and current version of Ubuntu installed.

---

### Post by debderivs on 2018-08-20
Thanks for your input. 

So the installation problem is that this program is not updated... No other similar program witg a GUI? 
Hmm, command line conrtrol for something like this is, I don´t trust much... Will have a look around.

Anyway, odd there aren´t more programs capable of doing overclocking and such on Linux...

---

### Post by Yellow Pasque on 2018-08-20
> Command line control for something like this I don´t trust much...

You don't use the command line to control it. You enable "coolbits" in your xorg.conf and then the appropriate settings appear in the Nvidia Settings GUI if your card and driver support it.

For a 9800, something like this would be appropriate:
```
sudo nvidia-xconfig --cool-bits=5
```
And don't forget to log out or reboot to restart X.

---

### Post by debderivs on 2018-08-21
> **Temüjin said:**
> You don't use the command line to control it. You enable "coolbits" in your xorg.conf and then the appropriate settings appear in the Nvidia Settings GUI if your card and driver support it.

For a 9800, something like this would be appropriate:
```
sudo nvidia-xconfig --cool-bits=5
```
And don't forget to log out or reboot to restart X.


Ah, OK, I wasn´t sure what that was exactly, and didn´t have the time yet to try it. I saw somewhere some
commands and thought that every detail, and there were many, had to be executed through terminal. With
CoolBits enabled, it will be much easier. At least I hope I can lower the fan speed, and GPU and Memory 
clocks.

Thanks!

---

### Post by Frogs Hair on 2018-08-21
You should be able to see if fan speed is supported in nvidia settings . As you can see, the card I use is unsupported.

---

### Post by debderivs on 2018-08-21
I´ll have a look tonight when I can. 

Why isn´t your card supported? It should be, being a modern card. I hope my old card is. I just need it for the 
desktop and TV and video playback, not to play games at all. 

If mine is not supported either, is there another way to configure the fan? Hope so... terminal tweaking route, 
I guess.

Thanks.

---

### Post by Frogs Hair on 2018-08-21
> Why isn´t your card supported?  Though it has 2gb of memory and good video in general it's still considered an entry level card. I don't have heat problems at all though the open source  driver causes the fan to scream !  The proprietary driver is a must for this card.

---

### Post by Yellow Pasque on 2018-08-21
> **Frogs Hair said:**
> As you can see, the card I use is unsupported.

Did you set Coolbits before taking this screenshot? In this case, "Unsupported" means the fan does not report RPM. It does not necessarily mean the fan can't be controlled through PWM (i.e. you can specify a percentage of the max speed).
You should set coolbits=12, and then see if anything changes on the next boot. You may have an OC setting on the PowerMizer section and a fan control in the Thermal section. You can also use coolbits=4 if you don't want anything to do with manual clock control.

---

### Post by Frogs Hair on 2018-08-21
> **Temüjin said:**
> Did you set Coolbits before taking this screenshot? In this case, "Unsupported" means the fan does not report RPM. It does not necessarily mean the fan can't be controlled through PWM (i.e. you can specify a percentage of the max speed).
You should set coolbits=12, and then see if anything changes on the next boot. You may have an OC setting on the PowerMizer section and a fan control in the Thermal section. You can also use coolbits=4 if you don't want anything to do with manual clock control.

I've checked with other forums and with a utility on the Windows side. I don't see any heat problems anyway except with the open source driver. The temperature is consistent on both operating systems though I game much more with Windows.

---

### Post by debderivs on 2018-08-22
> **Temüjin said:**
> You don't use the command line to control it. You enable "coolbits" in your xorg.conf and then the appropriate settings appear in the Nvidia Settings GUI if your card and driver support it.

For a 9800, something like this would be appropriate:
```
sudo nvidia-xconfig --cool-bits=5
```
And don't forget to log out or reboot to restart X.


Hi,

I´ve tried this method but to no avail, CoolBits doesn´t show up nowhere.

First time I tried the command, there was an error reporting that there was no /etc/X11/xorg.conf file,
I recall... but the second time, it was created automatically and the command seemed to work, but 
after rebooting CoolBits functions didn´t show up. 

What is wrong? Something wrong with the /etc/X11/xorg.conf file?

Thanks.

---

### Post by Yellow Pasque on 2018-08-22
> What is wrong?
It's possible Coolbits doesn't support your card.

> CoolBits doesn´t show up anywhere.
You looked in the 'PowerMizer' and 'Thermal Settings' sections?

---

### Post by debderivs on 2018-08-22
Yes, looked for it everywhere, but it is missing. Hmm, the card is an old popular 9800 GTX+, so I guess it
should be supported. What else could I try? Could I have done something wrong?

Thanks.

---

### Post by Yellow Pasque on 2018-08-22
> Could I have done something wrong?
Unless you struggle with copy/paste, probably not.

>  What else could I try?
Maybe try it with cool-bits=1 or cool-bits=4 (see here for more detailed explanation: [https://wiki.archlinux.org/index.php/NVIDIA/Tips_and_tricks#Enabling_overclocking](https://wiki.archlinux.org/index.php/NVIDIA/Tips_and_tricks#Enabling_overclocking) )

>  Hmm, the card is an old popular 9800 GTX+, so I guess it should be supported.
I wouldn't make that assumption, especially if it was factory overclocked.

---

### Post by debderivs on 2018-08-25
I´ve tried a new thing: deleting the xorg.conf so the Nvidia Panel saves the X Configuration file just in case
there could be some error somewhere. Well, once saved and added the "Option         "Coolbits" "1"" line and
rebooted, this thing doesn´t work either. Tried the values 1, 4 and 5.

What´s wrong then? The value? Or perhaps, some kind of incompatibility with this card?

Here is the content of the xorg.conf file:


```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 396.24  (buildd@lcy01-amd64-004)  Wed May  2 23:28:36 UTC 2018

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Ancor Communications Inc ASUS VX239"
    HorizSync       24.0 - 83.0
    VertRefresh     50.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GTX/9800 GTX+"
    Option         "Coolbits" "1"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "TV-0"
    Option         "metamodes" "DVI-I-3: nvidia-auto-select +0+0, TV-0: 800x600 +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

### Post by #&amp;thj^% on 2018-08-25
May I ask why you use the "Coolbits" "1"
**I have two files for this.  (I have found this (the 2 files) to be needed since 16.04)**
1st is in "/etc/X11/xorg.conf"
2nd is in /etc/X11/Xsession.d/20-nvidia.conf
They are exactly the same file>>>just named differently.
Mine reads as follows:
```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 378.13  (buildmeister@swio-display-x86-rhel47-05)  Tue Feb  7 19:37:00 PST 2017

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 367.35  (builduser@rw)  Fri Jul 15 21:07:27 CEST 2016

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP w2338h"
    HorizSync       24.0 - 83.0
    VertRefresh     48.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 560 Ti"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-1"
    Option         "metamodes" "DVI-I-1: nvidia-auto-select +0+0"
    Option         "SLI" "Off"
    Option         "MultiGPU" "Off"
    Option         "BaseMosaic" "off"
   [COLOR="#FF0000"] Option         "Coolbits" "28"[/COLOR]
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Device"
    Identifier  "intel"
    Driver      "modesetting"
    BusID       "PCI:0:2:0"
    Option      "AccelMethod"  "sna"
    #Option      "TearFree" "True"
    #Option      "Tiling" "True"
    #Option      "SwapbuffersWait" "True"
EndSection
```
Please Note that I use:
**Option         "Coolbits" "28"**>>>This gives me a bit more options IE: Fan control, and Power Settings

---

### Post by debderivs on 2018-08-25
As I said, I tried values 1, 4 and 5, and because someone told me so... the reasoning for this I think it´s because mine
is an old card. I could use any value, of course, as long as it works...

Should I try value 28 as you do?

Also, I see that there is no CoolBits line in the Device section of your file, but on the Screen one... Could this make a
difference?

Thanks for your input, mate!

---

### Post by #&amp;thj^% on 2018-08-25
> **debderivs said:**
> 

Should I try value 28 as you do?

Also,[B][U] I see that there is no CoolBits line in the Device section of your file, but on the Screen one... Could this make a
difference?
[/U][/B]
Thanks for your input, mate!

Yep.!
It won't hurt anything to try value 28. as they are just hacks put there if the card is up to the task. :)

---

### Post by Yellow Pasque on 2018-08-25
> **1fallen said:**
> It won't hurt anything to try value 28.

It won't hurt, but it makes no sense on a pre-Fermi card, since it won't flip on the relevant bit for OC'ing.  Read the manual. [http://us.download.nvidia.com/XFree86/Linux-x86_64/340.107/README/xconfigoptions.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/340.107/README/xconfigoptions.html)

> I see that there is no CoolBits line in the Device section of your file, but on the Screen one..

"The following driver options are supported by the NVIDIA X driver. **They may be specified either in the Screen or Device sections** of the X config file." [http://us.download.nvidia.com/XFree86/Linux-x86_64/340.107/README/xconfigoptions.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/340.107/README/xconfigoptions.html)

---

### Post by #&amp;thj^% on 2018-08-25
> **Temüjin said:**
> It won't hurt, but it makes no sense on a pre-Fermi card, since it won't flip on the relevant bit for OC'ing.  Read the manual.

:p Yep, I did not take the time to see this: Important part **GeForce 9800 GTX/9800**
So I agree makes no sense for this card. Thanks for the catch>> I plainly over looked. ;)

---

### Post by debderivs on 2018-08-25
Hmm, if that value addresses newest cards, it probably won´t do anything. I will give it a try though, but especially
will create that copy of xorg.config in that other folder you mentioned. If this doesn´t work, I dont´t what could
be left...

---

### Post by debderivs on 2018-08-25
> **Temüjin said:**
> "The following driver options are supported by the NVIDIA X driver. **They may be specified either in the Screen or Device sections** of the X config file." [http://us.download.nvidia.com/XFree86/Linux-x86_64/340.107/README/xconfigoptions.html](http://us.download.nvidia.com/XFree86/Linux-x86_64/340.107/README/xconfigoptions.html)


OK, thanks. So this detail is actually insignificant.

---

### Post by debderivs on 2018-08-26
I´ve tried now copying the xorg.conf (though the extension was changed automatically to a date) to the folder
"etc/X11/Xsession.d/", and after rebooting, nothing changed, no new CoolBits features show up in the Nvidia
Settings Panel.

What else is left to try...?

---

