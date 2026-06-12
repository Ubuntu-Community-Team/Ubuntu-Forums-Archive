---
title: "Nvidia Restricted drivers PROBLEM!!!!"
date: 2008-05-31
forum: General Help
---

### Post by kemkokems on 2008-05-31
Well the problem is as it follows:

I am a virgin with the ubuntu and recently I have installed ubuntu 8.04 and it is really great OS and it got me pined down:-)I wanted to try those amazing effects so i installed nvidia driver via synaptic ,and everything went fine.Ubuntu connected to internet and installed this driver and asked me to reboot and now the problem starts.I couldnt boot into ubuntu,I just see black screen and it says: signal out of range!!!
So I booted into recovery and I tried to fix x-server and it works.So when I finnaly got into ubuntu I have this message in upper panel that drivers are installed but not supported!!!
I also tried installing driver via NvyNG applet(which is fully automated) and I tried all the 3 versions of the nvidia drivers(173.14.05/71.86.04/96.43.05)but none of them works and when I install them I have the same problem!!!!
By the way my configuration is:

CPU:Pentium 4 s478 2.0GHz Northwood
GPU:Asus GeForce FX5200 128MB
MBO:Asus P4S333-M

I also have windows xp pro sp2 installed along with the ubuntu in dual boot conf.
So if anyone has the solution please HELP!!!!
I was searching for help in my country but did not yet find the solution.
My ubuntu knowledge is very basic so simplify as much as possible!!!
THANX!!!

---

### Post by aikiwolfie on 2008-05-31
Why did you use synaptic to install the drivers? Ubuntu has a restricted drivers manager. You should have used that instead. Uninstall the drivers you installed.

Now go to System > Administration > Hardware Drivers

---

### Post by kemkokems on 2008-05-31
I am sorry I did not use synaptic I used restricted driver manager!!!I tried everything, I wrote that,I uninstalled drivers and I tried with NvyNG but same thing!!!!

---

### Post by FuturePilot on 2008-05-31
Try this
> 
Making this change will have no impact on your installed system and is to be considered safe. If you reboot your system this change will disappear. It is temporary.

Start your computer normally and after a few seconds you will see the GRUB boot loader menu. 

[LIST]
[*]With the use of the arrow keys, highlight the title of your choice you want to edit (the first Ubuntu entry should be ok) and press "e" to go to the entry editor interface. You will now see the boot entries for the title you selected.
[*]Highlight, again with the use of the arrow keys, the line that say "kernel" and press "e" to edit that line.
[*]Add, without the quotes " vga=normal" and press the enter key to go out of edit mode.
[*]Press the "b" key to boot your system.
[/LIST]

Note: To cancel your changes press the Escape key until the main menu appear.

