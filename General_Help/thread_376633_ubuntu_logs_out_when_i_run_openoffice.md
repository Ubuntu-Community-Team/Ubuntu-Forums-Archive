---
title: "ubuntu logs out when i run openoffice"
date: 2007-03-05
forum: General Help
---

### Post by yasasvy on 2007-03-05
hi. i have a really strange problem .. when i try to run openoffice my ubuntu jus logs out the prob started jus an hour back. and i simply cant find a solution. i reinstalled the package from the repositories, but nothing seems to happen. i use dapper .. and have been using it since 6 months now never faced a prob as such!.

---

### Post by kwaanens on 2007-03-05
Do you have at-spi installed? If so, try removing it and see if that helps. I remember having some OOo issues in Dapper with that combo.

- K

---

### Post by yasasvy on 2007-03-05
hi.. thnx for ur reply.... i have removed at-spi package.. and also removed all those transitional pacakages for OOo . but. that didnt help either.

---

### Post by Rui Pais on 2007-03-05
Hi,
try:
```
mv .openoffice.org2 .openoffice.org2_BACKUP
```
and then restart openoffice.

---

### Post by yasasvy on 2007-03-05
nop. that command didnt work too.. the prob is still persistent

---

### Post by Rui Pais on 2007-03-05
sorry that didn't work...

Try to launch it from a terminal and watch the output for any error messages. 



And you need also to do a:
```
mv .openoffice.org2_BACKUP .openoffice.org2
```
to get back your personal settings.

---

### Post by yasasvy on 2007-03-05
when i run in terminal.. all i get is the splashscreen of OOo and BOOM it jus logs out.

---

### Post by Rui Pais on 2007-03-05
i forget that it would do that...

try:
```
oowriter >> oowriter_test.txt
```

---

### Post by milton1 on 2007-03-05
Are you actually getting a logout command somehow, or is X just crashing hard? If something has gone goofy with X, the problem may not be OOo.

---

### Post by yasasvy on 2007-03-05
i dont know whts wrong but all i know is that i get logout command for a split second an then i am redirected to the login screen

---

### Post by yasasvy on 2007-03-05
all the other progs r running fine..

---

### Post by Rui Pais on 2007-03-05
sounds like a conflict between your desktop environment and Oo (are you using, gnome, kde, xfce, other?)

Are you the only user? can you login on another account? (you can make one temporarily)

---

### Post by yasasvy on 2007-03-05
i use gnome and yeah i can login to other account... but the prob is there will all the users in my system

---

### Post by yasasvy on 2007-03-05
i even changed my theme thinking that might be the prob.. but it crashes even while in the default theme.. i dont thilnk there is a conflct it was working fine today mornign the last time i used was 6 hrs back.

---

### Post by Rui Pais on 2007-03-05
> **yasasvy said:**
> ... i can login to other account... but the prob is there will all the users in my system
sorry? do you mean that it logouts with other accounts?

what happened when you run oowriter >> oowriter_test.txt? Can you post the output of oowriter_test.txt? 
and whats the output of 
```
cat .xsession-errors
```?

---

### Post by yasasvy on 2007-03-05
this is the output i get..


```
nanyam@home:~$ cat .xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "nanyam"
/etc/gdm/Xsession: Beginning session setup...

(x-session-manager:10426): Gdk-WARNING **: locale not supported by Xlib

(x-session-manager:10426): Gdk-WARNING **: cannot set locale modifiers
SESSION_MANAGER=local/home:/tmp/.ICE-unix/10426

(metacity:10488): Gdk-WARNING **: locale not supported by Xlib

(metacity:10488): Gdk-WARNING **: cannot set locale modifiers

(gnome-panel:10494): Gdk-WARNING **: locale not supported by Xlib

(gnome-panel:10494): Gdk-WARNING **: cannot set locale modifiers

(nautilus:10496): Gdk-WARNING **: locale not supported by Xlib

(nautilus:10496): Gdk-WARNING **: cannot set locale modifiers

(gnome-panel:10494): GLib-GObject-CRITICAL **: g_object_ref: assertion `G_IS_OBJECT (object)' failed
Failed to load gnome-fs-desktop: Error displaying image

(gnome-panel:10494): GdkPixbuf-CRITICAL **: gdk_pixbuf_loader_set_size: assertion `width >= 0 && height >= 0' failed

(gnome-panel:10494): GdkPixbuf-CRITICAL **: gdk_pixbuf_scale_simple: assertion `dest_width > 0' failed

** (gnome-panel:10494): WARNING **: Invalid borders specified for theme pixmap:
        /home/nanyam/.themes/Elegance/gtk-2.0/Panel/panelbutton1.png,
borders don't fit within the image

** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


(gnome-volume-manager:10498): Gdk-WARNING **: locale not supported by Xlib

(gnome-volume-manager:10498): Gdk-WARNING **: cannot set locale modifiers
Gnome-Message: gnome_execute_async_with_env_fds: returning -1

(update-notifier:10516): Gdk-WARNING **: locale not supported by Xlib

(update-notifier:10516): Gdk-WARNING **: cannot set locale modifiers

(gnome-panel:10494): Gtk-WARNING **: gtk_widget_size_allocate(): attempt to allocate widget with width -13 and height 24

(gnome-cups-icon:10522): Gdk-WARNING **: locale not supported by Xlib

(gnome-cups-icon:10522): Gdk-WARNING **: cannot set locale modifiers

** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


(firefox-bin:10552): Gdk-WARNING **: locale not supported by Xlib

(firefox-bin:10552): Gdk-WARNING **: cannot set locale modifiers

(gksu:10630): Gdk-WARNING **: locale not supported by Xlib

(gksu:10630): Gdk-WARNING **: cannot set locale modifiers

** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient

(synaptic:10631): Gdk-WARNING **: locale not supported by Xlib

(synaptic:10631): Gdk-WARNING **: cannot set locale modifiers

** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


(gnome-terminal:10667): Gdk-WARNING **: locale not supported by Xlib

(gnome-terminal:10667): Gdk-WARNING **: cannot set locale modifiers

** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


** (gnome-panel:10494): WARNING **: invalid source position for horizontal gradient


```

---

### Post by Rui Pais on 2007-03-05
it seems that it won't output  nothing for .xsessions-errors (but something seems wrong either with your locales as with gnome-panel...)

you need to catch some error message to understand whats going on... 
what the output of ```
cat oowriter_test.txt
``` after running the oowriter>>oowriter_test.txt?

Try to:
```
strace oowriter
``` and see if it logout or stops at any specific message (should output a lot in the console)

---

### Post by yasasvy on 2007-03-05
there r no error messages for cat oowriter.txt and when i run the strace command.. it outputs  a lot.. and finally the session is loggin out.

---

### Post by yasasvy on 2007-03-05
hey.. thnx for bearing me till now.. its already wayy past midnight here.. and i have to attend college tomorrow.. if there r any possible suggstions.. please post them.. illl check them tomorrow morning.. i mean after 10 hrs.

---

### Post by yasasvy on 2007-03-05
now i am sure the prob is with the X 

[http://ubuntuforums.org/showthread.php?t=358894](http://ubuntuforums.org/showthread.php?t=358894)

i too have the prob with screensavers.. the same with OOo.

[http://ubuntuforums.org/showthread.php?p=1429832#post1429832](http://ubuntuforums.org/showthread.php?p=1429832#post1429832)

 and i even saw the aobve thread.. but that didnt solve my prob either.. i cant change my screensaver settings. i get the same prob.. the sessions keeps loggin off.

---

### Post by yasasvy on 2007-03-06
i simply cant find any answers to my prob.. ran out of ideas .. can any one help me! i removed gnome-screensavers and.. i know the prob is due to X but donno where to start ..

---

### Post by Rui Pais on 2007-03-06
well, thats even harder... 
bad luck

X logs are in /var/log/X.0.log

check for errors with:
```
cat /var/log/Xorg.0.log |grep "(EE)"
```

and warnings (these are not problematic, but may give some clue):
```
cat /var/log/Xorg.0.log |grep "(WW)"
```


Another thing to check is why there are so many error references about locale in xsessions-errors? 
What language do use set at login usually? try to log setting language to english and see if you still got logouts.

---

### Post by yasasvy on 2007-03-06
hi again.. this is the one for errors.. 

```
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) AIGLX error: Calling driver entry point failed(EE) AIGLX: reverting to software rendering
(EE) Failed to load /usr/lib/xorg-air/modules/extensions/libGLcore.so
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
```


and these r the warnings i get 

```
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(WW) The directory "/usr/share/X11/fonts/cyrillic" does not exist.
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(WW) I810(0): Extended BIOS function 0x5f11 not supported.
(WW) I810(0): config file hsync range 28-51kHz not within DDC hsync ranges.
(WW) I810(0): config file vrefresh range 43-60Hz not within DDC vrefresh ranges.(WW) I810(0): xf86AllocateGARTMemory: allocation of 1 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 4 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 16 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 8 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 768 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 768 pages failed
(WW) I810(0): xf86AllocateGARTMemory: allocation of 12801 pages failed
(WW) I810(0): Extended BIOS function 0x5f05 failed.
```

and i use english as the default language.

---

### Post by Rui Pais on 2007-03-06
Hi,
you seems to have problem loading glx module, something related to AIGLX. Maybe you are passing some incorrect option on xorg.conf. Btw, have you played around with compiz or beryl? 

wacom mentions are normal (no worry with that)

xf86AllocateGARTMemory are usually related with agp problems. What is you graphical card and which driver you use. You only noted this problem recently? Have you upgrade your kernel/restricted modules just after problem happen? Maybe a previous version of the kernel will work... 

Do you use English?! why it says locale not supported?... strange...
Can you post the output of:
```
locale
```


Can you post too the output of:
```
cat /etc/X11/xorg.conf
```

---

### Post by yasasvy on 2007-03-06
yeah i used to work on compiz and beryl.. but not now.. got sick of them .. very buggy.. and here r the outpus of the codes. u asked. 

```
nanyam@home:~$ locale
LANG=en_IN
LANGUAGE=en_IN:en
LC_CTYPE="en_IN"
LC_NUMERIC="en_IN"
LC_TIME="en_IN"
LC_COLLATE="en_IN"
LC_MONETARY="en_IN"
LC_MESSAGES="en_IN"
LC_PAPER="en_IN"
LC_NAME="en_IN"
LC_ADDRESS="en_IN"
LC_TELEPHONE="en_IN"
LC_MEASUREMENT="en_IN"
LC_IDENTIFICATION="en_IN"
LC_ALL=
nanyam@home:~$ cat /etc/X11/xorg.conf
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
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
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
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
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
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x400"
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

