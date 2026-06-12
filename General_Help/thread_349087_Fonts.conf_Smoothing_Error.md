---
title: "Fonts.conf Smoothing Error"
date: 2007-01-29
forum: General Help
---

### Post by undeadsoldier on 2007-01-29
Hi guys,

I can't for the life of me, figure out why this isn't working, would somebody be able to help me out on this one? Cheers!

My fonts.conf file:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>
        <match target="font">
                <test compare="more" name="pixelsize" qual="any">
                        <double>0</double>
                <test>
                <test compare="less" name="pixelsize" qual="any">
                        <double>7</double>
                <test>
                <edit name="rgba" mode="assign">
                        <const>rgb</const>
                </edit>
                <edit name="autohint" mode="assign">
                        <bool>false</bool>
                </edit>
                <edit name="antialias" mode="assign">
                        <bool>false</bool>
                </edit>
                <edit name="hinting" mode="assign">
                        <bool>false</bool>
                </edit>
                <edit name="hintstyle" mode="assign">
                        <const>hintnone</const>
                </edit>
        </match>

        <match target="font">
                <edit name="rgba" mode="assign">
                        <const>rgb</const>
                </edit>
                <edit name="autohint" mode="assign">
                        <bool>true</bool>
                </edit>
                <edit name="antialias" mode="assign">
                        <bool>true</bool>
                </edit>
                <edit name="hinting" mode="assign">
                        <bool>true</bool>
                </edit>
                <edit name="hintstyle" mode="assign">
                        <const>hintslight</const>
                </edit>
        </match>

        <match target="font">
                <test name="weight" compare="more">
                        <const>medium</const>
                </test>
                <edit name="autohint" mode="assign">
                        <bool>false</bool>
                </edit>
        </match>

        <selectfont>
                <rejectfont>
                        <pattern>
                                <patelt name="scalable">
                                        <bool>false</bool>
                                </patelt>
                        </pattern>
                </rejectfont>
        </selectfont>

</fontconfig>
```

I am trying to make all the fonts from size 8 up have smooth fonts, where size 7 down has no smoothing at all.

Greatly appriciate any help!

---

### Post by undeadsoldier on 2007-01-29
[SIZE="1"]Boy do I feel stupid.... true = true is supposed to be false.... UGH![/SIZE]

Nope, still doesn't work when I set it to false :(

---

### Post by undeadsoldier on 2007-01-29
Anybody?

---

### Post by kerry_s on 2007-01-29
You have it in the right place /home/you/.fonts.conf right? Do you logout and back in for the changes to take effect? Here's mine if you want to try it->

```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "fonts.dtd">
<fontconfig>

	<!-- Replace Courier with a better-looking font -->
	<match target="pattern" name="family">
		<test name="family" qual="any">
			<string>Courier</string>
		</test>
		<edit name="family" mode="assign">
			<!-- Other choices - Courier New, Luxi Mono -->
			<string>Verdana</string>
		</edit>
	</match>

	<match target="font">
		<edit name="rgba" mode="assign">
			<const>rgb</const>
		</edit>
		<edit name="autohint" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="antialias" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="hinting" mode="assign">
			<bool>true</bool>
		</edit>
		<edit name="hintstyle" mode="assign">
			<const>full</const>
		</edit>
	</match>

	<!-- Disable autohint for bold fonts, otherwise they look *too* bold -->
	<match target="font">
   		<test name="weight" compare="more">
			<const>light</const>
		</test>
   		<edit name="autohint" mode="assign">
			<bool>false</bool>
		</edit>
	</match>

	<!-- Reject bitmap fonts in favour of Truetype, Postscript, etc. -->
	<selectfont>
		<rejectfont>
			<pattern>
				<patelt name="scalable">
					<bool>false</bool>
				</patelt>
			</pattern>
		</rejectfont>
	</selectfont>

</fontconfig>
```

---

### Post by undeadsoldier on 2007-01-29
Nothing seems to be working for me :(

Thanks kerry for a response :) but the config you gave me enables antialiasing on all fonts.

---

### Post by undeadsoldier on 2007-01-29
don't worry about it.

I just started my X session with

"xstart -- -dpi 75"

cheers :)

---

### Post by kerry_s on 2007-01-29
Put that in your xorg.conf, i use 100x100 for mine, i don't even have 75dpi installed. :D 

```
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Mon Oct 16 22:13:07 PDT 2006

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

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "dbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
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

Section "Monitor"
    Identifier     "A70"
    Option         "DPMS"
    Option         "UseEdidDpi" "false"
    Option         "DPI" "100 x 100"
    Option         "HWCursor" "off"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
    Driver         "nvidia"
EndSection

Section "Screen"

# Only the official NVIDIA driver supports twinview
# these setting are an example
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV18 [GeForce4 MX 4000 AGP 8x]"
    Monitor        "A70"
    DefaultDepth    24
    Option         "SecondMonitorHorizSync" "31.468-71.0"
    Option         "SecondMonitorVertRefresh" "56.0-85.0"
    Option         "ConnectedMonitor" "crt,crt"
    Option         "RenderAccel" "true"
    Option         "nologo" "true"
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "RightOf"
    Option         "MetaModes" "1280x1024, 1280x1024"
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "FALSE"
EndSection


```

---

