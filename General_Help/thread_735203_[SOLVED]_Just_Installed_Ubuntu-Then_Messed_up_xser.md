---
title: "[SOLVED] Just Installed Ubuntu-Then Messed up xserver x-org HELP ME PLEASE"
date: 2008-03-25
forum: General Help
---

### Post by Takido on 2008-03-25
I have an [COLOR="Red"]Acer Aspire 3000 [/COLOR] and i am a total linux noob. I know nothing about my computer specs(its just an Acer Aspire notebook) and after i installed and updated i wanted to give myself widescreen resolution. So i ran the "sudo dpkg-reconfigure xserver-xorg" went through a bunch of stuff. And logged out. When i went to log back in i got an error saying that my x-org is all screwed up. So i tried to rerun it and fix it. But i don't know if in selecting the right things and when i get to choose my bit rate or w/e it is (24 bits) it leaves the dpkg reconfigure thing and goes back to the command line. I acn't fix my problem and when i boot windows i can't see the partition that linux is on so i can fix it? I don't mind re-installing linux but it would be nice if i could fix this problem without re-installing(as long as it's not too hard) if i can't please, please help me re-install.(without creating a new partition)

Thanks in advance and i hope to see somone post my solution before i get home from school.
Thanks.

---

### Post by Rocket2DMn on 2008-03-25
To get back to your original configuration, run
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
Once back in the GUI, please post the outputs of these commands so we can help you get X setup with the correct resolution.
```
lspci | grep VGA
cat /etc/X11/xorg.conf
```
Please tell us your monitor's native resolution (I'm assuming this is the resolution you want - the max widescreen res).

---

### Post by Takido on 2008-03-25
Ok. Once i get home i'll try that out and see.
Thanks.
Stay Tuned got about another 2 hours till i get home.

---

### Post by Takido on 2008-03-25
OK i got home and i ran that "sudo dpkg-reconfigure xserver-xorg -phigh" (JUST FOR REFERENCE I AM GOING TO THE NEWEST KERNEL ON SELECTION AND GOING TO THE RECOVERY ONE) and i got the same blue xorg configurer. It asked me what the company was, and then asks for the resolution. So i go to the 1280x800(my native resolution) hit spacebar to select it, then i go to press the OK button and it goes down to the command line and says somthing like "warning:overwrtiting somthing somthing, backup stored at xorg0238492384.conf" somthing like that. Then it does nothing. I know my card is a SiS M760GX with SiS 760 chipset, and a 1280x800 32bit 60ghz screen. I checked DXDIAG on windows to make sure. Apparently that -phigh didnt help? am i doing it wrong or what?

------------------------UPDATE
i just tried again. I went into it and selected sis like before, selected my 1280x800 resolution and then it ok. The message i got was then:"xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in etc/X11/xorg.conf.20080325160110"

It then just went to the next command line "david@david-laptop:~$"

