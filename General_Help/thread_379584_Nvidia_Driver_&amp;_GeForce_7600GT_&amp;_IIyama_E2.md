---
title: "Nvidia Driver &amp; GeForce 7600GT &amp; IIyama E2200WS"
date: 2007-03-08
forum: General Help
---

### Post by MrQuincle on 2007-03-08
The problem is very simple. I can only use the "nv" driver, not the "nvidia" driver. My screen now looks fuzzy. It is not sharp. Before I upgraded my kernel I managed to install the "nvidia" driver. I had a splash screen when I logged in. Now I can't manage it anymore. If you have any suggestions, I'll not disappoint you in actually following your directions... (Except throwing the thing out of the window et. :) )

**uname -r** 2.6.15-28-386

**GeForce 7600 GT**
I have a GeForce 7600 GT. That driver is listed in the supported packages list at [http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8762/README/appendix-a.html)

Yes, there is she, almost at the bottom: the GeForce 7600 GT with Device PCI ID: 0x0391.

**nvidia-glx**
So, according to [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) I can use nvidia-glx. 

**Dapper Drake**
I run Ubuntu Dapper Drake, no Edgy or another distribution. 

**What's on my system now?**
The command issued: lspci | grep -i nvidia 
It has a lot of results, I don't know if they are good of bad.

```
0000:00:00.0 Host bridge: nVidia Corporation: Unknown device 0071 (rev c1)
0000:00:00.1 RAM memory: nVidia Corporation: Unknown device 007f (rev a1)
0000:00:00.2 RAM memory: nVidia Corporation: Unknown device 0075 (rev a1)
0000:00:00.3 RAM memory: nVidia Corporation: Unknown device 006f (rev a1)
0000:00:00.4 RAM memory: nVidia Corporation: Unknown device 00b4 (rev a1)
0000:00:01.0 RAM memory: nVidia Corporation: Unknown device 0076 (rev a1)
0000:00:01.1 RAM memory: nVidia Corporation: Unknown device 0078 (rev a1)
0000:00:01.2 RAM memory: nVidia Corporation: Unknown device 0079 (rev a1)
0000:00:01.3 RAM memory: nVidia Corporation: Unknown device 007a (rev a1)
0000:00:01.4 RAM memory: nVidia Corporation: Unknown device 007b (rev a1)
0000:00:01.5 RAM memory: nVidia Corporation: Unknown device 007c (rev a1)
0000:00:01.6 RAM memory: nVidia Corporation: Unknown device 007d (rev a1)
0000:00:02.0 PCI bridge: nVidia Corporation: Unknown device 007e (rev a2)
0000:00:05.0 PCI bridge: nVidia Corporation: Unknown device 007e (rev a2)
0000:00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
0000:00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
0000:00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
0000:00:0a.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
0000:00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
0000:00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
0000:00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
0000:00:0e.0 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
0000:00:0e.1 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
0000:00:0e.2 IDE interface: nVidia Corporation MCP55 SATA Controller (rev a2)
0000:00:0f.0 PCI bridge: nVidia Corporation: Unknown device 0370 (rev a2)
0000:00:0f.1 0403: nVidia Corporation: Unknown device 0371 (rev a2)
0000:00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
0000:00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
0000:00:13.0 PCI bridge: nVidia Corporation: Unknown device 0376 (rev a2)
0000:00:17.0 PCI bridge: nVidia Corporation: Unknown device 0375 (rev a2)
0000:00:18.0 PCI bridge: nVidia Corporation: Unknown device 0377 (rev a2)
0000:04:00.0 VGA compatible controller: nVidia Corporation: Unknown device 0391 
```

It seems not good that 0391 is also "unknown".

**What's on my machine again?**
Let us take a look at what exist on my machine: aptitude search nvidia

