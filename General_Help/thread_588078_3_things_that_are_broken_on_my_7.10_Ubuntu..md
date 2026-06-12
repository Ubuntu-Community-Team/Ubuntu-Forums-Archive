---
title: "3 things that are broken on my 7.10 Ubuntu."
date: 2007-10-23
forum: General Help
---

### Post by lawentzel on 2007-10-23
I have three things that are broken with Ubuntu 7.10 that I would like to resolve.

1) My touch pad doesn't do the scrolling thing.  There is NO touch pad option under mouse in System, Preferences.

2) When I first installed 7.10 during the Alpha or Beta the power icon worked.  When I unplugged the power, it did show a battery icon.  Several updates later, and it too is broke.  The strange thing is, the battery applet you can install on the task bar still works flawlessly.  I just want the real icon to work.

3) Probably the most annoying, there is NO eject option to select when I put in a USB memory sticks, or my floppy dirve.  There is an unmount.  No eject.

Any help in resolving these would be greatly appreciated.

---

### Post by dayvy on 2007-10-23
If your touch pad is a synaptics you can install gsynaptics. This will add a tab to your mouse preferences (if I remember correctly)

Not sure about your battery icon as I don't have a laptop here to look at it.

There is only an eject option for cds. It should only be unmount for those devices as this tells the kernel to write the data to the device and then unmount it from the file system. It doesn't have the ability to physically eject these devices. This option may have been present before (I don't remember) but eject is a bit of a misnomer.

d.

---

### Post by lawentzel on 2007-10-23
Installing the gsynaptics went fine. It did not add the icon to the Mouse screen. It did add a Touch Pad option. So clicking on it, gets me an error which reads:

GSynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics

Tried the Unmount, and that did work, thank you. In the past you would "Eject" the thumb drive. Actually if you pulled the thumb drive off without unmounting or ejecting (since the option isn't there) you would get a message pop up that tells you, you need to select "Eject" from the drive before removing it.

Thank you for your help Dayvy.

Lee

---

### Post by Steve1961 on 2007-10-23
You need to add that SHMconfig entry to xorg.conf.  Should looks something like this:

Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
    Option         "SHMConfig"        "on"
EndSection

---

### Post by lawentzel on 2007-10-23
There are two xorg.conf.  One is located in /etc/X11 and the other in /usr/share/xresprobe.  I have added that information to both of them.  Completely restarted the laptop and still am getting the same error.

Lee

---

### Post by lawentzel on 2007-10-23
Double checked my CD-Rom drive, and there is no eject option for it either.  So, I am going to do a fresh install and see were I am at afterwards.

Lee

---

### Post by lawentzel on 2007-10-23
Okay...  A format and reload and here I am with the same problems.  The touch pad isn't working "automatically".  No option for it in Mouse.  Looking at Device Manager, it recognizes the touchpad as "SynPS/2 Synaptics TouchPad".

There is no eject option for my CD-Rom or the thumb drive.

Finally the power icon does not show if you are running on battery or AC.

---

### Post by lawentzel on 2007-10-24
Any suggestions?

The last time the touch pad worked was with version 6.10.  By worked, I mean had the scrolling capabilities.  This was without installing any additional software.

The power icon worked when I had installed the developers version of 7.10.  However several updates later and it is broke.

Version 7.04 has an eject option for the CDRom and thumb drive.

---

### Post by dayvy on 2007-10-24
I have gutsy installed and only have the eject for the cd-rw. I have unmount for the other devices.

What kind of laptop is it? I have gutsy installed on a toshiba at home and it also has a synaptics touchpad. I usually disable it as it drives me nuts. Anyhow, I'll have a look at the touchpad configuration and also the power icon and get back to you.

d.

---

### Post by lawentzel on 2007-10-24
It is a Compaq Prosignia 150 (or 170).  Thank you Dayvy.

---

### Post by dayvy on 2007-10-24
The power icon is called gnome-power-manager and should be enabled in "System" -> "Preferences" -> "Sessions". It's called "Power Manager" in the list and if it's not there then you can add it. The command is: gnome-power-manager.

Here is my xorg.conf file. You can see the synaptics entries there.

Section "Files"
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
        Identifier      "Intel Corporation 82852/855GM Integrated Graphics Device"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Also, try this to see if the synaptics module is being loaded:

sudo cat /var/log/Xorg.0.log | grep synaptics

You should see something like this:

(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="The XFree86 Project"

d.

---

### Post by dayvy on 2007-10-24
Oh yeah, notice at the end of the xorg.conf file the InputDevice "Synaptics Touchpad". It's easy to miss.

d.

---

### Post by lawentzel on 2007-10-25
> **dayvy said:**
> The power icon is called gnome-power-manager and should be enabled in "System" -> "Preferences" -> "Sessions". It's called "Power Manager" in the list and if it's not there then you can add it. The command is: gnome-power-manager.

It was there.  So, I ended it.  My icon on my task bar disappeared.  Went to terminal and typed "gnome-power-manager" and the icon came back.  When the icon worked, it looked differently then the icon I currently have.

I've just copied the bulk of your xorg.conf file.  The one thing I noticed, that I didn't add last time, was one of the last lines.

> **dayvy said:**
> InputDevice     "Synaptics Touchpad"

I am rebooting right not and am going to see if those changes worked.  They did.  In fact I am not sure I needed to add the gsynaptics in Add/Remove programs.  I went into Mouse, and sure enough there was a touchpad tab.  Thank you Dayvy.

Now just need to either live with the power icon, and no eject button on my CD-Rom, or sort them out.  Again, thank you very much for your help Dayvy.  I really think it was that last line that made the difference in the touchpad.  I have a friend with the exact same laptop & Ubuntu.  Will see if that is all that is required to fix it.

---

### Post by vapore0n on 2007-10-25
is the "Show icon" enabled on the power management preferences? The icon will vary with the theme.

To eject a usb device I have to unmount it. As soon as its done I remove it. If its writing some data it will pop up a message stating so.
Though sometimes it will pop up a message stating "the device can be removed now" or something.

---

### Post by lawentzel on 2007-10-25
> **vapore0n said:**
> is the "Show icon" enabled on the power management preferences? The icon will vary with the theme.

Thank you Vapore. I am aware that the icons will change with the different themes. The icon is set up to display. There is an icon there. Without changing themes, when ever the kernel seems to be updated, the "working" icon will appear just prior to a reboot. I use to have a screen snap shot of it... however, I recently (yesterday) formated and reloaded Ubuntu to ensure the problems I was having wasn't related to past updates and such.

As to the eject option.  I am completely fine with unmounting the device.  My point and question I guess is, prior to 7.10 there was an eject option.  Which is what I was use to doing.  It's no longer there.  If that is by design.  Fine.  If it is a bug, I would like to have it working the way it was meant to.  That's all.

Again, just to prove my point.  Plug in your thumb drive.  Give it a moment to recognize the drive and mount an icon on your desktop.  Now, unplug it.  You will get a VERY specific message which tells you to "eject" the drive prior to unplugging it.

Thank you for your assistance.

Lee

---

### Post by lawentzel on 2007-10-25
Just verified it on another laptop.  The only two things I needed to add to xorg.conf to get the touchpad working was:

> **dayvy said:**
> Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

And:

> **dayvy said:**
> InputDevice     "Synaptics Touchpad"

At the end of the file.  I did not have to install gsynaptics, or any other files for that matter.

---

### Post by lawentzel on 2007-10-25
Seems I did make a backup of my screen capture.  So... you can see the "Good" icon and the current one at:

[http://www.geocities.com/lawentzel/powericon.html]("http://www.geocities.com/lawentzel/powericon.html")

You will notice the restart icon next to the good power icon.  Once I restarted the computer, the power icon reverted back to the lower one.

---