Also i keep getting this error: "firmware_helper[4595]:main: error loading 'lib/firmware/bcm43xx_microcode5.fw' for device '/class/firmware/000:00:0b.0' with driver '(unknown)'
[459.900000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed."

I don't know what to do at this point. i tried following this
[http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/](http://absolutebeginner.wordpress.com/2006/09/15/restoring-your-previous-xorgconf-file/)
but when i type cd/ i just get "-bash: cd/: no such file or directory"

---

### Post by Rocket2DMn on 2008-03-25
Oh, you have one of the more irregular cards out there.  I think this means that you will have to use the "vesa" driver, which is normally a fallback safe mode driver.  With this card, you won't be able to get a lot of functionality out of it in linux.  
What driver were you selecting before?
Also, from the recovery mode kernel, you don't need "sudo" since you are already at a root terminal.
Try reconfiguring again, without sudo at the recovery mode, selecting the "vesa" driver, then your monitor's max resolution AND everything less than that.  Then reboot and see what happens.
PS: it's 60hz, not 60ghz.  60hz means your screen refreshes 60 (not 60 billion!) times per second, this is typical of LCD displays.

---

### Post by Takido on 2008-03-25
once again, no go. I did it with -phigh, i selected Vesa, i went to 1280x800 and selected it and everything below it and hit ok. Same thing happened. It said the crap about the warning and the recovery went to new line, and i restarted. still have the blue and grey screen with wierd symbols and the Failed to start X server(your graphical interface)

Damnit.
Any other ideas??
If not, you can just tell me how to re-install to the same partition as the one its currently on if you could please. Thanks.

---

### Post by Rocket2DMn on 2008-03-25
OK, if you're down with reinstalling, that might just be easier.  First I need to know if you are running a dual boot system and if there is anything on your drive that you need to recover.  Doing a reinstall will wipe everything off of your root partition.

---

### Post by Takido on 2008-03-25
i am duel-booting. I have windows XP on my C: drive and when i first installed ubuntu i partitioned my D: drive into 2 parts. So i do have a drive with nothing on it BUT the messed up ubuntu now. I just don't want to have to re-partition anything; i just want to delete this old install and make a new one.

---

### Post by Rocket2DMn on 2008-03-25
OK, that's easy enough to do.  If there is anything you need to recover from your Ubuntu installation, you can use the driver from [http://www.fs-driver.org/](http://www.fs-driver.org/) to access your linux partition from windows.  From there you can copy over anything you need.

Now to reinstall.  Just run the LiveCD (or alternate install cd) like you did before.  Choose manual partitioning and tell it to install the root "/" partition to your existing ext3 formatted root partition.  You can keep your same swap partition.  If you installed with a separate /home partition, you can keep your existing one as well (if you don't know what I'm talking about, then just ignore it).  It should be as easy as that.  If you think you are running into problems or confusion, don't risk it, just come back and ask - include a screenshot if possible.  That being said, you should always keep good and up-to-date backups on an external hard drive, or CD-R/DVD-R, flash drive, or other medium of your preference :)

---

### Post by Takido on 2008-03-25
ok its installing to my existing ext3 drive. now that i don't want to mess up my new system what is a safe (noob) way to give myself the widescreen resolutions that i'm going to need wihtout screwing myself up again? I remember seeing somthing in a different thread about using synaptic package manager to do it..

---

### Post by Rocket2DMn on 2008-03-25
So if the screen resolution is not listed under System->Preferences->Screen Resolution and you know the video card can go higher, you have to reconfigure X or modify xorg.conf manually.  I usually don't suggest manual edits since they tend not to work very well.  If you do this, first make a manual backup of xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
You can post the xorg.conf here if you want me to look at it, just let me know which video card you are using
```
cat /etc/X11/xorg.conf
```
and to edit it (make a backup first!)
```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by Takido on 2008-03-25
```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
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
        Identifier      "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
        Driver          "sis"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Silicon Integrated Systems [SiS] 661/741/760 PCI/AGP or 662/761Gx PCIE VGA Display Adapter"
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
EndSection

Section "DRI"
        Mode    0666
EndSection

```
there is my xorg and i made a backup. Im going to restart now because i just updated.
--------Update
Ok i'm back now and i have the gedit opened.
Now exactly what do you want me to change? Just add the 1280x800 resolution into each of these?
```
  SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection

```
I'll wait for your guidance either way.

---

### Post by Rocket2DMn on 2008-03-25
You would want to change the lines from
```
                Modes           "1024x768" "800x600" "640x480"
```
to
```
                Modes           "1280x800" "1024x768" "800x600" "640x480"
```
for each depth.  Depth 24 is usually what is used, hence it's the default, but you might as well change for all of them.
It seems to have autodetected the "sis" driver, a less known driver specific to your model card.  
Save and close, then restart X with CTRL+ALT+BACKSPACE.  If X fails to come up, you can restore your backup by doing CTRL+ALT+F1 to get to a tty, logging in there and running
```
sudo /etc/init.d/gdm stop
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
sudo /etc/init.d/gdm start
```

---

### Post by Takido on 2008-03-25
Yessssss. It worked. That was sooooo simple. Thank you sooooo much. I have only one more question. How do i update from 7.04 to 7.10? i did all the necessary updates in the update manager but i don't think im in 7.10. and alsoo.. Im gonna need to use bcm43xx-fwcutter i guess to get my wireless card working so that i don't have to have a wired connection to my laptop anymore.
here are the specs.
```
Networking

Networking
    Network adapter
Networking / Wireless LAN Supported
    Yes
Wireless NIC
    Acer InviLink 802.11b/g
Data link protocol
    Ethernet, IEEE 802.11b, IEEE 802.11g, Fast Ethernet
Networking standards
    IEEE 802.11b, IEEE 802.11g, Wi-Fi CERTIFIED 

```
In this thread [http://ubuntuforums.org/showthread.php?t=642013](http://ubuntuforums.org/showthread.php?t=642013) it says that it's easier to get bcm43xxfwcutter in version 7.10 rather then 7.04.

Thanks so much for your help.

---

### Post by Rocket2DMn on 2008-03-25
In terminal, post the output of
```
lsb_release -a
``` to see wha version you are running.  As far as your wireless goes, you will need to start a new thread on that one because I don't have an answer for you there.  Let me know about the version you're now running, though.

---

