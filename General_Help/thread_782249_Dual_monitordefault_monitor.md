---
title: "Dual monitor/default monitor"
date: 2008-05-04
forum: General Help
---

### Post by ep3w on 2008-05-04
I have been running two monitors on my laptop with Ubuntu for sometime with two different resolutions.  I thought hardy was supposed to let you easily enable them using the screen resolution applet but that didn't recognize my 2nd display at all. Not a big deal, I easily enabled it using nvidia-settings and they work great, the screen resolution applet recognizes them as one big screen despite the different resolutions (1680x1050 and 1280x1024 so the vertical is not off by much). Whenever I boot up and go to logon, the login window is always on my 2nd display and I have found no way around this.  Is there anyway to tell it the other is my primary one? It is marked as that in nvidia-settings. Also, any reason why when I only use one display and so the login window is one the widescreen one, the little circles that show up for your password are cut off at the bottom?

---

### Post by chewearn on 2008-05-05
Edit /etc/X11/xorg.conf manually.

Under Section "Device", you need to add something similar to the lines below:

```

Option  "TwinViewXineramaInfoOrder" "DFP, CRT"
Option "UseDisplayDevice" "DFP, CRT"
Option "TwinViewOrientation" "DFP LeftOf CRT"

```

Note:
You need to replace the "DFP" and "CRT" with the ones found in your xorg.conf.

---

### Post by ep3w on 2008-05-05
Thanks, that worked great! I switch between running dual and single monitors alot when I take my notebook to class using nvidia-settings. Should i tell it to merge with my existing so it doesn't overwrite what i just added? I would assume leaving that part in while running a single monitor would not effect anything since it is just telling it to use my notebook screen as default anyways, but correct me if I am wrong.

---

### Post by chewearn on 2008-05-05
Yeah, the settings will probably be ignore if you use a single screen only.