```
c   nvidia-glx                      - NVIDIA binary XFree86 4.x/X.Org driver
p   nvidia-glx-dev                  - NVIDIA binary XFree86 4.x/X.Org driver dev
p   nvidia-glx-legacy               - NVIDIA binary XFree86 4.x/X.Org 'legacy' d
p   nvidia-glx-legacy-dev           - NVIDIA binary XFree86 4.x/X.Org 'legacy' dv   nvidia-kernel-1.0.7174          -
v   nvidia-kernel-1.0.8762          -
v   nvidia-kernel-1.0.8776          -
ciA nvidia-kernel-common            - NVIDIA binary kernel module common files
p   nvidia-kernel-source            - NVIDIA binary kernel module source
p   nvidia-legacy-kernel-source     - NVIDIA binary 'legacy' kernel module sourc
p   nvidia-settings                 - Tool of configuring the NVIDIA graphics dr
p   nvidia-xconfig                  - The NVIDIA X Configuration Tool
```

**Is nvidia-glx not installed?**
Ai, it's not installed?: aptitude show nvidia-glx

```
Package: nvidia-glx
State: not installed (configuration files remain)
Version: 1.0.8776+2.6.15.12-28.1
Priority: optional
Section: restricted/x11
Maintainer: Ubuntu Kernel Team <kernel-team@lists.ubuntu.com>
Uncompressed Size: 12.5M
Depends: nvidia-kernel-1.0.8776, xserver-xorg-core (>= 1:0.99.0-1), libglu1-mesa         | libglu1, libatk1.0-0 (>= 1.9.0), libc6 (>= 2.3.4-1), libglib2.0-0 (>=         2.10.0), libgtk2.0-0 (>= 2.8.0), libpango1.0-0 (>= 1.12.2), libx11-6,
         libxext6
Suggests: nvidia-kernel-source (>= 1.0.8776)
Conflicts: nvidia-glx-src, nvidia-settings, nvidia-xconfig
Replaces: nvidia-glx-src
Provides: xserver-xorg-driver
Provided by: nvidia-glx-legacy, nvidia-glx-legacy
Description: NVIDIA binary XFree86 4.x/X.Org driver
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
of OpenGL applications via a direct-rendering X Server and support the newer
GeForce, nForce and Quadro families of NVIDIA chipsets.  AGP, TV-out and flat
panel displays are also supported.

If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy
package instead of this one.

To enable the driver, run "sudo nvidia-glx-config enable".
```

**Install nvidia-glx**
Okay, so let's install nvidia-glx: sudo aptitude install nvidia-glx

```
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  dpkg-dev fakeroot libc6-dev
The following NEW packages will be automatically installed:
  debconf-utils debhelper devscripts dpatch html2text kernel-package
  linux-libc-dev linux-restricted-modules-2.6.15-27-386
  nvidia-kernel-common nvidia-kernel-source patchutils
The following NEW packages will be installed:
  debconf-utils debhelper devscripts dpatch html2text kernel-package
  linux-libc-dev linux-restricted-modules-2.6.15-27-386 nvidia-glx
  nvidia-kernel-common nvidia-kernel-source patchutils
The following packages will be REMOVED:
  linux-kernel-headers
0 packages upgraded, 15 newly installed, 1 to remove and 0 not upgraded.
Need to get 11.3MB/19.2MB of archives. After unpacking 48.8MB will be used.
The following packages have unmet dependencies:
  fakeroot: Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.4 is installed.
  dpkg-dev: Depends: dpkg (>= 1.13.20) but 1.13.11ubuntu7 is installed.
  libc6-dev: Depends: libc6 (= 2.4-1ubuntu12) but 2.3.6-0ubuntu20.4 is installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
dpkg-dev [1.13.11ubuntu7 (dapper-updates, now)]
fakeroot [1.5.6ubuntu2 (dapper, dapper)]

Keep the following packages at their current version:
kernel-package [Not Installed]
libc6-dev [Not Installed]
linux-restricted-modules-2.6.15-27-386 [Not Installed]
nvidia-glx [Not Installed]
nvidia-kernel-common [Not Installed]
nvidia-kernel-source [Not Installed]

Score is -16

Accept this solution? [Y/n/q/?]
```

