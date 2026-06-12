---
title: "can't enable desktop effects"
date: 2008-05-23
forum: General Help
---

### Post by trauma1914 on 2008-05-23
I was having some problems with my graphics card since I'm new to ubuntu I was just typing stuff in to the command line. I know I remove the desktop effects. If someone could please help me out with this and keep in mind that I am new. Also when I turn my cpu on I get a message saying that I am running  in low graphics mode and before I messed with the video drivers I wasn't getting that message and I had some features of my compiz....Thanks in advance for any help

---

### Post by Forlong on 2008-05-23
What type of graphics card are you using?

---

### Post by trauma1914 on 2008-05-23
> **Forlong said:**
> What type of graphics card are you using?

ati mobility radeon x300 w/ 64MB dedicated RAM

---

### Post by Forlong on 2008-05-23
Run this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and then restart X.

Afterwards run this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

---

### Post by trauma1914 on 2008-05-23
> **Forlong said:**
> Run this:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
and then restart X.

Afterwards run this: [http://ubuntuforums.org/showthread.php?t=799070](http://ubuntuforums.org/showthread.php?t=799070)

I have ran that before I am not sure of what choices to make...Do you have any idea of how to get the desktop effects back onto my system>preferences screen

---

### Post by Forlong on 2008-05-23
Are you talking about the dpkg-reconfigure command?
The -phigh option shouldn't bother you with much questions. Just give it a try and report back if you run into any issues.

---

### Post by trauma1914 on 2008-05-23
> **Forlong said:**
> Are you talking about the dpkg-reconfigure command?
The -phigh option shouldn't bother you with much questions. Just give it a try and report back if you run into any issues.

I did it and I couldn't get past the log in page it would ask for un and pw then loop back and do it again...This is what my system gives me for my graphics chip  Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)

---

### Post by Forlong on 2008-05-23
I'm sorry, but you have to be more descriptive.
> **trauma1914 said:**
> I did it and I couldn't get past the log in page it would ask for un and pw then loop back and do it again...
What did you do exactly and what do you mean by "loop" -- does it say wrong password or does it try to log you in but fails?
And I assume by "log in page" you mean the GDM screen (the tan one with the Ubuntu logo)?
> **trauma1914 said:**
> This is what my system gives me for my graphics chip  Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
Again, what do you mean by "This is what my system gives me"?
And didn't you say it was an ATI chip?

---

### Post by trauma1914 on 2008-05-23
I'm sorry It comes to the tan screen and asks me to enter my un and pw so I can get to me desktop....Instead of logging me in the screen goes blank and it comes back up at the tan screen again asking me to enter my n and pw again.....



Someone just gave me the ati info....I used the ckeck to see if compiz would work on my system and it gave me the intel info

---

### Post by Forlong on 2008-05-23
> **trauma1914 said:**
> I'm sorry It comes to the tan screen and asks me to enter my un and pw so I can get to me desktop....Instead of logging me in the screen goes blank and it comes back up at the tan screen again asking me to enter my n and pw again.....
Can you log into the Failsafe GNOME session?
> **trauma1914 said:**
> Someone just gave me the ati info....I used the ckeck to see if compiz would work on my system and it gave me the intel info
When and how did you check that?

---

### Post by trauma1914 on 2008-05-23
> **Forlong said:**
> Can you log into the Failsafe GNOME session?

When and how did you check that?


I would need you to tell me how to log into that mode..............I checked it a few moments ago and I used :

wget [http://blogage.de/files/3847/download](http://blogage.de/files/3847/download) -O compiz-check
chmod +x compiz-check
./compiz-check

......and I get........

Gathering information about your system...

 Distribution:          Ubuntu 7.10
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
 Driver in use:         vesa
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)

---

### Post by trauma1914 on 2008-05-23
I did that in the terminal

---

### Post by jbb421 on 2008-05-23
do u have your screen connection hooked up to ur card and not in the onboard graphics port

---

### Post by trauma1914 on 2008-05-23
> **jbb421 said:**
> do u have your screen connection hooked up to ur card and not in the onboard graphics port

I'm not sure how to answer that question I have a Dell Latitude D610 lap top

---

### Post by shrimphead on 2008-05-23
can you post the output of lspci, so we can check exactly what card you have in your machine?

---

### Post by Forlong on 2008-05-23
I'm confused. Where did you get that output if you can't log in?

---

### Post by trauma1914 on 2008-05-23
> **Forlong said:**
> I'm confused. Where did you get that output if you can't log in?

I used sudo apt dpkg-reconfigure xserver-xorg and changed it back to my settings that were working...so now I'm basically back where we began

---

### Post by Forlong on 2008-05-23
OK, now post the output of
```
grep -v ^# /etc/X11/xorg.conf
```

---

### Post by trauma1914 on 2008-05-23
> **Forlong said:**
> OK, now post the output of
```
grep -v ^# /etc/X11/xorg.conf
```


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
        Option          "HorizEdgeScroll"       "0"
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
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "ati"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

        InputDevice     "Synaptics Touchpad"
EndSection

---

### Post by Forlong on 2008-05-23
> Section "Device"
Identifier "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
Driver "ati"
BusID "PCI:0:2:0"
EndSection
Open the file being root, e.g.
```
sudo gedit /etc/X11/xorg.conf
```
and change "ati" to "intel"

Save and reboot.

---

### Post by trauma1914 on 2008-05-23
> **Forlong said:**
> Open the file being root, e.g.
```
sudo gedit /etc/X11/xorg.conf
```
and change "ati" to "intel"

Save and reboot.

It went back to where it wouldn't allow me to log on to my desktop

---