However, if you switch single to dual screens frequently, it would be better to create multiple xorg.conf (test it to make sure it's working) for each scenario.  Put these xorg.conf files somewhere.  Subsequently, a simple file copy instruction and a Xorg restart will be sufficient to switch the configuration.

Advantage: it's always possible to switch instantly.
Drawback: no dynamic switching, need Xorg restart.

---

### Post by ep3w on 2008-05-05
That was the type of setup I had before I formatted.  My buddy helped me write a simple script so I could easily switch between the two. Now I just need to remember how I did it...Thanks for the help!

---

### Post by riiidaa on 2008-10-06
> **chewearn said:**
> Edit /etc/X11/xorg.conf manually.

Under Section "Device", you need to add something similar to the lines below:

```

Option  "TwinViewXineramaInfoOrder" "DFP, CRT"
Option "UseDisplayDevice" "DFP, CRT"
Option "TwinViewOrientation" "DFP LeftOf CRT"

```

Note:
You need to replace the "DFP" and "CRT" with the ones found in your xorg.conf.

Hi chewearn

I just set up Mythbuntu 8.04 yesterday and have a 2 screen setup. It's almost how I want it, running separate X screens with Xinerama enabled. However my problem is similar to the OP.

I have my 32" Bravia LCD (CRT-1) plugged in to my dvi port and the old 17" samsung monitor (CRT-0) plugged in to the regular vga port on my nvidia card, gpu0.

Trying to have linux see my 32" (CRT-1) as the default monitor, but linux wants to use the 17" for things like login - so I'm trying your advice but am a bit stuck...

You say to paste the 3 lines into the "Device" section...

Here's an extract from my xorg.conf
> Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GS"
    BusID          "PCI:5:0:0"
    Screen         0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 GS"
    BusID          "PCI:5:0:0"
    Screen         1
EndSection


Where exactly should I put it? Sorry I'm a bit green at this.

Also you say to replace* DFP* and* CRT *with what I have in the conf but what on your setup are these values labeled? For example in my conf I have:

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung S/M 753DF"

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "SONY TV"

So I'm wondering if in your setup if DFP is a ModelName an Identifier or some other label like my CRT-1 and 0?

Thanks in advance for any help,

---

### Post by chewearn on 2008-10-06
hi riiidaa

You have a different problem.  The previous fix apply only if you use Twinview dual screens.  For "Separate X screen" you do this:

Under Section "ServerLayout", add these two lines:
```
screen 0    "Screen0" 0 0
screen 1    "Screen1" rightof "Screen0"
```

The "Screen0" and "Screen1" labels must match the Identifier of Section "Screen".

---

### Post by riiidaa on 2008-10-06
Thanks chewearn, I got jack of tinkering with stuff on my own so chickened out and swapped the cables over for an easy way out, but I shall try what you've suggested in a few hours and hopefully that will solve it,:)

Have made do using a dvi to vga adaptor for the 2nd gpu output til now but if your tweak works it means I will be able to go out and buy a dvi cable for the bravia and be 100% happy that my multiple o/s's will accept it as default in the dvi port- will let you know.

---

### Post by alrag on 2008-10-24
> **ep3w said:**
> I have been running two monitors on my laptop with Ubuntu for sometime with two different resolutions.  I thought hardy was supposed to let you easily enable them using the screen resolution applet but that didn't recognize my 2nd display at all. Not a big deal, I easily enabled it using nvidia-settings and they work great, the screen resolution applet recognizes them as one big screen despite the different resolutions (1680x1050 and 1280x1024 so the vertical is not off by much). Whenever I boot up and go to logon, the login window is always on my 2nd display and I have found no way around this.  Is there anyway to tell it the other is my primary one? It is marked as that in nvidia-settings. Also, any reason why when I only use one display and so the login window is one the widescreen one, the little circles that show up for your password are cut off at the bottom?

Hi there, i have a similar problem, i used to have a login screen and after some updating, i now have nothing, i,m blindly login in, by typing user name and password when i hear the drum sound of the login screen. 

By using an slightly bigger monitor, i can see the login screen.
Question, How can I change the resolution of the login screen in ubuntu 8.04, so i can recover it?

Any help would be appreciated

---

### Post by chewearn on 2008-10-25
> **alrag said:**
> Hi there, i have a similar problem, i used to have a login screen and after some updating, i now have nothing, i,m blindly login in, by typing user name and password when i hear the drum sound of the login screen. 

By using an slightly bigger monitor, i can see the login screen.
Question, How can I change the resolution of the login screen in ubuntu 8.04, so i can recover it?

Any help would be appreciated


Edit xorg.conf:
```
gksudo gedit /etc/X11/xorg.conf
```Go to Section "Screen", SubSection "Display"; remove all entries with resolution not supported by your monitor.

---

### Post by Tyndarus on 2011-09-13
Hello,

sorry for bringing this old topic back to life...
I've got the same problem as ep3w: login screen keeps on appearing on my second monitor.
(i'm running ubuntu 10.04)

i've been retyping some stuff in xorg.conf, but nothing seems to work.
When i start up my PC, first screens appear on primary monitor (DFP-0), then it switches to other monitor for login (DFP-1), after logging in, my panels (bar with applications/places/system) are on my primary monitor again (as they should be because of     Option         "TwinViewXineramaInfoOrder" "DFP-0, DFP-1").

Is this because of wrong dual screen settings (see below) or has the login screen it's own setting for choosing monitor?

my xorg.conf file (srry for full text, dunno how to put it as 'code')

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Dell"
    ModelName      "E198WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Medion"
    ModelName      "MD 20144"
    HorizSync       29.0 - 81.0
    VertRefresh     55.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8600 GT"
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0, DFP-1"
    Option        "UseDisplayDevice" "DFP-0, DFP-1"  
    Option         "TwinViewOrientation" "DFP-1 LeftOf DFP-0"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "metamodes" "DFP-0: nvidia-auto-select, DFP-1: nvidia-auto-select"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

gtz,
Tyndarus

---

### Post by Tyndarus on 2011-09-13
... and another question,
do my inputdevices have to be mentioned in xorg.conf?

on all other forums/topics nobody seems to mention anything about input devices in xorg.conf

gtz,
tyndarus

---

### Post by chewearn on 2011-09-14
I think this line:
```
Option         "TwinViewOrientation" "DFP-1 LeftOf DFP-0"
```Should be:
```
Option         "TwinViewOrientation" "DFP-0 LeftOf DFP-1"
```It has been a while since I tinkered with nvidia in ubuntu, so apologies if I got it wrong. :-)

Also, I think the input devices no longer need to be in xorg.conf in later Ubuntu versions, but it might be still relevant for 10.04.  It's also retained by nvidia-settings because nvidia is slow catching up.  But don't quote me on that, as I said, it has been a while.

---