**Install dpkg-dev & fakeroot**
So, as I understand, libc6-dev will probably not be needed, so can be safely omitted from installation. And instead of a new version of dkpg-dev and fakeroot, old versions will be installed. Versions that can handle the old version (the Dapper Drake version) of libc6 I have on my machine.

It will remove linux-kernel-headers. For what it is worth... ;-)

The previous time all kind of packages were hold back instead of updated. That's not funny.

It reminds me tenderly:

```
The following NEW packages will be automatically installed:
  debconf-utils linux-libc-dev
The following NEW packages will be installed:
  debconf-utils linux-libc-dev
The following packages will be REMOVED:
  linux-kernel-headers
0 packages upgraded, 2 newly installed, 1 to remove and 0 not upgraded.
Need to get 30.9kB/1800kB of archives. After unpacking 1196kB will be freed.
Do you want to continue? [Y/n/?]

Writing extended state information... Done
Media Change: Please insert the disc labeled 'Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)' in the drive '/cdrom/' and press enter
```

**Edge Eft Hickup!**
Huh!? I've no Edgy Eft. Seems there is something terribly wrong on my system.

**Distro check**
Check: cat /etc/lsb-release```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.06
DISTRIB_CODENAME=dapper
DISTRIB_DESCRIPTION="Ubuntu 6.06.1 LTS"
```

**Dapper Drake**
After entering "no" one time, another option for dependencies is offered. Happily it does not say anything about Edgy this time. But, still, it's weird. Seems there is a somewhere an Edgy package on my system. Repeating the install of nvidia-glx:

```
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
dpkg-dev [1.13.11ubuntu6 (dapper, dapper)]
fakeroot [1.5.6ubuntu2 (dapper, dapper)]
libc6-dev [2.3.6-0ubuntu20.4 (dapper-updates)]

Keep the following packages at their current version:
linux-kernel-headers [2.6.11.2-0ubuntu18 (dapper, dapper, now)]
linux-libc-dev [Not Installed]

Score is -80

Accept this solution? [Y/n/q/?]
```

However, regretfully, my CD doesn't seem to be good enough.

```
Media Change: Please insert the disc labeled 'Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060806.1)' in the drive '/cdrom/' and press enter

aptitude: download_signal_log.cc:67: virtual bool download_signal_log::MediaChange(std::string, std::string): Assertion `rval != -1' failed.
Aborted
```

**Intermediate quickie with my cdrom player**
Mmm, that's not weird. I don't use /cdrom to mount, so do it before manually and repeat the previous step.

sudo mount /dev/cdrom /cdrom

**Install nivdia-glx**
Now for real! Funny, that same score is now -20. Magic!

```
Resolving dependencies...
The following actions will resolve these dependencies:

Install the following packages:
dpkg-dev [1.13.11ubuntu7 (dapper-updates, now)]
fakeroot [1.5.6ubuntu2 (dapper, dapper)]
libc6-dev [2.3.6-0ubuntu20.4 (dapper-updates)]

Keep the following packages at their current version:
linux-kernel-headers [2.6.11.2-0ubuntu18 (dapper, dapper, now)]
linux-libc-dev [Not Installed]

Score is -20
```

**Installing...**
Till now it's doing fine... :-D The linux-restricted-modules seems big.

**Enable**
And now: sudo nvidia-glx-config enable

**Restart Xserver**
now restarting the xserver should show a nvidia splash screen [Ctrl+Alt+Backspace]

**Nothing!!!**
Doesn't work at all. Manually changing the /etc/X11/xorg.conf driver "nv" to "nvidia" does not help. 

**And all kind of kept-back packages!**
And now I'm back again at, grrr. E.g. with an aptitude dist-upgrade.
```

The following packages have been kept back:
  dpkg-dev fakeroot libc6-dev
