---
title: "updates killed ubuntu"
date: 2007-01-21
forum: General Help
---

### Post by nami on 2007-01-21
ubuntu wanted to install some updates yesterday so i let it, when i restarted my computer, it will no longer start...

something about xorg?

---

### Post by ajmorris on 2007-01-21
I am afraid if i am to help you i will require some more info. What is the error you get concerning xorg?

---

### Post by nami on 2007-01-21
Thanks for offering to help.  I have no idea how to get the error message here except using my phone camera:

[[IMG]http://img154.imageshack.us/img154/3808/dsc009115xb.th.jpg[/IMG]](http://img154.imageshack.us/img154/3808/dsc009115xb.jpg)[[IMG]http://img295.imageshack.us/img295/7135/dsc009123mu.th.jpg[/IMG]](http://img295.imageshack.us/img295/7135/dsc009123mu.jpg)[[IMG]http://img95.imageshack.us/img95/6360/dsc009139bv.th.jpg[/IMG]](http://img95.imageshack.us/img95/6360/dsc009139bv.jpg)[[IMG]http://img95.imageshack.us/img95/44/dsc009142qp.th.jpg[/IMG]](http://img95.imageshack.us/img95/44/dsc009142qp.jpg)[[IMG]http://img95.imageshack.us/img95/6153/dsc009497aq.th.jpg[/IMG]](http://img95.imageshack.us/img95/6153/dsc009497aq.jpg)

I had nvidia, twinview, and berly working before the update

---

### Post by Enverex on 2007-01-21
You need to reinstall the nVidia kernel driver (which should be pretty obvious from the error).

---

### Post by feest on 2007-01-21
drop to command line and type "sudo apt-get remove-nvidia-glx" and reboot, does it start x?

we may be able to give a more precise help if you tell us wich version of ubuntu you have, if you got bery, compiz, or something like that installed. when this exactly happend (first boot after update?) and maybe you could post you xorg.conf (but first try the first line :P)

---

### Post by nami on 2007-02-02
last time i installed the graphics card drivers from the script on this site:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

how do i do that now that i don't have a working gnome environment?  how do i download that script again and run it?

---

### Post by nami on 2007-02-03
anyone?

---

### Post by Enverex on 2007-02-03
Use Lynx or links to browse the nVidia site and download the nVidia drivers then just run the downloaded file, it's all very straightforward.

---

### Post by nami on 2007-02-03
You can download stuff from the terminal/commandline?

---

### Post by fenian on 2007-02-03
The envy script should still be on your computer so after x fails to start and sends you to the command line login and run envy,choose the option to remove the nvidia drivers,then reinstall the drivers.I think I did it like that once.

---

### Post by nami on 2007-02-03
i remember downloading the envy script to my desktop and after installing it i deleted it from the desktop. #-o

---

### Post by fenian on 2007-02-03
He has it as a deb now could you get it with 

> wget htp://albertomilone.com/ubuntu/nvidia/scripts/envy_0.8.1-0ubuntu3_all.deb

and then install it with sudo dpkg -i ?

---

### Post by nami on 2007-02-04
> **feest said:**
> drop to command line and type "sudo apt-get remove-nvidia-glx" and reboot, does it start x?

we may be able to give a more precise help if you tell us wich version of ubuntu you have, if you got bery, compiz, or something like that installed. when this exactly happend (first boot after update?) and maybe you could post you xorg.conf (but first try the first line :P)

i just tried this and it said, invalid command.

---

### Post by nami on 2007-02-04
> **fenian said:**
> He has it as a deb now could you get it with 



and then install it with sudo dpkg -i ?

i also just tried this and it downloaded and installed without an error but i still cant get into gnome.  i get the same error as the error i posted in the original post.

---

### Post by nami on 2007-02-05
I'm hoping I don't have to do a clean ubuntu install, as it took me ages to get it the way I want it.

Help

---

### Post by fenian on 2007-02-05
After you installed envy were you able to run it from the command line?

---

### Post by nami on 2007-03-06
yes, i was able to do that.  but it didn't fix the problem.

how can i revert back to the original config file, because at the moment, i can't get in at all.  does the automated nvidia driver installer make a backup of the config file?

help...  i've been without ubuntu for months.

---

### Post by tyler_roach on 2007-03-06
Dude, just do:

sudo dpkg-reconfigure -phigh xserver-xorg

And choose the vesa drivers or the default "nvidia" ones (I'm not sure what they're called; I use ati.)

That should get  you your GUI back until you are able to reinstall the proprietary drivers.

However, someone else on these forums had the same problem recently, and a simple:

sudo apt-get install --reinstall nividia-glx

Solved his problem.. I hope that works for you.

BTW Don't event think about reinstalling.

---

### Post by nami on 2007-03-06
thanks

i will try this out first thing when i get home.

---

### Post by nami on 2007-03-07
ok that worked

sudo dpkg-reconfigure -phigh xserver-xorg

thanks

i then re-installed the nvidia drivers and everything works fine.  only problem is when i change some settings from the nvidia settings, it does not remember when the next time i login...

any ideas why?

---

### Post by feest on 2007-03-07
try this command code: 

cp xorg.conf xorg-old.conf
cp xorg.conf.backup xorg.conf

and boot again...

---

### Post by nami on 2007-03-07
i tried that and it says "no such file or folder found".

---

### Post by mrmonday on 2007-03-07
I'm not sure why it won't remember your settings, but I had the same problem... It seems to be when there is a kernel update. I have found the solution is to hit enter to get to the command line, then run envy. I hope this helps.:)

---

### Post by shakumafu on 2007-03-07
run nvidia-settings in the terminal and change your settings and check to see if it spits out an error

---

### Post by aidanr on 2007-03-07
nvidia settings are not automatically reapplied, you will need to add ```
nvidia-settings -l
``` to your startup programs, system -> preferences -> sessions -> startup programs

---

### Post by nami on 2007-03-08
Thanks, I'll try that tonight.

However, when I try changing the settings, I get a message saying something like "was unable to apply the changes because of the following reasons".  I cant remember exactly what it said so I will get a screenshot probably tonight and post it up.

Thanks for the help so far,  appreciated very much.

---

### Post by nami on 2007-03-10
here is a error message i get when i try to change the nvidia settings

[[IMG]http://img176.imageshack.us/img176/3353/screenshotow3.th.png[/IMG]](http://img176.imageshack.us/img176/3353/screenshotow3.png)

any ideas how to fix this?

when i restart, it reverts back to a screen-0 only at 1024x768, when it should be both screens at 1280x1024.

---

### Post by tyler_roach on 2007-03-11
Could you post the results of lspci and your xorg.conf file?

---

### Post by nami on 2007-03-11
Absolutely

results of lspci

> nami@nami-desktop:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev a2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev a3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80)
01:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
05:00.0 VGA compatible controller: nVidia Corporation Unknown device 0160 (rev a1)
nami@nami-desktop:~$

results of xorg.conf

> # nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Fri Dec 15 10:12:14 PST 2006

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
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
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
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
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
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

---

### Post by tyler_roach on 2007-03-12
Back up your xorg.conf, and try manually adding the mode "1280x1024" to each "Mode" line in your "Screen" and "Display" sections.

---

### Post by nami on 2007-03-12
Thanks,

I'll try that tonight.

---

### Post by nami on 2007-04-17
If I install ubuntu 7.04 when its released, will it break the graphics drivers again, and ruin my dual display?

---

