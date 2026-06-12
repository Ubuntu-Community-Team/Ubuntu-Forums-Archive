---
title: "Dual graphics cards for three monitors"
date: 2013-01-15
forum: General Help
---

### Post by wshaffer79 on 2013-01-15
Hello,

I'm not sure what specific section this should go in, and my searches are only coming up with dual monitor threads.

I have a system running Ubuntu 12.10 with Gnome Shell that has two NVIDIA Quadro NVS 290 cards in it.  One card has two monitors attached, and the other has one monitor.  The OS is using the nouveau driver.

Currently, the two monitors attached to the one card work fine.  The desktop is extended between the two monitors and works as I would expect in a dual monitor setup.  However, the single monitor on the second video card does not seem to be detected in Gnome.  The Display settings applet doesn't see it.

When I run 'lspci', I see a line for both NVIDIA cards, so at least the kernel sees them both.  How do I get the nouveau driver to see and use both cards so that Gnome can extend to all three monitors?

Thanks in advance for the help.

---

### Post by Cheesemill on 2013-01-15
I'm not sure if the nouveau driver supports this sort of set up.

Have you tried installing the closed-source Nvidia drivers as these tend to provide more options (go to Software Sources > Additional Drivers).

---

### Post by wshaffer79 on 2013-01-15
I did try the closed source drivers a few times.  It has been a few weeks, so I don't remember the specifics.  I know I installed them via the additional drivers thing, but then I had to reboot.  When I rebooted, BIOS would post, the kernel would attempt to start loading, and the screen went blank with an error message similar to:

<some numbers> xgifb: video bios unavailable.....

and it would just freeze there.  I ended up having to reinstall the OS (not knowing how else to fix it) and it of course reverts back to the nouveau drivers.

I'm not sure I want to attempt to use the nvidia drivers again because I don't want to have to reinstall the OS yet again if something fails.

---