```

---

### Post by Rui Pais on 2007-03-06
so, your are using English from India... maybe your system failed to build the locales for that.
On a console type:
```
sudo locale-gen
```
and watch on the list tat outputs if en_IN is being generated.

If you don't mind, try this:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_TEMPBACKUP 
```
and then edit /etc/X11/xorg.conf, and replace it by this one:
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
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
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
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
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

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to
                                                      # /dev/input/event
                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Device"
        Identifier      "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Driver          "i810"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
#        HorizSync       28-51
#        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "720x400" "640x480" "640x400"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#        InputDevice     "stylus" "SendCoreEvents"
#        InputDevice     "cursor" "SendCoreEvents"
#        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
```
That will avoid some of the errors outputed on X log... don't know if they are caused by what ever is making your session being terminated...

Another thing was to check how you installed beryl. 
You installed aiglx too (eventually changing dri module too) you need to revert those steps. If you folowed something like [this how-to]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX") you will need to remove xserver-xorg-air-core, disable any repo related with beryl or dri and reinstall linux-dri-modules-common.

at least you should do:
```
sudo aptitude purge xserver-xorg-air-core
```
to see if remove that will avoid the error when load glx module when X server starts.

After that, 
rm .xsession-error file, 
go to a console (CTRL+F2) login and type :
```
sudo /etc/init.d/gdm restart
```
that will start a new X server with the new generated locales and new corg.conf.
Login and check if .xsession-errors have new errors.
Start Oo to see if still crash.

Good luck.

---

### Post by yasasvy on 2007-03-06
```
Generating locales...
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... up-to-date
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... up-to-date
  en_ZA.UTF-8... done
  en_ZW.UTF-8... done
Generation complete.

```

---

### Post by yasasvy on 2007-03-06
hey!!! thnx the prob is solved eventually.. the xorg-air-core is the culprit... i installed a version not supported by dapper... ooff. i came bak to life..  can sleep peacefully today.. 

however the xorg.conf u gave.. isnt working well .. my monitor.. shows up a resoultion of only 640*480 so. i reverted back to my original one.. now its perfect

thn for helping me out... bye TC. have a nice time.

---

### Post by Rui Pais on 2007-03-06
> **yasasvy said:**
> hey!!! thnx the prob is solved eventually.. the xorg-air-core is the culprit... i installed a version not supported by dapper... ooff. i came bak to life..  can sleep peacefully today.. 

however the xorg.conf u gave.. isnt working well .. my monitor.. shows up a resoultion of only 640*480 so. i reverted back to my original one.. now its perfect

thn for helping me out... bye TC. have a nice time.

Good! Nice to know it's solved.

The monitor resolution failure it's because of:
```
#        HorizSync       28-51
#        VertRefresh     43-60
```
most ot the cases the X server find those values automatically. 
Anyway uncomment them although working, outputs errors on logs... maybe a search on google for your monitor brand and model can easily show which are correct values.

The only other difference relative to yours original it's that i comment too the wacom references. 
That shouldn't even be warnings, much less errors... they are completely harmless but make logs huge with a lot of entrys referring it (sometimes it outputs too in console when one launch a program as root). 
I find more comfortable get rig of them :p

have a nice time too (and a good night sleep)
:)

---