0 packages upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
```

**Problem!!**
Mmm. what's the problem...?

One of the xorg.conf files I have used:
```


Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"

	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "IIyama E2200WS"
    HorizSync       28.0 - 84.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
    Modeline  	    "1680x1050" 149.00  	1680 1760 1944 2280
						1050 1050 1052 1089 
    # http://en.wikipedia.org/wiki/XFree86_Modeline
    # Pixel clock frequency is 149,000,000 Hz.
    # With highest resolution, the refresh rate becomes:
    #   149000000/(2280*1089) = 60.01 Hz (slightly too much)
EndSection

Section "Device"
    Identifier     "NVIDIA GeForce 7600GT"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA GeForce 7600GT"
    Monitor        "IIyama E2200WS"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

If anyone can help me, thanks a lot! :guitar: I'm busy on it for days by now.

---

### Post by MrQuincle on 2007-04-30
For whom it may concern. I solved my problem after an upgrade to Feisty. Does have a nice GUI named the Restricted Drivers Manager. Not directly related with my problem, but that's not the point. 


Choose in Feisty Fawn(!) System - Administration - Restricted Drivers Manager, the driver and enable it.

Fill in [http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl) values:
Sync rate: 31.0 - 83.0 kHz, refr. rate 56-75 Hz, max dot clock 162 Mhz, resolution 1680x1050, refr. rate 0, dot clock 146.250 en choose one with interlace and one without.

Edit conf. file: sudo gedit /etc/X11/xorg.conf:
```

  Section "Monitor"
    Identifier "Generic Monitor"
    Option "DPMS"
    Horizsync 31-83
    Vertrefresh 56-75
    Modeline "1680x1050@57" 146.25 1680 1712 2264 2296 1050 1071 1081 1103
    Modeline "1680x1050@115i" 146.25 1680 1712 2264 2296 1050 1071 1081 1103 interlace
  EndSection

    SubSection "Display"
      Depth 24
      Modes "1024x768" "800x600" "640x480" "1680x1050@57" "1680x1050@115i"
    EndSubSection

```

Don't forget them to add at the modes in the display section.

I played a little bit with nvidia-settings, but it's now on auto. However, in the System - Preferences - Screen Resolution dialog, I choose 1680x1050 on 54 Hz, and contrary to 53 and 55 Hz, the screen is now very clear. The letters are not fuzzy anymore. Excellent!!

:guitar: :popcorn:

---

### Post by die-andis on 2007-06-02
Hello, 

i have some problems with the IIyama E2200WS on my kubuntu feisty. The nvidia drivers works fine(Nvidia FX5200 AGP), but the screen (connected with dvi) can´t display the 1680x1050 resolution (with single- and duallinkcable). It works only with 1280x1024. Connected with D-SUB everything is fine (with full resolution).

Here is my xorg.conf

Section "Device"
	Identifier	"Standardgrafikkarte"
 	Driver		"nvidia"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Standardbildschirm"
	Option		"DPMS"
	HorizSync	31-83
	VertRefresh	56-75
        Modeline "1680x1050@57" 146.25 1680 1712 2264 2296 1050 1071 1081 1103
       Modeline "1680x1050@115i" 146.25 1680 1712 2264 2296 1050 1071 1081 1103 interlace
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Standardgrafikkarte"
	Monitor		"Standardbildschirm"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
#		Modes		"1680x1050"
                 Modes "1680x1050@57" "1680x1050@115i"
	EndSubSection
EndSection

i have no ideas what can i do, to get my monitor works with dvi.

P.S. Sorry for the beginner-english

---

### Post by der_joachim on 2007-06-03
Die-andis: 
I had a GeForce 5600 with the same problem. Does your card happen to be made by MSI? There's lots of postings on the internet with similar issues, all MSI related. AFAIK a real solution has never been found.

---

### Post by die-andis on 2007-06-03
hello joachim,

yes its a card from msi. o no :-(

Andreas

---

