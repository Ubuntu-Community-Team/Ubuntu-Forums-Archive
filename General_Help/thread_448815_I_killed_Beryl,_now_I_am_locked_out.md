---
title: "I killed Beryl, now I am locked out"
date: 2007-05-19
forum: General Help
---

### Post by piratebill on 2007-05-19
Ok, so I was messing with my beryl settings, and changed the rendering engine from default (or was it automatic?) to xgl.....the problem is my graphics card doesn't support that and beryl locks up gnome and basically all I can do is move the mouse.  other than that the screen stays static.  The real kicker is I had beryl set NOT to go back to metacity after it crashes....so Every time I log in it locks up now and I cant do anything.  So I have 2 questions:

1.  Is there a file I can edit with Knoppix that will change the setting back?


2.  If not, I am trying to at least get my data off the drive.  By logging in as failsafe terminal I can launch gnomebaker...but the cdrom isn't detected and I cant seem to mount it.  How could I do that so I could at least burn my stuff off the drive (FYI, I was logged in as root doing all of that).  


Please help me. I dont want to loose my stuff :(

EDIT
tried to mount with command
mount -t auto /dev/cdrom /mnt/cdrom

---

### Post by octoberdan on 2007-05-19
> **piratebill said:**
> Ok, so I was messing with my beryl settings, and changed the rendering engine from default (or was it automatic?) to xgl.....the problem is my graphics card doesn't support that and beryl locks up gnome and basically all I can do is move the mouse.  other than that the screen stays static.  The real kicker is I had beryl set NOT to go back to metacity after it crashes....so Every time I log in it locks up now and I cant do anything.  So I have 2 questions:

1.  Is there a file I can edit with Knoppix that will change the setting back?


2.  If not, I am trying to at least get my data off the drive.  By logging in as failsafe terminal I can launch gnomebaker...but the cdrom isn't detected and I cant seem to mount it.  How could I do that so I could at least burn my stuff off the drive (FYI, I was logged in as root doing all of that).  


Please help me. I dont want to loose my stuff :(

EDIT
tried to mount with command
mount -t auto /dev/cdrom /mnt/cdrom

You could try looking for a backup of /etc/X11/xorg.conf in /etc/X11/ (xorg.conf.bk or something) or remove beryl with apt-get
```

sudo apt-get remove beryl

```
Perhaps also post your xorg.conf?

---

### Post by piratebill on 2007-05-19
where would I find xorg?

EDIT:
never mind, I am retarded

---

### Post by piratebill on 2007-05-19
tried to remove beryl....no effect.

---

### Post by octoberdan on 2007-05-19
Can you please post the result of 
```

ls /etc/X11/

```

---

### Post by piratebill on 2007-05-19
I will post it, but it will take a minute to type out

---

### Post by piratebill on 2007-05-19
Section "Files"
 font path "/usr/share/X11/fonts/misc"
 FontPath "/usr/share/X11/fonts/cyrillic"
 FontPath "/usr/share/X11/fonts/100dpi/:unscaled"
 FontPath "/usr/share/X11/fonts/75dpi/:unscaled"
 FontPath "/usr/share/X11/fonts/Type1"
 FontPath "/usr/share/X11/fonts/100 dpi"
 FontPath "/usr/share/X11/fonts/75 dpi"
 FontPath "/usr/share/X11/fonts/misc"
#path to fonts
 FontPath "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSelection


Section "Module"
Load        "i2c"
Load        "bitmap"
Load        "ddc"
Load        "extmod"
Load        "freetype"
Load        "glx"
Load        "int10"
Load        "type1"
Load        "vbe"
Load        "dri"
Load        "dbe"
Load        "glx"

EndSelection


Section "InputDevice"
Identifier       "Generic Keyboard"
Driver     "kbd"
Option    "CoreKeyboard"
Option    "XkbRules"    "xorg"
Option    "XkbMode1"   "pc105"
Option    "XkbLayout"   "us"
Option    "XkbOptions"   "lv3:ralt_switch"

EndSelection

Section "InputDevice"
Identifier    "Configured Mosue"
Driver      "mouse"
Option     "CorePointer"
Option    "Device"               "/dev/input/mice"
Option   "Protocol"           "ExplorerPS/2"
Opton   "ZAxisMapping"                    "4 5"
EndSelection


###I have to leave for a wedding, so I am only going to put the graphics driver settings next

Section Device
Identifer  "Intel Corpation 82852/855GM Integrated Graphics Device"
Driver    "i810"
BusID  "PCI:0:2:0"
Option "XAANoOFFscreenPixmaps"
EndSelection

Moniter
option DPMS
HorizSync 28-64
VertSync  43-60




Screen 
All modes are 1280x800



Section DRI
mode 0666
EndSection

Section DRI
Mode 0666
EndSection

its in there twice.

I can post all the parts I missed when I get back.  Sorry for the inconvenience.

---

### Post by patrickfromspain on 2007-05-19
Go to a failsafe terminal and remove the folder **.**beryl from your home. That should do it.

Also, under ~/.config/autostart you have autostart apps. If the above doesn't work, remove the beryl stuff from there.

A last try, if none of the above works: sudo apt-get remove beryl-manager

---

### Post by piratebill on 2007-05-19
I can log in now after I removed the beryl manager.  But, when I reinstall the manager, the issue persits again.  Is there a folder that stores the beryl-manager settings?  How can I get beryl back?

---

### Post by piratebill on 2007-05-20
I fixed it.

typed

rm .beryl-managerrc


Thanks everyone!!

---

