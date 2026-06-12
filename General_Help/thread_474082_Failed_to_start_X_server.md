---
title: "Failed to start X server"
date: 2007-06-14
forum: General Help
---

### Post by raichle on 2007-06-14
Hi all, I have been happily running Feisty Fawn for a little while now.   I followed the directions here: 

[http://www.xsol.se/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/](http://www.xsol.se/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/)

and when I rebooted, I received this error:

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly."

Then I view the X server output and see

X Windows System Version 7.2.0
Release...
X Protocol Version 11, Revision 0 Release 7.2
Build...
Current Operating System: Linux avenger 2.6.20-16-generic #2 SMP Thu Jun 7..... i686
...
Module Loader Present
Markers:....
(==) Log file:...
(==)Using config file: "/etc/X11/xorg.conf"

Finally I get to "The X server is now disabled.   Restart GDM when it is configured correctly."  And, I can log in to the CLI.  

Can anyone tell me how to fix in really clear steps?

Thanks!




*** Edit, it's a Dell Inspiron B130 laptop

The permissions on /etc/X11/xorg.conf are rw-r-r

When I run "sudo startx" 

I see these errors:  
(EE) Problem parsing the config file
(EE) Error Parsing the config file

---

### Post by Crafty Kisses on 2007-06-14
> **raichle said:**
> Hi all, I have been happily running Feisty Fawn for a little while now.   I followed the directions here: 

[http://www.xsol.se/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/](http://www.xsol.se/index.php/2007/04/29/feisty-performance-fly-like-a-butterfly/)

and when I rebooted, I received this error:

"Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly."

Then I view the X server output and see

X Windows System Version 7.2.0
Release...
X Protocol Version 11, Revision 0 Release 7.2
Build...
Current Operating System: Linux avenger 2.6.20-16-generic #2 SMP Thu Jun 7..... i686
...
Module Loader Present
Markers:....
(==) Log file:...
(==)Using config file: "/etc/X11/xorg.conf"

Finally I get to "The X server is now disabled.   Restart GDM when it is configured correctly."  And, I can log in to the CLI.  

Can anyone tell me how to fix in really clear steps?

Thanks!




*** Edit, it's a Dell Inspiron B130 laptop

The permissions on /etc/X11/xorg.conf are rw-r-r

When I run "sudo startx" 

I see these errors:  
(EE) Problem parsing the config file
(EE) Error Parsing the config file

You should try reconfiguring your X server:
```
sudo dpkg-reconfigure xserver-xorg
```

Then after that you should make a backup, so if anything else goes wrong you can quickly recover it:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then when you want to recover your backed up X server file, you can try:
```
cp /backupdir/xorg.bak /etc/x11/xorg.conf
```

Hope this helps. :)

---

### Post by raichle on 2007-06-14
I ran  "sudo dpkg-reconfigure -phigh xserver-xorg" and was able to get back into GDM.   But when I look through my /etc/X11/xorg.conf file now I see that the video stuff is all set to generic.  The complete file is below.   How can I get everything back to the way it was?  It used to be set as an Intel running the i810 driver.



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
        Identifier      "Generic Video Card"
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
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
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

---

### Post by Crafty Kisses on 2007-06-14
> **raichle said:**
> I ran  "sudo dpkg-reconfigure -phigh xserver-xorg" and was able to get back into GDM.   But when I look through my /etc/X11/xorg.conf file now I see that the video stuff is all set to generic.  The complete file is below.   How can I get everything back to the way it was?  It used to be set as an Intel running the i810 driver.



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
        Identifier      "Generic Video Card"
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
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
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
Just reconfigure everything, then backup your X server file, so if this ever happens again, you can quickly get it back into working order.

---

### Post by raichle on 2007-06-14
that works and I backed it up.  Thanks!

---

### Post by Crafty Kisses on 2007-06-14
> **raichle said:**
> that works and I backed it up.  Thanks!

No problem. :p

---

### Post by surfer57 on 2007-06-15
God Bless you CODENAME!!!!  wOOt  I had upgraded to fiesty and then lost my xsever....thanks to you my desktop is back.....no more hacking ati drivers for me auto detect is now my mantra...thanks again....\\:D/

---

### Post by Crafty Kisses on 2007-06-15
> **surfer57 said:**
> God Bless you CODENAME!!!!  wOOt  I had upgraded to fiesty and then lost my xsever....thanks to you my desktop is back.....no more hacking ati drivers for me auto detect is now my mantra...thanks again....\\:D/

No problem man anytime I love to help anyone and everyone. :p

---

### Post by jpbefx on 2007-06-27
> **Codename said:**
> No problem man anytime I love to help anyone and everyone. :p

This sux.  I have tried everything I can to fix my xserver issue.  I have error microcode bcm43xx and it says that my xserver is not configured right.  I have done [FONT="Courier New"]_Sudo dpkg-reconfigure xserver-xorg_[/FONT] and gone through all of the items in there and put in all of my system info which is keyboard pc101, ATI driver. graphic card is ATI Mobility Radeon X1300. on PCI 1:0:0,generic monitor, I put 16 bit for the colors as so not to overwhelm the program, and have all the defaults for the rest.  I have done the [FONT="Courier New"]_sudo /etc/init.d/gdm stop_[/FONT] and [FONT="Courier New"]_sudo /etc/init.d/gdm start_[/FONT] at which it says [FONT="Courier New"][failed][/FONT] and then I re-do the [FONT="Courier New"]_sudo /etc/init.d/gdm start_[/FONT] and it blink the screen a couple of times and goes right back to the xserver is not recognized screen again and I then do the [FONT="Courier New"]_sudo dpkg-reconfigure xserver-xorg_[/FONT] again and go through all of the options again.  I've tried all of the combinations I can possibly think of and none of them will take.  I am running from the cd since I can't get to the install option. so I have to manually install the broken system first before I can do any of the xserver changes??  What am I doing wrong.  I have also tried [FONT="Courier New"]_sudo apt-get update_[/FONT], and [FONT="Courier New"]_sudo apt-get upgrade_[/FONT] along with the [FONT="Courier New"]_sudo apt-get install lynx_[/FONT], and still nothing.  I am at the brink of giving up I'm also a noob to this system and to the Linux world.  I have been reading blog after blog for the last two weeks and nothing I've read is helping:(:(:(.  WTHeak  If anyone can help PLEASE do.  I thank everyone for their support in advance. ;););)

---

### Post by Diabolis on 2007-06-29
I had the same error, and I ran many times the "sudo dpkg-reconfigure xserver-xorg" command with no luck. I choosed many times the VESA driver because I read in another forum that VESA was a good option. After reading this thread I decided to try with the i380 driver, it seems to work, but now ubuntu takes too long to load de UI and everything looks smaller(I guess that deals with the resolution or the monitor size I picked while reconfiguring).

While I was reconfiguring the x server I really wasn´t sure what I was doing and I kind of just picked what seemed good. Is there any documentation around about how to make a good x server configuration?

I think is worth to mention that I had no problems with ubuntu until I tried to upgrade from edgy to feisty.

---

