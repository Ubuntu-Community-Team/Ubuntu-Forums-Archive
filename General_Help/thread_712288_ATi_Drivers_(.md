---
title: "ATi Drivers :("
date: 2008-03-01
forum: General Help
---

### Post by wh33t on 2008-03-01
I installed Xubuntu 7.10 fine. It updated fine and did the typical Ubuntu goodness. But then after I installed using the Restricted available drivers update for my x800 I can no longer get a log in screen :(

Xubuntu boots and I get a black screen... bah!

---

### Post by Rocket2DMn on 2008-03-01
Hey, run the automatic reconfigure of X: do CTRL+ALT+F1 to get to a tty and run
```
sudo /etc/init.d/xdm stop
sudo dpkg-reconfigure xserver-xorg -phigh
sudo /etc/init.d/xdm start
```
That should restore your original settings.

In order to get fglrx to work, you may need to reconfigure X manually, so if needed, you can follow this guide: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
For the restricted drivers you would select "fglrx" instead of "ati".

---

### Post by wh33t on 2008-03-01
Thanks man.

It does make me sad that it doesn't work though.
I thought for a second I was in something better and easier to use than Windows :(

---

### Post by Joeb454 on 2008-03-01
Try running the command **Rocket2DMn** mentioned above, but change gdm to xdm, and see if that works :)

---

### Post by Rocket2DMn on 2008-03-01
Ease of use is relative.  For a lifetime windows user to suddenly switch to Ubuntu would make it seem difficult since you already know how to use windows.  There IS a learning curve, if somebody told you otherwise, you were lied to - that being said, we wouldn't be here if we didn't love Ubuntu.  If you had never used windows or linux before, you would probably find linux easier to use.

I fixed my post above, I didn't realize you were using Xubuntu (my bad!).  It's xdm not gdm :)  Try again, hehe.
Thanks Joeb!

---

### Post by wh33t on 2008-03-01
> **Rocket2DMn said:**
> Hey, run the automatic reconfigure of X: do CTRL+ALT+F1 to get to a tty and run
```
sudo /etc/init.d/xdm stop
sudo dpkg-reconfigure xserver-xorg -phigh
sudo /etc/init.d/xdm start
```
That should restore your original settings.

In order to get fglrx to work, you may need to reconfigure X manually, so if needed, you can follow this guide: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
For the restricted drivers you would select "fglrx" instead of "ati".

Odd. I can't seem to get another TTY. I hit CTRLALTF1 and nothing happens, same if i try F2-7.
Another strange thing is that my 22" LCD appears to be on... Which means it's getting signal from the video card, but it's just not showing me anything. I wonder if it's because my monitor has such a weird resolution 1680x1050.

I booted into safe mode (recovery mode in linux i think from the grub menu), and ran the command, but with gdm, I will try again with xdm.

I may also plug in my old crt to see if that makes a difference.

---

### Post by Rocket2DMn on 2008-03-01
> **wh33t said:**
> I booted into safe mode (recovery mode in linux i think from the grub menu), and ran the command, but with gdm, I will try again with xdm.

We've seen the problem with TTYs not showing, but we're not sure why.  
Get into recovery mode, you won't need to start/stop xdm in recovery mode because the GUI isn't running.  You will just need to reconfigure X (no sudo necessary since you will be at a root terminal).
```
dpkg-reconfigure xserver-xorg -phigh
reboot
```

If that doesn't get you back to a GUI when you run "reboot" and choose the normal kernel, get back to the recovery kernel and run the manual configure with
```
dpkg-reconfigure xserver-xorg
reboot
```

[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by wh33t on 2008-03-01
> We've seen the problem with TTYs not showing, but we're not sure why. 

I'm guessing because of hsync vsync rates. Why do I say that? Because I just switched back to my CRT monitor and it worked fine. Looks like my video card is spitting out some bogus junk my LCD can't interpret. GRRRR

Also, I didn't have xdm in my init.d directory, only gdm... not sure what's up with that. But I promise you I am running xubuntu.

Anyways. Tell me what I can do to make this work on my LCD. It's an Acer 22" LCD at 1680 * 1050.

Ps. Graphic accel is nice !

---

### Post by Rocket2DMn on 2008-03-01
Can you please post the output of:
```
sudo lsb_release -a
```

---

### Post by wh33t on 2008-03-01
```
wh33t@wh33t-desktop:~$ sudo lsb_release -a
[sudo] password for wh33t:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
```

---

### Post by Rocket2DMn on 2008-03-01
It appears that you are using Ubuntu (with Gnome) instead of Xubuntu (with Xfce).  I have no idea about the confusion, but this appears to be the way it is...
Use "gdm" instead of "xdm"

So where are we now?  Do you have a GUI on the LCD?  What works and what doesn't?

---

### Post by wh33t on 2008-03-01
I'm using Xubuntu. I downloaded the ISO from xubuntu, and when I boot I get the xubuntu splash. I have the xfce menu and everything. I know what gnome looks like, this is not it.

My crt works, but my LCD does not. I'm in xubuntu right now.

---

### Post by Rocket2DMn on 2008-03-01
w0rd.

This is all very confusing, because Xfce uses xdm, not gdm.  Can you please post your xorg.conf file and the output of the second command:
```
cat /etc/X11/xorg.conf
lspci | grep VGA
```

---

### Post by wh33t on 2008-03-01
```

wh33t@wh33t-desktop:~$ cat /etc/X11/xorg.conf
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
        Identifier      "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
        Driver          "ati"
        BusID           "PCI:2:0:0"
EndSection

Section "Monitor"
        Identifier      "Acer AL2216W"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
        Monitor         "Acer AL2216W"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1680x1680" "1680x1050" "1600x1200" "1440x1440" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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
EndSection
wh33t@wh33t-desktop:~$ 
```

```
wh33t@wh33t-desktop:~$ lspci | grep VGA
02:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)
wh33t@wh33t-desktop:~$
```

Edit.

Weird it still thinks i"m using my LCD. I am not. I'm using my CRT now.

---

### Post by Rocket2DMn on 2008-03-01
You need to run the manual configuration, and select "fglrx" as your driver.  Here is the guide again: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
Do it with your LCD plugged in since this is what you will be using.

---

### Post by wh33t on 2008-03-01
Well I ran the dpkg-reconfigure and rebooted with my LCD hooked up. This time for some strange reason it appeared. 

So am I now back at the default as if I just did the install? Or do I have the ati-closed source driver running? Is there a way I can check if I'm getting 3d/2d acceleration?

Also. I don't get 1680x1050 as a resolution choice. How can I add that in there?

---

### Post by Rocket2DMn on 2008-03-01
Did you run the configure with your LCD plugged in?  Please do that.  When prompted about resolutions, select 1680x1050 and everything less by using TAB to move and SPACEBAR to select.  Choose the "ati" open source drivers since the proprietary ones aren't working.  At least you'll be back to square one.  If you want, you can try fglrx if you were able to get a GUI with it.
Once in the GUI, run
```
glxgears -info
```  If you are getting a few hundred frames/sec or more, you have 3d running.

---

### Post by wh33t on 2008-03-01
From your other post, when I run dpkg-reconfigure it gives me an error message about the file already existing or some sort... So I can't even do the manual set up :(

```
wh33t@wh33tbox:~$ sudo dpkg-reconfigure xserver-xorg -phigh
[sudo] password for wh33t:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080301181856
wh33t@wh33tbox:~$ 
```

Btw, I reinstall xubuntu. I have not put any updates yet. This is totally fresh.

---

### Post by Rocket2DMn on 2008-03-01
That message is normal, it just makes a backup of your original xorg.conf file in the format xorg.conf.YearMonthDayTime
It DID get the manual configuration.  Here is the guide to install the proprietary drivers: [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
Install them and tell me what happens.

---

### Post by uberlube on 2008-03-01
How did you install your drivers?

---