[https://wiki.ubuntu.com/FrameBuffer]("https://wiki.ubuntu.com/FrameBuffer")

---

### Post by kemkokems on 2008-05-31
But where am I going with editing this line in grub menu???I fixed the booting problem didnt you read my post?I just want to use effects but it seems to me that u think that I can no longer boot in ubuntu or what!?Or editing this kernel line will possibly fix further driver installation problem?I am confused now!???

---

### Post by starcannon on 2008-05-31
Heres how I set up every one of my nvidia cards, don't skip steps even if you have already done them in the past.
```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
    1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
    4.a) Add "nvidia" without quotes to the list.
    4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
    5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
    5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
    7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
    7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
        -------------------------------------------------------------------------------------------------------
        If you used Envy to attempt a previous nvidia install please run this command now before you go on:

        sudo envy --uninstall-all 
        sudo dpkg -P envy 
        sudo envyng --uninstall-all
        sudo dpkg -P envyng
        In Depth Instructions on Envy and EnvyNG install/uninstall http://albertomilone.com/pmwiki/pmwiki.php?n=Main.EnvyNG-InstructionsForUbuntu




        -------------------------------------------------------------------------------------------------------
        If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

        sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

        -------------------------------------------------------------------------------------------------------
        If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

        sudo nvidia-installer --uninstall

        -------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
    8.a) Okay were in Command Line only now, we have a little left to do in here.
    8.b)login:
    8.c)Password:

9) sudo /etc/init.d/gdm stop
    9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
    10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
    11.a) Answer to the affirmative for all questions.
    11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
    11.c) If you somehow answered incorrectly on the last question in the installer then:
        c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
    12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

**Optional But recommended:**
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     http://ubuntuforums.org/showpost.php?p=5227704&postcount=1
```Here's a click link for the guide mention in step 13
[http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)

I will continue to update this guide as I find new things, but I am not really following this thread any longer as the OP seems to have moved on.

If I refer you to this guide from another thread, then please continue posting in the thread we met on. GL and hope this guide helps you.

~Starcannon

---

### Post by FuturePilot on 2008-05-31
> **kemkokems said:**
> But where am I going with editing this line in grub menu???I fixed the booting problem didnt you read my post?I just want to use effects but it seems to me that u think that I can no longer boot in ubuntu or what!?Or editing this kernel line will possibly fix further driver installation problem?I am confused now!???

You said you were getting a Signal Out Of Range error. By editing Grub it should get rid of that possibly, since for some reason something is telling your monitor to go into a mode it doesn't support. You can edit Grub when you see the Grub menu come up after your BIOS screen when you turn your computer on.

---

### Post by dansued on 2008-05-31
After I installed the nvidia.run drivers, everything works perfectly. However, when I restart the computer, X cannot start and I have to run the driver setup program again before it will work. Why can't it remember the drivers?

btw, I'm installing with sh not ./ if it makes a difference

---

### Post by dansued on 2008-05-31
> **starcannon said:**
> Heres how I set up every one of my nvidia cards, don't skip steps even if you have already done them in the past.
```

8) CTRL-ALT-F1
    8.a) Okay were in Command Line only now, we have a little left to do in here.
    8.b)login:
    8.c)Password:

9) sudo /etc/init.d/gdm stop
    9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
    10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
    11.a) Answer to the affirmative for all questions.
    11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
    11.c) If you somehow answered incorrectly on the last question in the installer then:
        c.I) sudo nvidia-xconfig #this will write a new or attempt repair of an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
    12.a) You should see an Nvidia Logo, and then be put at your login screen, you should also be able to enable desktop effects.
```


After I installed the nvidia.run drivers, everything works perfectly. However, when I restart the computer, X cannot start and I have to run the driver setup program again before it will work. Why can't it remember the drivers?

btw, I'm installing with sh not ./ if it makes a difference


sorry for double posting..

---

### Post by kemkokems on 2008-05-31
Well now I am really pissed of!!!I tried all of these steps above and none of them works and now I totally crushed x-server and it can not find any backup!!!And now I am going to DELETE UBUNTU!!!!!!!!!!!
****,its driving me crazy.
THANX ANYWAY!!!!

---

### Post by starcannon on 2008-05-31
@dansued

```
4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit
```

That should fix you up.

---

### Post by starcannon on 2008-05-31
ack nm browser freaked out for some reason

---

### Post by starcannon on 2008-05-31
> **kemkokems said:**
> Well now I am really pissed of!!!I tried all of these steps above and none of them works and now I totally crushed x-server and it can not find any backup!!!And now I am going to DELETE UBUNTU!!!!!!!!!!!
****,its driving me crazy.
THANX ANYWAY!!!!

guess you missed at least step
```
6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup
```

If however you did do step 6 then all you would have to do to get back to where you started would be 
```
sudo cp ./xorg.conf.backup /etc/X11/xorg.conf
sudo reboot
``` 

GL and relax before you do anymore, you sound a bit manic, computers don't respond well to that.

---

### Post by dansued on 2008-05-31
> **starcannon said:**
> @dansued

```
4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit
```

That should fix you up.
nvidia was already in /etc/modules

any other solutions?

Thanks in advance!

---

### Post by dansued on 2008-06-01
so nvidia is in /etc/modules and it still doesn't load after a reboot, however I managed to get a log

```
/etc/gdm/failsafeXserver: line 47: [: too many arguments
Warning: Failsafe mode was already attempted within 30 seconds
Warning: Falling back to gdm to report the issue.
```

btw, when I run nvidia*.run, it reports that the drivers are already installed, but I reinstall it anyway which makes it work. I always let the program reconfigure the X config. I think the drivers are fine maybe just some file needs to be updated.

---

### Post by starcannon on 2008-06-02
I'm stumped for the moment, putting nvidia in that modules list is supposed to cure your particular problem...

I've got to run out and setup a lan and wireless printer here in a few minutes, when I get back home I will look into this some more with you if you like.

If you could post the output of

```
cat /etc/X11/xorg.conf
cat /etc/modules
cat /etc/default/linux-restricted-modules-common

```

here in the thread perhaps that will help shed some light on this.

---

### Post by PacketRatket on 2008-06-06
Thanks Starcannon for your detailed post. I've been through many others with bits and pieces of this over the past couple days and your post is the most complete and makes sense. Unfortunately, it didn't work so I am still trying to figure this out. I am new convert but trying to come up to speed so I appreciate the detail.

Here is the present situation:
-8.04 kernel 2.6.24.18 after recent update.
-I have presently tried loading Nvidia 173.14.05 by your procedure
-Video Card is NV40 (Gforce 6800) AGP 
-Motherboard is P4 based 2.4 GHz Intel ASUS P4PE
-Monitor is Samsung SyncMaster 204B connected Via DVI
(also attempted archived video driver revisions previously, but I think by your cleanup I should be good. Nothing has made any difference in behavior so far on any attempt)

What happens is that on gdm start the screen will blink 3 times as if attempting to detect monitor and then drop back to the "low resolution" dialog allowing only 800x600. I never get the Nvidia logo.

If I use the Xorg autoreconfigure sudo dpkg-reconfigure -phigh xserver-xorg command, it does work and I can get up to 1280x1024 with no hardware acceleration. Also note same exact hardware under XP (dual booted from Grub startup menu) loads the latest Nvidia drivers for windows and resolution at 1600x1200 (60 Hz) no problem.

Here is the file info requested. Note I added some extra info into the monitor and display section from an earlier Xorg config file that should be valid as an attempted fix because default nvidia-xconfig generated file did not work either.

I am pretty much at a dead end at this point, so hoping some new ideas come forward or perhaps some tests I can run to try to help track this down. Everything else I have found via search of other threads comes up with a part or subset of what you have already posted.

Thanks

```
~$ cat /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder63)  Mon May 19 00:33:37 PDT 2008

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
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
    Identifier     "Monitor0"
 	Vendorname	"Samsung"
	Modelname	"Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
	Horizsync	30-81
	Vertrefresh	56-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
	Gamma	1.0
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
 SubSection "Display"
		Depth	24
		Virtual	1600	1200
		Modes		"1600x1200@60"	"1024x768@70"	"800x600@60"	"1024x768@60"	"1152x864@75"	"1280x1024@75"	"1280x960@60"	"1280x1024@60"	"1280x960@75"	"1400x1050@60"	"1600x1200@65"	"1600x1200@60"
	EndSubSection
EndSection

~$ cat /etc/modules
# {Standard comment lines removed for this post}

fuse
lp
nvidia

~$ cat /etc/default/linux-restricted-modules-common
# {Standard comment lines removed for this post}

DISABLED_MODULES="nv"

```

---

### Post by PacketRatket on 2008-06-06
A little more research, hoping this thread is not dead. I looked at the Nvidia driver readme file, Chapter 5 which is the same for both the recommended archived version (by some 173.08) and latest version 173.14.05
[http://us.download.nvidia.com/XFree86/Linux-x86/173.08/README/chapter-05.html]("http://us.download.nvidia.com/XFree86/Linux-x86/173.08/README/chapter-05.html")

and noticed that although my install by Starcannons procedure seemed to go fine none of the files get written to the directories noted in the list of installed components.  The above chapter says for example that the X driver should be at > An X driver (/usr/X11R6/lib/modules/drivers/nvidia_drv.so)but on my system the X11R6 directory is empty and the nvidia installer loaded the driver to to > usr/lib/xorg/modules/drivers. I note that many of the other files appear to have gone to > XORG instead of > X11R6

Could this be why my X log says> (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found

Is there a way in Linux to grab a whole folder, copy it, and move it to another directory? If so, maybe I could test taking the entire "modules" directory including subs from "lib/xorg" and copying it to "X11R6/lib" I could try and see if this will fix the issue. There is little risk I think because X11R6 is presently empty so it will either find the drivers there after I copy them or keep doing whatever it has been anyway which is no loss. Trouble is being green I don't know how to grab a whole folder and cut and paste in gnome when root privileges are required and I can't seem to login as "root" with the same password I use for sudo in the terminal.

---

### Post by PacketRatket on 2008-06-06
Having an interesting coversation with myself but just in case anyone else stumbles on this, I am happy to report this is fixed, although ugily.

Here's what I did... I decided to flush the whole thing and start over with a brand new install. My drive is just used for Ubuntu system (all data is on shared NTFS drives) so I reloaded the whole ubunt-chilada from scratch (Live CD, full partition, blowing away previous hosed install). Upon first load from the hard drive, the kernel is 2.6.24-16 and I got the notification that restricted drivers and 129 updates were available. I went ahead and let the hardware drivers manager load the restricted drivers but deferred the updates and was able to enable desktop effects. I then yielded to update manager that wanted to install the 129 updates. In spite of a few error messages that some packages did not load (I could not find details in the log on this), I rebooted and new build is 2.6.24-18 (but not the same 2.6.24-18 I had a couple days ago I think it was appended with 18.23 or 18.32 in the terminal window description). Good news is that it appears everything is working now so on to reload all the programs I want (wine, samba, etc.)

So good news is that as of today a user that does a clean install from the CD image should not have the problems I had with the GForce 6800 (NV40) card. No real way to know if this was an updater issue or something I did in the past couple days changing hardware and hosing my system.

Attached are the config files just for reference:
```
# xorg.conf (X.Org X Window System server configuration file)
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

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection
```

```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
```

/etc/default/linux-restricted-modules-common (i.e. nothing blacklisted)
```
DISABLED_MODULES=""
```

So I would say now the nvidia driver issue appears resolved for me. On to running some benchmarks on the games I like (under Windows and Wine) with the same hardware.

---

### Post by zedstrange on 2008-06-08
> **PacketRatket said:**
>  I went ahead and let the hardware drivers manager load the restricted drivers but deferred the updates and was able to enable desktop effects

Please make it clear whether you rebooted or not after installing the restricted drivers and before installing the updates?

---

### Post by zedstrange on 2008-06-11
> **starcannon said:**
> Heres how I set up every one of my nvidia cards, don't skip steps even if you have already done them in the past.

Ok,  did all that - twice. and running off a clean install as well.
used both the latest and the 100.14.19 drivers which someone said somewhere works fine.  (and tried almost everything else i have read in this forums)

I get to this point no problems.

>  sudo /etc/init.d/gdm start
    12.a) You should see an Nvidia Logo, and then be put at your login screen, you should also be able to enable desktop effects.

No Logo. eventually i get a configuration window, i only have choice of 640*480 or 800*600. when desktop loads i get this error when i attempt to run Nvidia X server settings.

¨you do not appear to be using the NVIDIA X driver....¨

Honestly, am ready to give up.  So many people have this issue, and seems the only solutions to be really offered is by those who did not have the issue in the first place

It cant be a total Nvidia issue,  my laptop is running fine on the latest drivers and on 8.04, wasnt even a clean install.

---

### Post by zedstrange on 2008-06-12
Ok, never mind. My Issue resolved.  No Nvidia issue, No Ubuntu Issue.

I have a Dell SC430, which requires a modified PCIE card installed in the 4x PCIE slot, and I installed it in the 8x, which is not meant to support a Display adaptor.

I moved to the new slot and installed 8.04 clean, and its all set up, nice and shiney.

3 Cheers for Starcannon, I used your instructions.

---

### Post by martinitime1975 on 2008-06-19
I have been having problems with restricted graphics drivers with both pci express cards I have.  

On my older machine (Athlon 2600, Radeon 9800 pro AGP) restricted drivers work fine and I can enable desktop effects.  Ditto with my Dell laptop (Xubuntu 8.04, Centrino Proc, Radeon x300). However, when I built my new system with a dual core AMD 3800, and a PCI express video card (first a Radeon 800 GTX and then an Nvidia 8600 GT) I am having total black screen madness after enabling the restricted drivers.

I have tried every way in the book to install drivers, all from clean installs. I've tried ticking the restricted drivers check box, using Envy, building the driver from Nvidia, none of it works.    And after reboot, I don't even get to alt+f1 into a console window, the entire thing becomes non responsive.  This is an embarrassment to both Ubuntu and ATI/NVIDIA.  There has to be something wrong with Ubuntu.  I even tried installs of Hardy AND Gutsy, neither one worked.  It works on older graphics hardware, but not newer ones.

This needs to be fixed asap, it's shameful.  No one is going to take Linux seriously if they can't even get accelerated graphics running (let alone printing, but that's another story).

---

### Post by GhettoYhetti on 2008-06-24
PacketRatket,

I have this same monitor and am having the same problem with the 6800 XT AGP.

My monitor settings, for what it is worth now are:

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
EndSection

---

### Post by GhettoYhetti on 2008-06-26
> **starcannon said:**
> Heres how I set up every one of my nvidia cards, don't skip steps even if you have already done them in the past.
```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, you should also be able to enable desktop effects.
```


Follow these instructions (TRULY FOLLOW THEM WITHOUT SKIPPING STEPS) and you will be up and running.  

Thanks starcannon!

---

### Post by altersense on 2008-07-05
I had the same problem with the screen going black (out of range)
right after installing the nvidia restricted drivers and rebooting.

My video card is a GeForce 6200, attached via DVI to a Samsung SyncMaster 226BW.

This turned out to be an EDID problem.

The general idea is to allow the LCD panel to be driven with a custom modeline.

This does not work unless one overrides DDC, EDID, pixel clock detection,
otherwise your custom modeline gets removed and xorg tries to drive
the panel with the incorrect values (out of range).

I have attached my xorg.conf in case it is useful to someone else.

For the SyncMaster 204B, replace with this modeline:
  ModeLine "1600x1200@55" 150.0 1600 1804 1996 2160 1200 1201 1204 1250 +hsync +vsync 


Just install Ubuntu as normal, apply all updates, enable the NVidia restricted driver and 
overwrite xorg.conf before rebooting.

---

### Post by :) Smiley :) on 2008-07-07
I had that same problem, but because I was using a laptop the laptop's monitor worked. It was only when I connected my external display I found the problem.
I used nvidia-settings
It's a great program and its in Synaptic. To set up your external display open a terminal window, type sudo nvidia-settings (after you've installed it), type your password and then the nvidia-settings window will appear. Click on X Server Display Configuration. You should see your monitors, if not click Detect Displays. Click on the display you want to configure, click configure, select an option, click OK, click Save to X Configuration File, click Save and then restart the X server.

---

### Post by Daisama on 2008-07-08
Never mind, it works now. Thanks a lot. I am still surprised at how bad the performance is for the 8xxx series. Maybe they will release better drivers in the future.

---

### Post by solarwind on 2008-07-08
> **starcannon said:**
> Heres how I set up every one of my nvidia cards, don't skip steps even if you have already done them in the past.
```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

**Optional But recommended:**
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     http://ubuntuforums.org/showpost.php?p=5227704&postcount=1
```
Here's a click link for the guide mention in step 13
[http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)

I will continue to update this guide as I find new things, but I am not really following this thread any longer as the OP seems to have moved on.

If I refer you to this guide from another thread, then please continue posting in the thread we met on. GL and hope this guide helps you.

~Starcannon

This helped me. Thank you!

---

### Post by Benconcups on 2008-07-09
> **starcannon said:**
> Heres how I set up every one of my nvidia cards, don't skip steps even if you have already done them in the past.
```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

**Optional But recommended:**
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     http://ubuntuforums.org/showpost.php?p=5227704&postcount=1
```
Here's a click link for the guide mention in step 13
[http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)

I will continue to update this guide as I find new things, but I am not really following this thread any longer as the OP seems to have moved on.

If I refer you to this guide from another thread, then please continue posting in the thread we met on. GL and hope this guide helps you.

~Starcannon


I searched THIS solution for 2 days thanks

---

### Post by sanike on 2008-07-11
Thanks for the tip

it worked for me on a 7300gt

---

### Post by sliding on 2008-07-18
I have a dual boot system with openSuse 11.0 and UbuntuStudio.
Though Ubuntu beats openSuse regarding handling the sound setup, it is far behind in 
configuring videocard and monitor.
I have a NVidia GeForce 7300 GS using nvidia driver 173.14.09 on openSuse 11.0 with a
Sony GDM-F540 21" monitor.

UbuntuStudio, updated to 8.04 (which introduced more trouble) does see the Nvidia card but
does not know this monitor. I tried most of the steps described in this thread with NO result, which 
leaves the last option of installing the NVidia driver package by hand.

Before trying that I first re-install the latest UbuntuStudio release, since I suspect having 
messed up the original install before the update to 8.04

While reading the posts on this problem, I was thinking that copying most of the xorg.conf file
from openSuse to Ubuntu might be a good idea, since it contains the proper monitor settings 
which I cannot find on Ubuntu. Yes, I know you can read them from a windows .inf file, but that
did not work and after updating the data dissappeared:confused:.

Since the NVidia driver is working great with openSuse on the same hardware, I think the problem
must be the way it is setup within Ubuntu regarding the proprietairy drivers.

---

### Post by upchucky on 2008-07-18
I hope this helps those that are getting frustrated by a nvidia install that just wont work.

Starcannons post will work, if you do exactly as it says.

there is one lcd that i know of that has trouble with it and that is because Toshiba refuses to play nice.

if toshiba is a trident microsystems display, then there is specific instructions to make this work, but it works.

there are other displays that seem to not work, but simply are listed as the wrong device device 0 or device 1.

some are listed as unknown, set these to generic,

it is very important to make sure you have removed all files of a failed install, sometimes rebooting just to be sure.

it is very important to understand what you are doing and understanding what you are seeing.

google your system to be able to post exact specs, google anything else you dont understand.

just cause you get dumped to a grub prompt does not mean the system is borked, it means you are on your way to becoming a guru.

if the install does not boot after a vid driver install that says it was successful, it usually means that it only needs the correct information edited into a couple of files to make it boot.

there are hundreds of posts here that say the same thing over and over, however not every system is identical, but the basics are the same.

if you are having trouble, be patient, read lots, and post exact information, the more detailed, that faster the answer can be found.

---

### Post by jeffLane on 2008-07-23
:(
These instructions worked just find until I got to item #10. When it says to enter 'sudo chmod a+x ./NVIDIA*.run

I get the following message no such directory or file found. At this point nothing else comes up on the screen.

I restart gdm and came back here for more help. I don't know if I left something out or if there is a step missing. I am new to Linux and Ubuntu and really appreciate all the help.

Thanx,
Jeff

> **starcannon said:**
> Heres how I set up every one of my nvidia cards, don't skip steps even if you have already done them in the past.
```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

**Optional But recommended:**
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     http://ubuntuforums.org/showpost.php?p=5227704&postcount=1
```
Here's a click link for the guide mention in step 13
[http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)

I will continue to update this guide as I find new things, but I am not really following this thread any longer as the OP seems to have moved on.

If I refer you to this guide from another thread, then please continue posting in the thread we met on. GL and hope this guide helps you.

~Starcannon

---

### Post by Jordy on 2008-07-24
Hey Starcannon, Just want to say thyanks for the instructions. Fixed up my Nvidia 7300GT beautifully. One comment though. I couldn't get the 
"sudo chmod a+x ./NVIDIA*.run" 
code to work until i realised that it was case sensitive. You might want to include something about that in  your instructions - for complete noobies like me!

Brilliant stuff

Thanks
again

Jordy

---

### Post by dannofoo on 2008-08-02
> **starcannon said:**
> Heres how I set up every one of my nvidia cards, don't skip steps even if you have already done them in the past.
```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

**Optional But recommended:**
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     http://ubuntuforums.org/showpost.php?p=5227704&postcount=1
```
Here's a click link for the guide mention in step 13
[http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)

I will continue to update this guide as I find new things, but I am not really following this thread any longer as the OP seems to have moved on.

If I refer you to this guide from another thread, then please continue posting in the thread we met on. GL and hope this guide helps you.

~Starcannon


Worked for me(dell pc, 6800 nvidia), thanks alot for this little guide.

---

### Post by Clappy on 2008-08-02
Shouldn't this thread be flagged as solved? It seems like everyone who had the problem has it fixed with Starcannon's post.

---

### Post by herda05 on 2008-08-02
Just a note. These steps have NOT worked with my integrated GF 8200 on m biostar M2+ MB. I've tried both the 173.14.12 and 177.13 which is beta. BOTH packages give the same result, a flickering screen. I've spent much of the time in this thread trying to get it solved:

[http://ubuntuforums.org/showthread.php?p=5511367#post5511367]("http://ubuntuforums.org/showthread.php?p=5511367#post5511367")

---

### Post by Jaxco on 2008-08-12
I am using a 9500gt, I can successfully install any driver even the new 177.xx... i just get a black screen after install, drivers work great with my old hardware but not this puppy!

---

### Post by the_nite_owl on 2008-08-20
Thank you very much, solved my problems with my 6100 GeForce.
One issue I had though is that I have EnvyNG installed rather than just Envy so the instructions would not work for uninstalling.

I would also suggest for anyone using a KVM switch that they plug the monitor directly into the PC during the process so that it can correctly identify the monitor capabilities.  Have had this problem on previous installs.

Thanks for a great how-to.

---

### Post by SilverBear on 2008-08-20
Blessings/beneficial karma/good luck and happiness to [B][COLOR="Blue"]starcannon!
[/COLOR][/B]
These steps worked perfectly for my son's new Compaq CQ50-110us laptop that  he needs to start university in another 3 days.  It has Vista, of course. . . but why start college at a disadvantage?! Dual booting.

Now I have to solve the wireless connection [ethernet works perfectly] --and Dad's work is done.
:guitar:


> **starcannon said:**
> Heres how I set up every one of my nvidia cards, don't skip steps even if you have already done them in the past.
```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

**Optional But recommended:**
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     http://ubuntuforums.org/showpost.php?p=5227704&postcount=1
```
Here's a click link for the guide mention in step 13
[http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)

I will continue to update this guide as I find new things, but I am not really following this thread any longer as the OP seems to have moved on.

If I refer you to this guide from another thread, then please continue posting in the thread we met on. GL and hope this guide helps you.

~Starcannon

---

### Post by cordoba57 on 2008-09-02
Thanks Silverbear,

I reworked one of my twin CQ50 laptops per your instructions -- thanks.

In researching the awful sound and weird responses to keyboard switches (e.g.: touchpad on/off and wifi on/off), I have found that Nvidia differentiates between the GeForce and GeForce M/Go (laptop version).  In fact, the "M/Go" version is older.

Selecting GeForce 8 series takes me to
[http://www.nvidia.com/object/linux_d...173.14.12.html](http://www.nvidia.com/object/linux_d...173.14.12.html)

Selecting GeForce M series takes me to
[http://www.nvidia.com/object/linux_d...32_169.12.html](http://www.nvidia.com/object/linux_d...32_169.12.html)

I understand that Nvidia produces the video card as well as mainboard for many laptops. This machine seems to be one, and
lspci seems to indicate that the audio is also Nvidia, I'm wondering if I've selected the "best" driver...(173)

Oh, as for wifi -- I think we've discovered that, although the wifi button really does turn the card on and off, the light is always red.  So, if you're having trouble with madwifi or NDIS wrapper finding the card, try taping the wifi button once...

Cordoba57

---

### Post by mailbox on 2008-09-19
> **starcannon said:**
> Heres how I set up every one of my nvidia cards, don't skip steps even if you have already done them in the past.
```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

**Optional But recommended:**
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     http://ubuntuforums.org/showpost.php?p=5227704&postcount=1
```
Here's a click link for the guide mention in step 13
[http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)

I will continue to update this guide as I find new things, but I am not really following this thread any longer as the OP seems to have moved on.

If I refer you to this guide from another thread, then please continue posting in the thread we met on. GL and hope this guide helps you.

~Starcannon

Hmm, this isn't working for me. I followed the instructions down to the letter, but I'm still not getting the Nvidia splash screen, and glxgears is horribly slow: ```
dissonance@iridium:~$ glxgears -info
GL_RENDERER   = GeForce 7900 GTX/PCI/SSE2
GL_VERSION    = 1.2 (2.1.2 NVIDIA 173.14.12)
GL_VENDOR     = NVIDIA Corporation
GL_EXTENSIONS = GL_ARB_depth_texture GL_ARB_imaging GL_ARB_multitexture GL_ARB_point_parameters GL_ARB_point_sprite GL_ARB_shadow GL_ARB_texture_border_clamp GL_ARB_texture_cube_map GL_ARB_texture_env_add GL_ARB_texture_env_combine GL_ARB_texture_env_dot3 GL_ARB_texture_mirrored_repeat GL_ARB_window_pos GL_ARB_texture_non_power_of_two GL_ARB_vertex_program GL_ARB_fragment_program GL_EXT_abgr GL_EXT_bgra GL_EXT_blend_color GL_EXT_blend_func_separate GL_EXT_blend_minmax GL_EXT_blend_subtract GL_EXT_draw_range_elements GL_EXT_fog_coord GL_EXT_multi_draw_arrays GL_EXT_packed_pixels GL_EXT_rescale_normal GL_EXT_secondary_color GL_EXT_separate_specular_color GL_EXT_shadow_funcs GL_EXT_stencil_wrap GL_EXT_texture3D GL_EXT_texture_edge_clamp GL_EXT_texture_env_add GL_EXT_texture_env_combine GL_EXT_texture_env_dot3 GL_EXT_texture_lod GL_EXT_texture_lod_bias GL_EXT_texture_object GL_EXT_vertex_array GL_EXT_framebuffer_object GL_ATI_texture_mirror_once GL_IBM_texture_mirrored_repeat GL_NV_blend_square GL_NV_texgen_reflection GL_NV_texture_rectangle GL_NV_texture_env_combine4 GL_SGIS_generate_mipmap GL_SGIS_texture_lod GL_SGIX_depth_texture GL_SGIX_shadow 
2338 frames in 5.0 seconds = 463.577 FPS
2340 frames in 5.0 seconds = 466.597 FPS
2340 frames in 5.0 seconds = 465.626 FPS
```

---

### Post by TeXtonyx on 2008-09-19
He means that after you install the updates it wants you to reboot right then which I imagine you did. I have a dual monitor Nvidia card which did not work, and both your description and Starcannon's were very informative.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
That explains how to work around Ubuntu disabling root login by default.
So yes you can use Nautilus, $gksudo nautilus to copy directories. Also by
the command line, example: sudo cp -a /media/sdc1/Program\ Files/MAIET /home/cookieorc/.wine/drive_c/Program\ Files
Also since I'm the only person with access to my computer ever, I disabled being prompted for the password every time I used sudo (in my stephen account) which is described in the RootSudo link above.

---

### Post by sulba on 2008-10-28
Hmm this way works but i have another problem :(. When my desktop is loading (~10 sec. after loging) my computer is frozen... i have to press reset. After reboot my resolution is again 800x600 :( or i have error...

|Configure|    |Shut Down|   |Continue|

graphic card: GeForce 8400

Ppl help me ! i hate vista!!

ps. sorry for my english.

---

### Post by Zimmer on 2008-10-28
Have you recently updated to the new kernel? 2.6.24 -21   ?
Were you using the nvidia drivers for 3D ?
If yes, then you will need to re install the nvidia drivers.

The method I have just used to do this is as follows.
At this point...
|Configure| |Shut Down| |Continue|

 press Continue
Boot In low graphics mode .
Open Synaptic package Manager and install envyng-gtk.

run envyng and select NVIDIA and remove the drivers, reboot, run envyng and install the 173 driver

See [http://albertomilone.com/envyfaq.html](http://albertomilone.com/envyfaq.html)
for more info BEFORE you start.

Worked for my Geforce 8400M GS  in HP laptop.

---

### Post by tpsingh on 2008-11-14
> **starcannon said:**
> Heres how I set up every one of my nvidia cards, don't skip steps even if you have already done them in the past.
```
Print out this guide, you will be in pure CLI for part of the install.

1)  Download the driver for your Nvidia Card from http://www.nvidia.com/Download/index.aspx?lang=en-us
	1.a) Make sure its in your home directory, this will make it so we don't have to change directories later when were in terminal.

2) Open a terminal: Applications--> Accessories--> Terminal

3) sudo apt-get install build-essential

4) gksudo gedit /etc/modules
	4.a) Add "nvidia" without quotes to the list.
	4.b) Save and Exit

5) gksudo gedit /etc/default/linux-restricted-modules-common
	5.a) Add "nv" without quotes to the restricted list. It should look exactly like this: DISABLED_MODULES="nv"
	5.b) Save and Exit

6) sudo cp /etc/X11/xorg.conf ./xorg.conf.backup

7) sudo rm /etc/X11/xorg.conf
	7.a) Were just deleting your old xorg.conf file, we backed it up in step 6 just in case we ever need it back again.
	7.b) Getting rid of old drivers, use one or more of the sections that apply to you:
		-------------------------------------------------------------------------------------------------------
		If you used Envy to attempt a previous nvidia install please run this command now before you go on:

               sudo envy --uninstall-all 
		sudo dpkg -P envy 

		-------------------------------------------------------------------------------------------------------
		If you have some old Ubuntu repository/restricted driver manager attempts installed please run this command before you go on:

		sudo apt-get remove --purge nvidia*
                sudo rm /lib/restricted-modules/.nvidia*

		-------------------------------------------------------------------------------------------------------
		If you have a failed NVIDIA*.run (drivers from the nvidia.com site) run this command before you go on:

		sudo nvidia-installer --uninstall

		-------------------------------------------------------------------------------------------------------
####################################################################################
##................................................................................##
## Alright Now Assuming That You are starting with a clean slate lets move forward##
##................................................................................##
####################################################################################

8) CTRL-ALT-F1
	8.a) Okay were in Command Line only now, we have a little left to do in here.
	8.b)login:
	8.c)Password:

9) sudo /etc/init.d/gdm stop
	9.a) This step shuts down the x-server and gnome desktop manager

10) sudo chmod a+x ./NVIDIA*.run
	10.a) We made the nvidia installer executable.

11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.

12) sudo /etc/init.d/gdm start
	12.a) You should see an Nvidia Logo, and then be put at your login screen, 
              you should also be able to enable desktop effects.

**Optional But recommended:**
13) To get the driver to update itself when a new kernel is installed from the update
    manager be sure to follow the guide in this link:
     http://ubuntuforums.org/showpost.php?p=5227704&postcount=1
```
Here's a click link for the guide mention in step 13
[http://ubuntuforums.org/showpost.php?p=5227704&postcount=1](http://ubuntuforums.org/showpost.php?p=5227704&postcount=1)

I will continue to update this guide as I find new things, but I am not really following this thread any longer as the OP seems to have moved on.

If I refer you to this guide from another thread, then please continue posting in the thread we met on. GL and hope this guide helps you.

~Starcannon

Thanks

---

### Post by Undertwotimes on 2008-11-19
Great guide thanks dude!  Two comments that might help people, I had to install the linux-headers package to compile the nvidia drivers.  I also had to edit xorg.conf and add 1920x1200 res in there.  Thanks again.

---

### Post by BunnyGirlDoom on 2008-11-21
Squished screen:

I have tried to solve the following problem myself, but I am admitting partial defeat and coming to you for suggestions. This topics seems relevant enough so instead of starting a new thread (I haven't turned up any searches with this problem) I decided to pos here.

I have a Dell Inspiron 2650 with GeForce2 GO graphics card. I have the 96.43.06 version installed using Hardware Driver manager. I also have medium desktop effects enabled.

The problem that I'm having is that about 70% of the time, my computer loads up but after the option screen (I am running dual boot with XP SP2), the display is squished over to the left side of the screen. It is literally pushed over so that half the screen is black and half is Ubuntu looking like it is having a mammogram. I am still able to login but since everything is mushed together vertically, what fun is that? ;)

Anyway, the other 30% of the time it loads up absosmurfly fine, full screen at 1024X768 with desktop effects.

So, the driver is working correctly *sometimes* - but I am assuming that during the start up process it is conflicting with something.

This doesn't happen when the driver is not installed or working in low graphics mode. If the driver is not installed I never get th squished screen, but I would prefer to have my resolution beyond 800X600 and I'd also like some moderate desktop effects.

In case this matters, there is no problem like this when booting into XP, it's only when loading Ubuntu does this happen.

I am stumped.

Any ideas?


Thanks!

---

### Post by BunnyGirlDoom on 2008-11-21
Double post. Sorry.

---

### Post by Zimmer on 2008-11-22
@BunnyGirlDoom
You appear to be using the correct driver for your legacy card.
See if you can see what is happening via the xorg.log and the syslog.


[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#seealso](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia#seealso)

---

### Post by BunnyGirlDoom on 2008-11-29
Thanks for the response Zimmer =) I have been away for most of the week so forgive the late reply.

I think I have solved it on my end. On a hunch I went into BIOS and peaked around. Figured it had to do something with startup. Anyway, my BIOS has a setting for - I think it was - detecting displays. CRT, LCD or Auto. Mine was set to auto. I set it to LCD since I don't connect a CRT to it. Saved changes, exited BIOS and I haven't had the squished screen thing happen since. 

If this does happen again, I'll be sure to get the xorg and syslog info.

Thanks!

---

### Post by Gregz on 2008-12-06
OK I tried this on ubuntu server 8.10 and couldn't get past step 4.
It pulls up a blank screen. It says it is looking but has empty page.

Step 5 does not work either same as above, Tho I did finally get a list and added nvidia to step 4. BUT can't pull it again.

I have ubuntu server 8.10

Nvidia GX7600GS card

---

### Post by Zimmer on 2008-12-07
> **Gregz said:**
> OK I tried this on ubuntu server 8.10 and couldn't get past step 4.
It pulls up a blank screen. It says it is looking but has empty page.

Step 5 does not work either same as above, Tho I did finally get a list and added nvidia to step 4. BUT can't pull it again.

I have ubuntu server 8.10

Nvidia GX7600GS card

Just a question, why do you need a 3d proprietry driver running a server? Is the vesa driver not adequate?

The simplest solution I have found to my Nvidia problems has been Envy.

install envyng-gtk  for GNOME  (or envyng-qt for Kubuntu (I think))

run envyng and pick the relevant radio button for ATI or Nvidia cards,  and the appropriate action.

If you are in a fix already, uninstall the drivers using Envyng, then re install them using envyng.
See Alberto's web site for more info..
[http://albertomilone.com/envyfaq.html](http://albertomilone.com/envyfaq.html)

---

### Post by Gregz on 2008-12-08
> **Zimmer said:**
> Just a question, why do you need a 3d proprietry driver running a server? Is the vesa driver not adequate?

The simplest solution I have found to my Nvidia problems has been Envy.

install envyng-gtk  for GNOME  (or envyng-qt for Kubuntu (I think))

run envyng and pick the relevant radio button for ATI or Nvidia cards,  and the appropriate action.

If you are in a fix already, uninstall the drivers using Envyng, then re install them using envyng.
See Alberto's web site for more info..
[http://albertomilone.com/envyfaq.html](http://albertomilone.com/envyfaq.html)





Because I also host a game on it and like to get on it and play plus do some other work on it. I need the 3d to do these things. :guitar:

---

### Post by Zimmer on 2008-12-09
Fair enough :)  are you hosting ET by any chance?

---

### Post by Benic on 2009-01-21
> **starcannon said:**
> 
        11) sudo ./NVIDIA*.run
	11.a) Answer to the affirmative for all questions.
	11.b) Be sure to specifically say you DO WANT it to write a new xorg.conf
	11.c) If you somehow answered incorrectly on the last question in the installer then:
		c.I) sudo nvidia-xconfig #this will write a new or attempt repair of
                     an xorg.conf file for you.


At this moment, the Nvidia driver tries to build a kernel module (if I remember correctly). Then it stops, saying ERROR: Unable to build the NVIDIA kernel module. I put the log in attachment. I'm wondering if it could be caused by a wrong driver. I have a Dell Latitude C840 (GeForce 440) and I use the 96.43.07 driver. What did I do wrong?

---

### Post by dj_flx on 2009-04-10
I followed the instructions, but now not only is that card effectively bricked, but I can no longer use my other, older tnt2 vanta card, even after restoring the backed up xorg.conf and removing the "nv" from the restricted modules. I had to re-install the 71 driver and now I have that back... but worse, because glx no longer loads anymore, and it did before.

---

### Post by amor0fati on 2009-05-04
> **Benic said:**
> At this moment, the Nvidia driver tries to build a kernel module (if I remember correctly). Then it stops, saying ERROR: Unable to build the NVIDIA kernel module. I put the log in attachment. I'm wondering if it could be caused by a wrong driver. I have a Dell Latitude C840 (GeForce 440) and I use the 96.43.07 driver. What did I do wrong?

I get this same problem.  before this it wouldn't allow me to activate the drivers, and now I can't even see the drivers.

---

### Post by Benic on 2009-05-05
> **amor0fati said:**
> I get this same problem.  before this it wouldn't allow me to activate the drivers, and now I can't even see the drivers.

I tried envyng and it was the only way I could install the nvidia drivers.

---

### Post by amor0fati on 2009-05-05
I tried envy.  I can't remember exactly what it said, but it was something along the lines of not having any support for my system.

---

### Post by Zimmer on 2009-05-05
> **amor0fati said:**
> I tried envy.  I can't remember exactly what it said, but it was something along the lines of not having any support for my system.
envy or envyng?
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Which system? 
 
Legacy?

[http://albertomilone.com/envyfaq.html](http://albertomilone.com/envyfaq.html)

---

### Post by amor0fati on 2009-05-05
Must've done something wrong the last time, because I tried it again and got a different output...still problematic though:
```
~$ sudo envyng -t


 +-------------------------------------------------+
 |                                                 |
 |             Welcome to EnvyNG                   |
 |    Developed by Alberto Milone (aka tseliot)    |
 |                                                 |
 +-------------------------------------------------+


 +-----------------------------------------------------------+
 |    EnvyNG Menu                                            |
 |                                                           |
 |    1 - Install the NVIDIA driver                          |
 |                                                           |
 |    2 - Uninstall the NVIDIA driver                        |
 |                                                           |
 |    3 - Install the ATI driver                             |
 |                                                           |
 |    4 - Uninstall the ATI driver                           |
 |                                                           |
 |    5 - Restart the Xserver                                |
 |                                                           |
 |    6 - Restart your computer                              |
 |                                                           |
 |    7 - Exit                                               |
 |                                                           |
 |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
 +-----------------------------------------------------------+
Please select one of the activities displayed above and press ENTER:

1
 +----------------------------------------------------------------------------+
 | Number | Candidate Version  | Installed Version | Compatible | Recommended |
 |----------------------------------------------------------------------------|
 | 0      | 180.51-0ubuntu1    | -                 | +          | +           |
 |----------------------------------------------------------------------------|
 | 1      | 173.14.16-0ubuntu1 | -                 | +          | -           |
 |----------------------------------------------------------------------------|
 | 2      | 96.43.10-0ubuntu1  | -                 | -          | -           |
 |----------------------------------------------------------------------------|
 | 3      | 71.86.08-0ubuntu1  | -                 | -          | -           |
 +----------------------------------------------------------------------------+
Please select the number corresponding to the desired driver and press ENTER 
(or type another number and press Enter to go back to the previous menu): 
0
False


 +--------------------------------------------------------+
 |    Error:                                              |
 |                                                        |
 |    EnvyNG has detected that the headers for            |
 |    your kernel are missing and cannot be installed     |
 |                                                        |
 +--------------------------------------------------------+

```

---

### Post by Zimmer on 2009-05-05
Aha you have not downloaded the headers for your kernel.
Find the headers in Synaptic that match your latest kernel and install them...

Also check  which driver your graphics card is supported by??

[http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/173.14.09/README/appendix-a.html)

Check which driver you should use .

---

### Post by amor0fati on 2009-05-05
This is odd, in synaptic, I already have linux-headers-2.6.28-11, but should I have 12?  Also, I've noticed that on bootup, my grub still seems to only have Intrepid 8.10 and no Jaunty.  I'm assuming this is probably a big source of my problems.

Just adding this:
```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		7bd72270-3f33-4a86-91e9-9d14fcc9258b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7bd72270-3f33-4a86-91e9-9d14fcc9258b ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		7bd72270-3f33-4a86-91e9-9d14fcc9258b
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=7bd72270-3f33-4a86-91e9-9d14fcc9258b ro  single
initrd		/boot/initrd.img-2.6.28-11-generic
```

to the top of menu.lst should do the trick?

---

### Post by amor0fati on 2009-05-05
So envyng worked after that and I installed 173, as 180 didn't seem to support my card.

---

### Post by Zimmer on 2009-05-06
So, you were not actually booting Jaunty... and I guess then you had no headers for the kernel that you were booting into which stopped the Nvidia driver loading properly....  had you not discovered this you could have spent a long time bemoaning how Jaunty was no different to Hardy, maybe.....  :)

---

