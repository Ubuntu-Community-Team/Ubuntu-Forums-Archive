---
title: "Two questions, please help."
date: 2007-05-17
forum: General Help
---

### Post by roffy on 2007-05-17
I figured I would lump these two question into one thread since I already have one other thread on here and I don't want to flood the forum. Please, keep in mind I am still a n00b and the switch from Windows has been great, but there have been some problems. The pros outweigh the cons though.

I am using Ubuntu Feisty

1. When surfing the internet, pages just seem to load slower than they do when using the same computer with XP. Especially when flash is present on the page. But even things as simple as this forum load slower. It can be a bit frustrating just because I feel it shouldn't be loading so slowly. And when visiting myspace pages (again moreso ones with a lot of flash) scrolling is a slow process.

2. Sometimes, it seems very randomly, when I boot it will boot to 640 x 480 res. and not let me change it.  I am using an old Dell we had just sitting around and it has the onboard video (bummer, I know).

---

### Post by strabes on 2007-05-17
Please open a [terminal](http://www.psychocats.net/ubuntu/terminal) and paste the output of the following command: ```
cat /etc/X11/xorg.conf
```

The slow scrolling problem in firefox may be because you don't have the proper video card drivers installed. See the "Install Video Card Drivers" link in my signature to learn how to do this for your card.

---

### Post by Pollywoggy on 2007-05-17
I have that type of problem (the first problem mentioned) sometimes with Konqueror, but not with Firefox, Flock, or Opera.  Have you tried one of those?

I am not sure what is causing the second problem you mentioned, perhaps you might get better performance if you install an older Nvidia type graphics card.

Maybe someone can help if you post your /etc/X11/xorg.conf

---

### Post by roffy on 2007-05-17
I have had the same problem with both firefox and opera.

Here is the output though:

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
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
        Load    "type1"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
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
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "DELL M992"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "DELL M992"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by roffy on 2007-05-17
...Any more help, please.

---

### Post by ramjet_1953 on 2007-05-18
Often the problem with slow response when browsing can be fixed by disabling what is called [COLOR="Blue"]ipv6[/COLOR].

in a terminal copy and paste the following:

[COLOR="Red"]gksu gedit /etc/modprob.d/bad_list[/COLOR]

When the editor opens, copy and paste this in:

[COLOR="Red"]alias net-pf-10 off[/COLOR]

Save the file and exit.

Re-boot and you should notice a difference in response.

The reason for this is because ipv6 is hardly ever used and it conflicts with ipv4, which is by far the most common. This conflict slows things down and can even cause crashes.

Regards,
Roger :cool:

---

### Post by bobplano on 2007-05-18
the slowdown especially on pages with flash might mean you don't have the newest version of flash. go to about : plugins (without the spaces) and scroll down to where it says flash. if you don't have version 9 then you might try upgrading

---

### Post by hikaricore on 2007-05-18
I had alot of trouble with my old integrated intel chip and firefox/flash.  I suggest changing your defailt depth. to 16bit and relogging.  Trust me it really will make a difference.

> Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
Monitor "DELL M992"
DefaultDepth **16**

---

### Post by roffy on 2007-05-18
> **hikaricore said:**
> I had alot of trouble with my old integrated intel chip and firefox/flash.  I suggest changing your defailt depth. to 16bit and relogging.  Trust me it really will make a difference.

When it was at 16 flash videos weren't working at all. 

But after doing the suggestion above (there was a typo but I got it figured out), surfing was faster with Opera but flash was still a bit sketchy, but I moved back to firefox and it's working much smoother now.

Thanks guys.

---

### Post by Pollywoggy on 2007-05-18
> **ramjet_1953 said:**
> Often the problem with slow response when browsing can be fixed by disabling what is called [COLOR="Blue"]ipv6[/COLOR].

in a terminal copy and paste the following:

[COLOR="Red"]gksu gedit /etc/modprob.d/bad_list[/COLOR]

When the editor opens, copy and paste this in:

[COLOR="Red"]alias net-pf-10 off[/COLOR]

Save the file and exit.

Re-boot and you should notice a difference in response.

The reason for this is because ipv6 is hardly ever used and it conflicts with ipv4, which is by far the most common. This conflict slows things down and can even cause crashes.

Regards,
Roger :cool:

Did you mean that 
'alias net-pf-10 off' should replace 'alias net-pf-10 ipv6' in /etc/modprobe.d/aliases  ?

That is how I would have done it, but I might be wrong.
I am also not sure whether 'sudo update-modules' should be run after making the change.

Thanks for the info, I would not have thought to disable ipv6 to solve the slow browsing problem.

---

