---
title: "Recompile the kernel."
date: 2008-01-26
forum: General Help
---

### Post by supertails on 2008-01-26
How do I recompile the kernel on a Toshiba A215-S7437?

---

### Post by Kilz on 2008-01-26
This is far from a beginner topic. I am in the process of learning to compile a kernel myself to improve performance. Here are some sites that have been helpful

[http://www.howtoforge.com/kernel_compilation_ubuntu_p2](http://www.howtoforge.com/kernel_compilation_ubuntu_p2)
[http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/](http://www.howtogeek.com/howto/ubuntu/how-to-customize-your-ubuntu-kernel/)

And there is a application called kernelcheck that seems to make things easier.
[http://ubuntuforums.org/showthread.php?t=618563&highlight=kernelcheck](http://ubuntuforums.org/showthread.php?t=618563&highlight=kernelcheck)

---

### Post by hal10000 on 2008-01-26
kernelcheck is a very good tool, Itried it yesterday. But if you are really a beginner, you should first read the links mentioned by kilz and find out if you really need to compile you own kernel.

---

### Post by supertails on 2008-01-27
I did the kernelcheck. Is it suppose to shut it's self down. I saw it close it's self and I'm wondering if it was suppose to do that. My sound is still mute and the time is still off.

---

### Post by Washer on 2008-01-27
Main question: Why do you want to recompile? Time can be changed by right clicking on it & selecting adjust date/time.

kernelcheck is good, but it's still under development. It's a good idea to do it manually first to get the hang of it.

---

### Post by supertails on 2008-01-27
Okay but how do I fix my graphics and sound.

---

### Post by danwood76 on 2008-01-27
Your graphics and sound are loaded with kernel modules, not the actual kernel itself. Recompiling probably wont give you sound or graphics.

You probably need to compile the ALSA sound drivers and possibly install proprietry graphics drivers.
What sound card and graphics card do you have?

regards,
Danny

-- edit --

Post the result of: ```
 lspci 
```

---

### Post by supertails on 2008-01-27
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.


tails@tails-laptop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:01.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (Internal gfx)
00:04.0 PCI bridge: ATI Technologies Inc Unknown device 7914
00:05.0 PCI bridge: ATI Technologies Inc Unknown device 7915
00:06.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 2)
00:12.0 SATA controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
00:13.0 USB Controller: ATI Technologies Inc SB600 USB (OHCI0)
00:13.1 USB Controller: ATI Technologies Inc SB600 USB (OHCI1)
00:13.2 USB Controller: ATI Technologies Inc SB600 USB (OHCI2)
00:13.3 USB Controller: ATI Technologies Inc SB600 USB (OHCI3)
00:13.4 USB Controller: ATI Technologies Inc SB600 USB (OHCI4)
00:13.5 USB Controller: ATI Technologies Inc SB600 USB Controller (EHCI)
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 14)
00:14.1 IDE interface: ATI Technologies Inc SB600 IDE
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
00:14.3 ISA bridge: ATI Technologies Inc SB600 PCI to LPC Bridge
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon X1200 Series
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller (rev 01)
14:06.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
14:06.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
14:06.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
14:06.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
14:06.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
tails@tails-laptop:~$

---

### Post by danwood76 on 2008-01-27
Right your graphics driver should be fairly easy to get sorted.
Just go into the restricted drivers manager (System -> Administration -> Restricted Drivers Manager) and enable the ati driver. You may need to reboot after this is done to complete the install.

The sound could be a little harder.
I recomend compiling the ALSA driver from scratch, the version shipped with gutsy is a bit out dated and doesnt seem to work with everyone.

Go here to get the driver source code: [http://www.alsa-project.org/main/index.php/Main_Page](http://www.alsa-project.org/main/index.php/Main_Page)
and I found a guide to compiling them here: [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto) folow the bit titled 'Update to the Latest Version of ALSA'
Hopefully you should be able to get sound working also.

Any problems obviously post here.

regards,
Danny

---

### Post by supertails on 2008-01-27
I've already freed the restricted driver but it still doesn't let me do the eye candy effects and I try building the ALSA driver from scratch but I got this.

tails@tails-laptop:~$ sudo mkdir -p /usr/src/alsa
[sudo] password for tails:
tails@tails-laptop:~$ sudo mkdir -p /usr/src/alsa
tails@tails-laptop:~$ cd /usr/src/alsa
tails@tails-laptop:/usr/src/alsa$ sudo cp ~/downloads/alsa*
cp: missing destination file operand after `/home/tails/downloads/alsa*'
Try `cp --help' for more information.
tails@tails-laptop:/usr/src/alsa$ sudo tar xjf alsa-driver*.bz2
tar: alsa-driver*.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
tails@tails-laptop:/usr/src/alsa$ sudo tar xjf alsa-lib*.tar.bz2
tar: alsa-lib*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
tails@tails-laptop:/usr/src/alsa$ sudo tar xjf alsa-utils*.tar.bz2
tar: alsa-utils*.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
tails@tails-laptop:/usr/src/alsa$

---

### Post by danwood76 on 2008-01-27
In regards to alsa, use the GUI to place and untar the source archives into a common folder.
I like to keep all my builds in ~/build. You dont need to place them in /usr/src/

Then navigate to this directory in the terminal and continue the build process from the guide.

About your graphics, you may have an xorg.conf problem.
can you post the result of:
```
cat /etc/X11/xorg.conf
```

regards,
Danny

---

### Post by supertails on 2008-01-27
tails@tails-laptop:~$ cat /etc/X11/xorg.conf
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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "fglrx"
        Busid           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       30-70
        Vertrefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
        Inputdevice     "Synaptics Touchpad"
EndSection
Section "Module"
        Load            "glx"
EndSection
Section "Extensions"
        Option          "Composite"     "0"
EndSection
tails@tails-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for tails:
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080127165728
tails@tails-laptop:~$

---