### Post by dannyboy79 on 2013-01-15
according to this here: [http://superuser.com/questions/81981/dual-nvidia-graphics-cards-in-ubuntu-xorg-conf-mania](http://superuser.com/questions/81981/dual-nvidia-graphics-cards-in-ubuntu-xorg-conf-mania)
it states if the cards are the same it should work. When using the nvidia binaries I am not sure installing them thru the additional hardware blacklists the nouveau driver. I know if you install the nvidia binaries from their website, it DOES blacklist the nouveau driver. Good luck

---

### Post by wshaffer79 on 2013-01-16
I went ahead and enabled the NVIDIA proprietary drivers from nvidia-current, via the "Additional Drivers" tab of the "Software Sources" application.  Then I rebooted the computer.  BIOS did its post tests, the screen went blank, and displays the following error:
 
[    10.070170]  xgifb 0000:20:05.0: video BIOS not available
 
 
I can't tell if grub even loaded or not.  The system appears to be frozen at this error message.  The normal Ubuntu splash screen didn't even come up that normally appears during the boot process.  I didn't make ANY other changes other than to enable the nvidia-current driver and reboot.
 
Any ideas on this?  I'm guessing I can boot with a LiveCD, chroot to the Ubuntu filesystem, and revert back to the nouveau drivers, but I wanted to see if there is a better way to fix this.

---

### Post by dannyboy79 on 2013-01-16
can you hit ctrl-alt-f1 and log into a textual environment? was there an xorg.conf file created? can you check the /var/log/Xorg.0.log file for errors?

---

### Post by wshaffer79 on 2013-01-16
While the xgifb error in my previous post is displayed, the system is completely unresponsive.  I can't ctrl-alt-F1 or anything through F12.  Ctrl-alt-delete also does not respond.  I rebooted the computer via the power button and booted with a LiveCD instead and mounted the hard drive under /mnt/hd.

There is no xorg.conf file under mnt/hd/etc/X11.  There also are no configuration files at all in /mnt/hd/etc/X11/xorg.conf.d.  However, there is a file named /mnt/hd/etc/X11/xorg.conf.failsafe, which uses the "fbdev" driver.

I took a look at the Xorg.0.log file and it looks like it attempts to use several modules one by one, failing each one, including 'nvidia', 'nouveau', 'nv', and 'vesa'.  It says that the modules are not present for at least most of them.

The log file is attached.

I thought by selecting the nvidia-current driver from 'additional drivers', that it would have installed the actual kernel module files.

---

### Post by wshaffer79 on 2013-01-16
Sorry, I accidentally grabbed the LiveCD version of Xorg.0.log instead of the copy on the hard drive.  New file is attached.

I noticed that the log file states that the "nvidia" module is not present, but if I follow the symlink for /usr/lib/xorg/modules/drivers/nvidia_drv.so, it follows a few other symlinks to the actual /usr/lib/nvidia-current/xorg/nvidia_drv.so

---

### Post by wshaffer79 on 2013-01-16
I think I may have found the answer.  I assume the nvidia-current driver is for a standard NVIDIA card.  The card I'm using is an NVIDIA Quadro NVS 290.  If nvidia-current doesn't supply the right driver, I'll have to install the one from nvidia.com.
 
I attempted to install it from their website by booting off a LiveCD, chrooting to my local hard drive, and running the NVIDIA....bin file, but it said the distribution's pre-install script failed, so I aborted the install.  Should I be able to install the one from nvidia.com via chroot?
 
I also cannot successfully boot the hard drive (without CD) either normally or into recovery mode.  It freezes completely either way.

---

### Post by dannyboy79 on 2013-01-16
i am not sure if the nvidia binaries support the quadro cards? did you verify on the website?

can you chroot into the OS and uninstall the nvidia-current driver so it reverts back to the nouveau driver?

---

### Post by wshaffer79 on 2013-01-17
Nvidia's website has a search where I can specify the Quaddro series and drill down to the Quaddro NVS 290 card.  It then comes up with a driver, which I downloaded, so it should support the card.
 
I booted off the LiveCD again, chrooted into the OS, and uninstalled nvidia-current.  Upon reboot (without the CD) the lightdm login manager came up successfully, so it looks like nouveau was being used.
 
I logged in and tried to ctrl-alt-f1 so that I could kill X and install the quaddro binary from nvidia, but it didn't give me a text console, just a blank screen on ctrl-alt-f1.  So, I rebooted with the LiveCD.
 
I booted the LiveCD, chrooted to the OS, and tried installing the binary from their website.  It appeared to install successfully, and even "attempted" to disable the nouveau driver.  Now somehow it almost seems that neither of the drivers are installed properly.  If I boot off the hard drive, I am getting the xgifb video bios unavailable message again.
 
If I boot the livecd, chroot to the OS, and try to uninstall nvidia-current, or the nvidia proprietary driver, it says they are not installed, but that 'video bios' error implies that they are installed.
 
I'll keep digging.

---

### Post by wshaffer79 on 2013-01-17
Another update.
 
I chrooted into the OS and tried something I found on this website to 'remove' the nouveau drivers: [http://linuxers.org/howto/how-remove-nouveau-drivers-ubuntu](http://linuxers.org/howto/how-remove-nouveau-drivers-ubuntu)
 
This includes blacklisting a few modules in /etc/modprobe.d/blacklist.conf, uninstalling all of nvidia* packages, and rebooting. Reboot brings me right back to the "video BIOS not available" error message. This looks like perhaps a kernel error since it does come up right after grub loads (in the background).
 
If I try to use the Ubuntu 12.10 LiveCD to chroot into the OS and install nvidia drivers from the website, it fails because nouveau is already in use. The installer attempts to disable it, but it is disabling the ones on the hard drive, not the ones on the LiveCD. Is there a way to disable the ones on the LiveCD while the system is running? I can't just 'rmmod nouveau' because it says the driver is in use.
 
EDIT:  I found a way to disable the nouveau driver that is running from the LiveCD.  When you start booting the LiveCD, hit 'tab' on the keyboard when the bootloader is coming up.  When grub comes up with the text menu, hit 'tab' again to display the end of the 'kernel' line where it mentions 'splash' and other options.  Type 'noveau.blacklist=1' at the end of the line and hit F10 to boot.  When the kernel tries to load the noveau module, it will fail because there apparently is no .blacklist submodule inside noveau.  So it will revert the LiveCD to use some other module for graphics (VESA??).  You can verify by pulling up a terminal after it boots and run 'lsmod |grep noveau'.
 
I did this and the LiveCD then allowed me to chroot the installed OS, install the proprietary drivers (sudo ./NVIDIA-<version>.bin), and reboot.  BUT.... rebooting still causes the 'video BIOS not available' error.
 
I'm at a loss...

---

### Post by wshaffer79 on 2013-01-22
Since this thread is getting away from the original topic, dual graphics cards for three monitors, I will move this discussion to another thread I forgot that I had open.  Link is below.  Feel free to discuss the original topic here.

Link to other thread about the "video BIOS not available" message:
[http://ubuntuforums.org/showthread.php?t=2096541](http://ubuntuforums.org/showthread.php?t=2096541)

---

### Post by grantjohnston on 2013-02-03
Alright, I'm having the same issues as (seemingly) everyone. I've got an NVIDIA GTX 550 x2 running non-SLI (board will not support it) and needing it to run via DVI to a 20" Dell, 19" eMachine (on first card) and then via HDMI to my 50" Insignia TV. Running Ubuntu 12.10 x64. Any questions; lemme know!

I've used NVIDIA TwinView and then tried adding Xinerama to add the third monitor (via all the tips in this thread and many others out there via google).

The best I can get is my desktop appearing on my two monitors via card #1 and card #2 (50" Insignia TV) is a different X screen with a full white screen covering it. I can move the mouse over there, but cannot move a window I've got open.

If I pop up a terminal and kill nautilus it'll kill the screen on  new X server on the 50" and show my background, but it'll not have any window manager allowed there.


I'm in 'doze atm (only way I can view my movies/TV shows at the moment that I've got on my computer) so I can't post my xorg.conf right now, but I will later.

Any help would be UNBELIEVABLY appreciated. This is the last thing I need Windoze for. I've been poking around on the net for some time now trying to get this fixed.



Does ANYONE have a clue?


Thanks


grant

---

### Post by grantjohnston on 2013-02-09
Here's my xorg.conf btw. This is the one I have running currently for my two DVI monitors and the TV not activated/hooked up. I'll post the one I've been trying to tweak and get working to get the 2 monitors and the TV working (TwinView/Xinerama combined).


Anyway, here's the working one (2 monitors, no TV)

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 304.51  (buildd@komainu)  Fri Oct 12 12:53:49 UTC 2012


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
    ModelName      "DELL E207WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 550 Ti"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 550 Ti"
    BusID          "PCI:2:0:0"
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-2: nvidia-auto-select +1680+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "DFP-0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-2: nvidia-auto-select +1680+0; DFP-0: nvidia-auto-select +0+0, DFP-2: nvidia-auto-select +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection


```

---

### Post by grantjohnston on 2013-02-09
Here's the one I've been working with and trying to get working to get all three monitors working.

```

# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 304.51  (buildd@komainu)  Fri Oct 12 12:53:49 UTC 2012


Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    Screen	1  "Screen1" LeftOf "Screen0"
    Option	   "Xinerama" "1"
    Option	   "AIGLX" "true"
    Option	   "RenderAccel" "true"
    Option	   "AllowGLXWithComposite" "true"
    Option	   "XGL" "true"	
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load	   "dbe"
    Load	   "extmod"
    Load	   "type1"
    Load	   "freetype"
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
    ModelName      "DELL E207WFP"
    HorizSync       30.0 - 83.0
    VertRefresh     56.0 - 75.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 550 Ti"
    BusID          "PCI:1:0:0"
EndSection

Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce GTX 550 Ti"
    BusID          "PCI:2:0:0"
EndSection

Section "Screen"

# Removed Option "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-2: nvidia-auto-select +1680+0"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    Option	   "AddARGBGLXVisuals" "True"
    Option	   "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "metamodes" "DFP-0: nvidia-auto-select +0+0, DFP-2: nvidia-auto-select +1680+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"

    Identifier	   "Screen1"
    Device	   "Device1"
    Monitor	   "Monitor1"
    DefaultDepth    24
    Option	   "AddARGBGLXVisuals" "True"
    Option	   "TwinView" "0"
    Option	   "metamodes" "nvidia auto-select +0+0"
    SubSection "Display"
	Depth	    24
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

I will say, though when I run this one it messes EVERYTHING up. Where the mouse appears on the screen is not actually where it clicks (if you right click where you think it is the menu appears on pretty much the other side of the monitors; I still can't appear to drag anything to/from the third monitor. Also, the login screen splits between the two monitors on the main card (Although, from re-thinking that bit, I think it's because I have xinerama enabled on the first card when it probably shouldn't.


I'm going to try and mess with this setting some more and see what I can't pull out of it... I also have another xorg.conf that has a lot of hashtags in it that explain what everything does and goes rather in depth... So I may try and mess with that a bit later on too...


If anyone has ANY input on this I'd appreciate it more than you could know... Even if I can't get this to work in Unity but can in Gnome, XFCE or w/e that would be stellar... I've read that Xinerama can't work in Unity3d; which is cool with me. I'll go back to XFCE if I need to.


Anyway, any thoughts and help are MUCH appreciated



grant

---

