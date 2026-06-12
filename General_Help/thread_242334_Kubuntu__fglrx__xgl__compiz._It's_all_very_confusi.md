---
title: "Kubuntu / fglrx / xgl / compiz. It's all very confusing. Am I getting it right?"
date: 2006-08-23
forum: General Help
---

### Post by Steveire on 2006-08-23
First off, there are tons of guides which all either assume I am running gnome or assume I am using gdm. I am not.
Do I need to use gdm and not kdm for this stuff to work? Why? Will it be brown?

If I get that out of the way, it looks like I need to following things:
[list]
[*] Proprietry ATI drivers. (Are the Open source ones I have not good enough?) 
[*] XGL or AIGLX. These are composite managers. AIGLX is open source. I don't think XGL is. How would I know which I should install? Is it an arbitrary choice? Am I supposed to try one, and if that doesn't work try the other? What are the advantages / disadvantages to each? 
[*] Compiz
[/list]

It looks like the supported ATI card is **Mobility Radeon 9700 SE: Xgl running with proprietary fglrx driver 8.23**
I don't think I have a 9700. Can I still use XGL/AIGLX/Compiz? The output of lspci on my laptop is below.

```

steveire@ubuntu:~$ lspci
0000:00:00.0 Host bridge: ATI Technologies Inc RS300 Host Bridge (rev 02)
0000:00:01.0 PCI bridge: ATI Technologies Inc Radeon 9100 IGP AGP Bridge
0000:00:14.0 SMBus: ATI Technologies Inc ATI SMBus (rev 18)
0000:00:14.1 IDE interface: ATI Technologies Inc ATI Dual Channel Bus Master PCI IDE Controller
0000:00:14.3 ISA bridge: ATI Technologies Inc: Unknown device 434c
0000:00:14.4 PCI bridge: ATI Technologies Inc: Unknown device 4342
0000:00:14.5 Multimedia audio controller: ATI Technologies Inc IXP150 AC'97 Audio Controller
0000:00:14.6 Modem: ATI Technologies Inc IXP AC'97 Modem (rev 01)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc RS300M AGP [Radeon Mobility 9100IGP]
0000:02:03.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
0000:02:04.0 CardBus bridge: Ricoh Co Ltd RL5c475 (rev 81)
0000:02:05.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0000:02:06.0 USB Controller: NEC Corporation USB (rev 43)
0000:02:06.1 USB Controller: NEC Corporation USB (rev 43)
0000:02:06.2 USB Controller: NEC Corporation USB 2.0 (rev 04)


```
I saw this on [this page](http://gentoo-wiki.com/HARDWARE_Video_Card_Support_Under_XGL). Does this apply to me? Does it mean that I have to do some kind of kernel messing with fglrx?
```

    *  Radeon 9000 mobility (R9100IGP)
          o Chipset: RV250?
          o Driver: DRI-exa
          o Notes: It work after few tweak 

```
[This post](http://ubuntuforums.org/showthread.php?p=423584#post423584) seems to say that it won't work for my card, though. Is that right?

[This page](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide) seems to be a good guide to installing fglrx for a start, but I want to do backups of all neccessaries before I start any of this. What do I need to backup before starting? I've already backed up my xorg.conf file.

I've also read this page: [https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager), and would probably use [this guide](http://www.ubuntuforums.org/showthread.php?t=145068) to do the rest.

I admire the patience of anyone still reading at this point.

---

### Post by flankker on 2006-08-23
hiya there i was in the same situation u were a couple of months ago, i am running kubuntu and i have the same video card, an ati mobility 9000 igp.

i will show u the guides i used, that should help you:

to get the DRI driver working with 3D acceleration: [http://ubuntuforums.org/showthread.php?t=219336&highlight=ati+open+source+driver](http://ubuntuforums.org/showthread.php?t=219336&highlight=ati+open+source+driver)
(just follow the first part, not the xgl/compiz second part)

for setting up xgl/compiz as a session i used the ¨ubuntu gnome howto¨ guide over at [http://www.compiz.net/index.html](http://www.compiz.net/index.html), and i just modified it for kubuntu. no need to intall gdm, kdm works just fine. then i used the ¨compiz-start¨ script to start compiz, which can also be found at that site.

i would link to the precise guide but [http://www.compiz.net/index.html](http://www.compiz.net/index.html) is down for me at the moment.

hope that helps u  :)

---

### Post by Steveire on 2006-08-24
Hey thanks for the links and reassuring me about the kdm issue. I've completed the first part, and so far so good.

> 
for setting up **xgl/compiz** as a session i used the ¨ubuntu gnome howto¨ guide over at [http://www.compiz.net/index.html](http://www.compiz.net/index.html), and i just modified it for kubuntu. no need to intall gdm, kdm works just fine. then i used the ¨compiz-start¨ script to start compiz, which can also be found at that site.

xgl/compiz? I thought this uses AIGLX and not xgl?

Compiz.net doesn't work for me at times too, but it's working now. I found this thread on compix.net: [http://www.compiz.net/viewtopic.php?id=389](http://www.compiz.net/viewtopic.php?id=389), and started working from it. Is it the one you meant?

After activating the beerorkid repository, it instructs to install these packages.
```

sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

```

[This thread](http://ubuntuforums.org/showthread.php?t=222034) instructs to install different packages:
```

sudo apt-get install xserver-xgl compiz-gnome cgwd cgwd-themes

```
though when I enter both into the terminal, I get almost the same packages once dependancies have been sorted out. The only difference is that the package called 'compiz' doesn't get installed using the second command. That seems kind of neccessary to me.

[This thread](http://www.ubuntuforums.org/showthread.php?t=145068) instructs to install different packages too, and it seems to instruct to change xorg.conf in a different way.

It recommends this:
> 
compiz 
aiglx are now partially official, compiz-vanilla or compiz-quinn packages work now on xorg-aiglx. All compiz-aiglx packages are now deprecated, well first uninstall all compiz-aiglx packages

```


sudo aptitude purge compiz-aiglx compiz-aiglx-gnome

```

you can then either install compiz-vanilla packages :
```


sudo apt-get install compiz-vanilla-aiglx compiz-vanilla compiz-vanilla-gnome

```
or compiz-quinn packages:
```


sudo apt-get install compiz-quinn-aiglx compiz compiz-gnome

```


When I edit my sources list to also include 'aiglx' from the beerorkid repos, and try to run the first command, I get this:
```

steveire@ubuntu:/etc/kde3/kdm$ sudo aptitude install compiz-quinn-aiglx compiz compiz-gnome
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for compiz-quinn-aiglx
The following NEW packages will be automatically installed:
  capplets-data compiz-core compiz-plugins libcroco3 libgsf-1-113
  libgsf-1-common librsvg2-2 libwnck-common libwnck18 libxres1
The following packages have been kept back:
  xserver-xorg-driver-ati xserver-xorg-driver-i810
The following NEW packages will be installed:
  capplets-data compiz compiz-core compiz-gnome compiz-plugins libcroco3
  libgsf-1-113 libgsf-1-common librsvg2-2 libwnck-common libwnck18 libxres1
0 packages upgraded, 12 newly installed, 0 to remove and 2 not upgraded.
Need to get 1727kB of archives. After unpacking 13.4MB will be used.
Do you want to continue? [Y/n/?]   

```

Which is a less complete version of the result of this command (repeated from above after adding the aiglx part to the sources.list):
```

steveire@ubuntu:/etc/kde3/kdm$ sudo aptitude install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome cgwd cgwd-themes
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following NEW packages will be automatically installed:
  capplets-data compiz-core compiz-plugins libcroco3 libglitz1 libgsf-1-113
  libgsf-1-common librsvg2-2 libwnck-common libwnck18 libxres1
The following packages have been kept back:
  xserver-xorg-driver-ati xserver-xorg-driver-i810
The following NEW packages will be installed:
  capplets-data cgwd cgwd-themes compiz compiz-core compiz-gnome
  compiz-plugins libcroco3 libglitz-glx1 libglitz1 libgsf-1-113
  libgsf-1-common librsvg2-2 libwnck-common libwnck18 libxres1 xserver-xgl
0 packages upgraded, 17 newly installed, 0 to remove and 2 not upgraded.
Need to get 4161kB of archives. After unpacking 19.8MB will be used.
Do you want to continue? [Y/n/?]    

```
I went with the command with the aiglx-quinn packages, because I'm using aiglx and not xgl. Why are these packages kept back, and can I do anything about it?
```

The following packages have been kept back:
  xserver-xorg-driver-ati xserver-xorg-driver-i810

```
If I do a sudo aptitude uprade, it offers to upgrade those packages. Are they not being upgraded because the compiz packages use a older versions of the packages (ie, the versions I currently have)?

I reedited my xorg.conf to include the changes directed in that page. The rest was already in there from when I configured it for the radeon card:
```

Option "XAANoOffscreenPixmaps"

```
and
```

Option "AIGLX" "true"

```
so that the sections in my xorg.conf now read:
```

Section "Device"
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
        Driver          "radeon"
        Option          "XAANoOffscreenPixmaps"
        BusID           "PCI:1:5:0"
EndSection

Section "ServerLayout"
        Option          "AIGLX" "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

```
Now I have to figure out what I need to edit kdm to.

Sorry about the really long post. I was doing this stuff as I wrote it.

---

### Post by flankker on 2006-08-25
well, im no expert so i think it will be better if i post what i personally did to make it work for me step by step.

if u followed the first link i gave u succesfully u shouldnt need to change anything in your xorg.conf.

about using aiglx intead of xgl, as far as i understand xgl is more up to date but also less stable, however i havent had any problems with it so i use xgl.

now heres what ive done:

added this repository to sources.list: deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main

this to get the key for the repo: wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -

then download the packages needed: sudo aptitude install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome cgwd cgwd-themes gconf-editor

the dependencies should be taken care of automatically. 

then create a startup script for xgl: sudo kate /usr/bin/startxgl.sh

paste this into the file: 

Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
# Start KDE
exec startkde
# Start Compiz window manager

save it and make the script executable: sudo chmod 755 /usr/bin/startxgl.sh

make an xgl session for the login manager: sudo kate /usr/share/xsessions/xgl.desktop

paste this into the file and then save it:

[Desktop Entry]
Encoding=UTF-8
Name=XGl
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application

then download this script and the icon and put them in your desktop: [http://www.compiz.net/attachment.php?item=1120](http://www.compiz.net/attachment.php?item=1120)

and for the icon:

[http://www.compiz.net/attachment.php?item=496](http://www.compiz.net/attachment.php?item=496)

then: chmod 755 compiz-start.py

and then: sudo mv logo24.png /usr/share/compiz/

im doing this from memory but i think thats it. to use xgl/compiz select the ¨xgl¨ session in kdm, then click on the compiz-start script on your desktop and compiz should load. if u have any other questions just ask here, or try the compiz forum at [http://www.compiz.net/index.html](http://www.compiz.net/index.html)

---

### Post by Steveire on 2006-08-25
Thanks for that. Just a quick one:
```

The following packages have been kept back:
  xserver-xorg-driver-ati xserver-xorg-driver-i810

```
Do you know anything about this? Trying an aptitude upgrade now offers to upgrade them. If I upgrade them though, it could break things before I even get started.

I'll be having a go at getting this working to completion soon, but it might be a few days. Thanks for your help.

---

### Post by flankker on 2006-08-25
> **Steveire said:**
> Thanks for that. Just a quick one:
```

The following packages have been kept back:
  xserver-xorg-driver-ati xserver-xorg-driver-i810

```
Do you know anything about this? Trying an aptitude upgrade now offers to upgrade them. If I upgrade them though, it could break things before I even get started.

I'll be having a go at getting this working to completion soon, but it might be a few days. Thanks for your help.

well im not sure but i would uninstall those two packages as you arent using those drivers. u are using the ¨radeon¨ driver so u shouldnt need to have the ¨ati¨ and ¨i810¨ drivers installed.

---

### Post by VCSkier on 2006-09-01
let us know if it works for you.  i've been working on a friend of mine for a while, trying to get him to convert to kubuntu from windows, and he's been interested but reluctant, but when he saw compiz, he now wants compiz AND kubuntu.  he has a pretty new ati mobility card...  thanks

---

### Post by Steveire on 2006-09-15
I'm just having another look at this now, but I haven't got a working aiglx/compiz system yet. Further to the steps I took above, I edited my kdmrc file to 
```

#ServerCmd=/usr/bin/X -br
ServerCmd=/usr/bin/Xorg-air :1

```
and edited my /etc/environments file too:
[http://www.ubuntuforums.org/showthread.php?t=216543](http://www.ubuntuforums.org/showthread.php?t=216543)

I also did sudo aptitude install xserver-xorg-air-core even though I hadn't seen an instruction to do so before.

I reboot and after the kubuntu screen about starting cupsd etc (is that the boot splash or usplash?), the empty progress bar reappears and nothing happens until I restart, and reverse the comments above and start normally again.

Any pointers on getting this working? Here's my complete xorg.conf if you can see something I've done wrong.
```


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
        Load    "bitmap"
        Load    "ddc"
        Load    "dbe"
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
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
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
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
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
        Identifier      "ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
        Driver          "radeon"
        Option          "XAANoOffscreenPixmaps"
        BusID           "PCI:1:5:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. Radeon Mobility 9100 U3 (R200 IGP)"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Option          "AIGLX" "true"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

Is there other packages to install or anything?

---

