---
title: "Browser operates slower in Ubuntu.  Any suggestions?"
date: 2006-12-12
forum: General Help
---

### Post by emarkay on 2006-12-12
I use the Mozilla "SeaMonkey" suite here and in my Windows 98SE partition.  In preparing to switch to Ubuntu for all my "online" use, I have been using both versions frequently.

Both are the 1.1b versions, and here is the data from the Linux one:
Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1) Gecko/20061101 SeaMonkey/1.1b
My PC is a Dell Optiplex GX110 (733 mHz P3)with 384Megs of RAM.  

In Ubuntu, accessing new browser pages or new tabs takes about double the time, and the page display (loading)takes noticeably longer.

All browser settings and options are identical, and as far as I know both OS optimization features are set set for performance.  I have the IPV6 feature disabled in Ubuntu, also.

What could be causing this?

---

### Post by taurus on 2006-12-12
Did you install a driver for your graphic card in Ubuntu?

---

### Post by Scheater5 on 2006-12-12
You could always try Swiftfox.  I've heard it denounced lately as the owner refuses to release the source code - but if that bit of a philosophical doesn't bother you, give it a shot.  I think it's in the repositories - probably have to have either the universe or the multiverse enabled.  If so just 
```
sudo apt-get install swiftfox
```
or 
```
sudo aptitude install swiftfox
```
But I'm not positive about that.  If not, I know Automatix will install it.

---

### Post by pgilmon on 2006-12-12
Have you disabled the option in the browser or in the whole system?

If you want to know if it is disabled system-wide, open the console and type:

lsmod | grep ipv6

If it doesn't return anything then it is disabled in the whole system. If it returns something, then it is still enabled and I suggest you should disable it. You can find instructions on how to do it [here]("http://computeraddict.neo-addict.net/guides/tut_ubuntudisableipv6").

You can also try setting up a dns cache. If the DNS are the problem, it could improve your speed quite a lot. There is a tutorial [here]("http://ubuntu.wordpress.com/2006/08/02/local-dns-cache-for-faster-browsing/").

---

### Post by emarkay on 2006-12-12
Aha! Graphics speed performance...  Never thought it may be that - but alas, this PC has the Intel 
82810E Graphics Controller (4 Mb), Intel i752 Video Accelerator built in to the mainboard. 
I have the latest Windows drivers, but hmmmm, I never thought of Linux drivers...  Let me investigate.

---

### Post by taurus on 2006-12-12
What "Driver" do you use for your graphic card in /etc/X11/xorg.conf?

---

### Post by emarkay on 2006-12-12
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=178&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=178&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)


a TAR.GZ and a RPM are available.  Now to figure how to install them..  (more research) 

THANKS!

---

### Post by taurus on 2006-12-12
> **emarkay said:**
> [http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=178&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=178&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)


a TAR.GZ and a RPM are available.  Now to figure how to install them..  (more research) 

THANKS!

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by emarkay on 2006-12-12
But then again, it looks like ther already is a driver there:

Log file: "/var/log/Xorg.0.log", Time: Tue Dec 12 09:33:47 2006
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "E771-4"
(**) |   |-->Device "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
****

(II) Wacom driver level: 47-0.7.2 $
(II) I810: Driver for Intel Integrated Graphics Chipsets: i810, i810-dc100,
	i810e, i815, i830M, 845G, 852GM/855GM, 865G, 915G, E7221 (i915),
	915GM, 945G, 945GM
(II) Primary Device is: PCI 00:01:0
(--) Chipset i810e found
****
Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
	Monitor		"E771-4"
	DefaultDepth	24
	SubSection "Display"
*****
Now, according to:
[http://www.die.net/doc/linux/man/man4/i810.4.html](http://www.die.net/doc/linux/man/man4/i810.4.html)
"The driver supports hardware accelerated 3D via the Direct Rendering Infrastructure (DRI), but only in depth 16 for the i810/i815..."

Would this make the card faster, and therefore should I set my Depth to 16? 

Thanks.

---

### Post by taurus on 2006-12-12
I guess you are using i810!!!  Is that what it says in /etc/X11/xorg.conf?  You can upgrade it to 915resolution in the repos...

```
cat /etc/X11/xorg.conf
```

---

### Post by emarkay on 2006-12-12
Yea it's an 810.  
I already found the 915resolution and installed it via Synaptic.  I presumed it was an "automatic install".  I will check out the website mentioned there on the info section:
[http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)

****

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
        Load    "dbe"
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
        Identifier      "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
        Driver          "i810"
        BusID           "PCI:0:1:0"
EndSection

Section "Monitor"
        Identifier      "E771-4"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82810E DC-133 CGC [Chipset Graphics Controller]"
        Monitor         "E771-4"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
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




915Resolution gives me the following:

"Intel chipset detected.  However, 915resolution was unable to determine the chipset type.
Chipset Id: 71248086
Please report this problem to [email]xxxxxxxx@yahoo.com[/email]"

Now I think we are on to something....

---

### Post by emarkay on 2006-12-12
> **pgilmon said:**
> Have you disabled the option in the browser or in the whole system?

If you want to know if it is disabled system-wide, open the console and type:

lsmod | grep ipv6

If it doesn't return anything then it is disabled in the whole system. If it returns something, then it is still enabled and I suggest you should disable it. You can find instructions on how to do it [here]("http://computeraddict.neo-addict.net/guides/tut_ubuntudisableipv6").


I get :
ipv6                  286976  22

So I need to look in to this - but I think it's the graphics card, and I am finding a LOT of "issues" with this chipset.  Mostly on 3D things, but I presume that these could also be slowing down it's display speed.

Thanks.

---

### Post by emarkay on 2006-12-13
Well changing default bitrate to 16 (from 24) sped things up a lot, but I still want to get rid of IPv6.  I tried the suggestion from this page:
[http://computeraddict.neo-addict.net/guides/tut_ubuntudisableipv6](http://computeraddict.neo-addict.net/guides/tut_ubuntudisableipv6)

"sudo echo "ipv6" >> /etc/modprobe.d/blacklist"
and I get this:
"bash: /etc/modprobe.d/blacklist: Permission denied"

Anyone know why?

---

### Post by taurus on 2006-12-13
Try to edit it from a terminal then!!!

```
gksudo gedit /etc/modprobe.d/blacklist
```
Then, add ipv6 to the end of it...

---

### Post by emarkay on 2006-12-13
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

#because I want to
blacklist ipv6

******

Correct?

---

### Post by emarkay on 2007-02-01
Reinstalling a new, clean Ubuntu speed things up just a bit.  Marking this "Resolved".

---

