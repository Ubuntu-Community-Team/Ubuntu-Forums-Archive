---
title: "Xubuntu 22.04 give tiny icons on display - how to force lower resolution permanently"
date: 2023-08-06
forum: General Help
---

### Post by JimLS on 2023-08-06
Have a Optiplex 7040 connected to a large LG TV.  It works ok if the TV is connected when the system boots although the icons are tiny.  If I switch on the TV later the display is only in the upper left corner.  Resolution defaults to 4096 x 2160.  I can manually switch to 1960 x 1080 which seems to work fine.  How can I force this resolution regardless of the TV being on or not.  It's being used as a DVR and the is not going to be on most of the time.

---

### Post by #&amp;thj^% on 2023-08-06
I use this others may have a different approach.
```
xrandr --output 'HDMI-A-0' --mode '1920x1080_60.00'
```
xrandr will give you your HDMI name.
Mine:
```
 xrandr
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-2 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080    120.00*+

```
Chech if yor GPU will handle the 69Hz first. (And you might already knnow that now)
This will only last the current Xsession so to make it permanent put that line in a/your "~/.xinitrc ".

---

### Post by JimLS on 2023-08-07
Tried xrandr.  Did it on the display hooked to the PC (not via ssh).  I can use the display adjustment gui to set the modes and it works ok.  couldn't get command line xrandr to work.

```
jim@jim-myth:~$ xrandr
Screen 0: minimum 320 x 200, current 4096 x 2160, maximum 16384 x 16384
HDMI-1 connected primary 4096x2160+0+0 (normal left inverted right x axis y axi>
   4096x2160     30.00*   25.00    24.00    29.97    23.98
   3840x2160     30.00    25.00    24.00    29.97    23.98
   2560x1440     59.95
   1920x1080    120.00   100.00   119.88    60.00    60.00    50.00    59.94   >
   1920x1080i    60.00    50.00    59.94
   1280x1024     60.02
   1280x720      60.00    50.00    59.94
   1024x768      60.00
   800x600       60.32
   720x576       50.00
   720x576i      50.00
   720x480       60.00    59.94
   640x480       60.00    59.94
   720x400       70.08
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
HDMI-3 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
jim@jim-myth:~$

jim@jim-myth:~$ xrandr --output 'HDMI-1' --mode '1920x1080_60.00'
xrandr: cannot find mode 1920x1080_60.00


```

I also noticed my files on the desktop that I copied some of the terminal output into have single quotes around the names when listing them in putty.  What's going on there?  I didn't put those in the names.
```
jim@jim-myth:~/Desktop$ ls
'mythinstall june2023'  'xrandr 7aug2023'
jim@jim-myth:~/Desktop$

```

---

### Post by #&amp;thj^% on 2023-08-07
I don't use Putty sorry, but what will this report:
```
 cat .xinitrc 
xrandr --output 'HDMI-0' --mode '1920x1080_60.00'
```
Her is mine with my suggestions now:
```
xrandr --listmonitors
Monitors: 2
 0: +DP-2 1920/344x1080/194+0+0  DP-2
 1: +HDMI-0 1920/698x1080/392+1920+0  HDMI-0

```

---

### Post by JimLS on 2023-08-07
I don't seem to have that file.
```
jim@jim-myth:~$ ls .*
.bash_history  .ICEauthority              .wget-hsts     .xsession-errors
.bash_logout   .lesshst                   .Xauthority    .xsession-errors.old
.bashrc        .profile                   .Xdefaults
.dmrc          .sudo_as_admin_successful  .xscreensaver

```

---

### Post by #&amp;thj^% on 2023-08-07
Good your here time is not on my side today, so can I see this now:
```
xrandr --listmonitors
```
Use the above with the HDMI "On @1920x1080"

---

### Post by JimLS on 2023-08-07
jim@jim-myth:~$ xrandr --listmonitors
Monitors: 1
 0: +*HDMI-1 1920/1600x1080/900+0+0  HDMI-1
jim@jim-myth:~$

---

### Post by #&amp;thj^% on 2023-08-07
Sorry I forgot this as well.
```
inxi -G
```
Just One Monitor then?
EDIT Off to work for a few short hours, will return.

---

### Post by JimLS on 2023-08-07
Yes, just one monitor - a big TV.

I didn't have inxi so had to install it.

```

jim@jim-myth:~$ inxi -G
Graphics:
  Device-1: Intel HD Graphics 530 driver: i915 v: kernel
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: modesetting
    unloaded: fbdev,vesa gpu: i915 resolution: 1920x1080
  OpenGL: renderer: Mesa Intel HD Graphics 530 (SKL GT2)
    v: 4.6 Mesa 22.2.5-0ubuntu0.1~22.04.3
jim@jim-myth:~$

```

---

### Post by #&amp;thj^% on 2023-08-07
Yep I figured it was over 50 inch's
Let's just go a easy route: [https://www.maketecheasier.com/change-screen-resolution-ubuntu/#arandr](https://www.maketecheasier.com/change-screen-resolution-ubuntu/#arandr)
You will need to install "arandr" though and follow that part of the page once again It's "Arandr"

---

### Post by JimLS on 2023-08-07
arandr appears to be just a gui for xrandr.  Am I missing something?

---

### Post by #&amp;thj^% on 2023-08-07
It sets as permanent if you read through all of the link.
Did it not work then?

---

### Post by #&amp;thj^% on 2023-08-11
It's a common courtesy to reply back when asking for help.
Otherwise i just Add names to my Ignore list, No big Deal there. (I get it some are just to cool to school)

---

### Post by MAFoElffen on 2023-08-11
I'm sorry if it seems I am jumping in cold... And i do not want to step on anyone's toes, in seeming like I want to high-jack the thread. Not my intention at all.

I feel like I need to to explain how things work under the covers in the Linux Graphics Layer. I think that once I explain that, that will help with this, and give you both ideas.

The Linux Kernel on boot checks which graphics devices are on the system and keeps note of them. It may get helpers from the cmdline boot parameters to set KMS modes as boot parameters.

If goes with those settings into the console, plymouth splash, and the DM graphical login screen. At the graphical login screen, the user assigns a user that logs in. The system inti's whichever graphics engine was choosen (xorg or wayland). Then looks for any user files, such as ~/.xintrc or /.bashrc and applies settings from them, then init's the graphics drivers...

During the graphics driver init, the graphics driver looks for displays that are turned on, and queries that capability of that display, using what is referred to as the EDID database, which is persistent in it's firmware and sets the display to "it's" preferred mode. That is unless another mode was set somewhere along the line... That somewhere can be anywhere along the process line from the kernel boot, to that point of time.

This works the same for the Linux Graphics Layer, for all of Linux, no matter the distribution or Flavor. This just happens to be more sensitive, and brought up more often in Mythbuntu... Where users maybe using devices between the computer and the display, or not have the display on when the computer is booted. Or the computer/display connection is not connected together all the time.

So since it cannot read the EDID all the time, or if the mode desired is not the preferred mode by the display, you have to provide it for the configuration. Why, because another piece of that is auto-plug-and-plug, where an intermittent kind of connection will end up trying to change the modes.

Are you two understanding that so far?

Xrandr is not a persistent setting across boots, and assumes that the user is using xorg xserver as the graphics engine... The way around that is two ways, either create an ~/.xinitrc file containing the xrandr set commands... or create a user xorg.conf file... with telling xorg to ignore if the EDID is there or not, define a mode for the display and use it as preferred. <<--- That has been the preferred way to do that with Mythbuntu for over a decade. That way they can use a Dolby or any other other kind of multiplexer or KVS type of switch, between the computer and display, and the computer does not have to see the display directly connected to have a mode set.

Does that make sense now? Does that give ideas for several ways to do that now?

---

### Post by #&amp;thj^% on 2023-08-11
> **MAFoElffen said:**
> 
Are you two understanding that so far?
Perfectly, I had suggested that  in my first post #4 "?.xinitrc file"
> **MAFoElffen said:**
> 
Xrandr is not a persistent setting across boots, and assumes that the user is using xorg xserver as the graphics engine... 

Respectfully agree to disagree on that,
that saved file from arandr gives the file to add to autostart or my case 
```
cat '/home/me/.screenlayout/mylayout.sh' 
#!/bin/sh
xrandr --output DP-0 --off --output DP-1 --off --output HDMI-0 --off --output DP-2 --primary --mode 1920x1080 --pos 0x0 --rotate normal

```
And that file should be placed in your AutoStart or Session Start-ups.

And don't be silly your never a highjacker in any I mean ANY of my posts/threads.
Your always Welcome...
But you have brought a point up, I don't use Gnome and the OP is on Xubuntu so my suggestions work for this.
Wayland may be a different cat all together, so warn on that part of the mix.

---

### Post by MAFoElffen on 2023-08-11
Yes. Your suggestion does work for this. As it should.

And... $HOME/.xinit has been a default method for setting the screen to Xubuntu users for over a decade.... LOL

Does the 'arandr' GUI wrapper for xrandr generate layout scripts for autostart? "If it does", then yes, then "it" uses the noted work-around to xrandr's non-persistent limitations. I think that is just a different perspective of that noted limitation.

LOL. You use a startup script (mylayout.sh) which 'sets' the modes via xrandr, because the underlying xrandr setting loses that mode over reboots (not persistent). Your layout script "is" the persistence, using the work-around for that... reissuing that command on login via autostart. So effectively the same.

There are a few other util's that work with Wayland for other desktops, that are similar to xrandr... kscreen-doctor, gnome-randr, wlr-randr, and wdisplays...

---

### Post by #&amp;thj^% on 2023-08-11
> **MAFoElffen said:**
> 
LOL. You use a startup script (mylayout.sh) which 'sets' the modes via xrandr, because the underlying xrandr setting loses that mode over reboots (not persistent). Your layout script "is" the persistence, using the work-around for that... reissuing that command on login via autostart. So effectively the same.

Actually I don't "use a startup script "  this was for the OP, you know me better than that.:P
But yes all the above is true and factual....

---

### Post by JimLS on 2023-08-11
> **1fallen said:**
> It sets as permanent if you read through all of the link.
Did it not work then?

No.  It didn't work.  It's only been 3 days ago so don't know why you are getting wound up about the delay.  I have things to do and am only working on this a bit here and a bit there and wanted to do some checking to make sure it wasn't working.  

The link you gave only showed using arandr.  It did not show calling the resultant file somehow so while it did set the mode it didn't persist on reboots.  It seems I need to put this file somewhere or link to it and there are several ways/places to do that.  And that was clearly NOT shown or even hinted at in the link.

I'm still a bit unclear on the best way to link to the output file of arandr.  A bit more detail on where to place scripts for startup and such would be very helpful.

---

### Post by #&amp;thj^% on 2023-08-11
> **JimLS said:**
> The link you gave only showed using arandr.  It did not show calling the resultant file somehow so while it did set the mode it didn't persist on reboots.  It seems I need to put this file somewhere or link to it and there are several ways/places to do that.  And that was clearly NOT shown or even hinted at in the link.

I'm still a bit unclear on the best way to link to the output file of arandr.  A bit more detail on where to place scripts for startup and such would be very helpful.
If you actually have that "whatever.sh" and for clarity that file would be in your /home/user_name/.screenlayout and that file whatever you named it goes in:
```
xfce4-session-settings
```
under "Application Autostart" tab at the top. You will hand add it. (See screenshot)
And This
> **JimLS said:**
> No.  It didn't work.  It's only been 3 days ago so don't know why you are getting wound up about the delay.  I have things to do and am only working on this a bit here and a bit there and wanted to do some checking to make sure it wasn't working.  
I have lots and lots of things to do as well and I spend time helping here in UF so I would appreciate that when your just tinkering as hobby or going to go off line for what ever reason, it's just good practice to notify all involved, so we can spend what time have more productively. That's just a Good thing to do right???

---

### Post by JimLS on 2023-08-11
Put the output script from arandr into ~/.xinitrc
It behaves as it has been.  It either gives me a screen with the display only filling the upper 1/4 or a completely blank screen.  If I issue the commands to exit myth FE (from memory as it isn't displayed) I get the desktop but still on the 1/4 upper left screen.

That's after reboot with the TV off and turning the tv on after boot.

---

### Post by JimLS on 2023-08-12
Added the script to application autostart list.  It doesn't work when  booting with the tv off (autologin).  If I then logout and login with  the TV on it adjusts as desired so there doesn't seem to be anything  wrong with how I set that up but an issue with when it is triggered and  persistance.  If I turn the tv off briefly and turn it back on it has  reverted to the old undesired setting.  Seems I somehow need to turn off  the automatic updates of resolution.

---

### Post by #&amp;thj^% on 2023-08-13
@JimLS  MAFoElffen and I have been brain storming, and the only other method known to work is, create this file like:
```
sudo nano /etc/X11/xorg.conf
```
With this added to it:
```

Section "ServerLayout"
  Identifier "Layout1"
  Screen "Screen1"
EndSection

Section "Device"
  Identifier "Device1"
  VendorName "Intel"
  BoardName "Intel HD Graphics 530"
  Driver "intel"
  Option      "DRI"  "iris"  # For Gen 8 and newer
  # DRI3 is the defualt driver for Intel, if that causes tearing problems, then
  # force DRI2 using the following:
  #Option "DRI" "2"
  Option "DPMS" "false"
  # These are tuning settings that will imporove performance for GNOME, KDE Plasma, Xfce, etc.
  # Of these tuning settings, if tearing appears, first try to set tearFree to "true"
  Option      "TearFree"        "false" 
  Option      "TripleBuffer"    "false"
  Option      "SwapbuffersWait" "false"
EndSection

Section "Monitor"
  Identifier      "HDMI-1"
  VendorName      "LG"
  ModelName       "SomeModel"
  HorizSync    30-107
  VertRefresh  48-120
  Option "UseEDID" "FALSE"

  #Native modes of Jim's LG TV on HDMI-1: 
  # "4096x2160_30.00" "3840x2160_30.00" "2560x1440_59.95" "1920x1080_120.00" "1920x1080_60.00" "1280x1024_6.00"

  # Modes Calculated from cvt
  # 4096x2160 29.98 Hz (CVT) hsync: 65.96 kHz; pclk: 362.00 MHz
  Modeline "4096x2160_30.00"  362.00  4096 4360 4792 5488  2160 2163 2173 2200 -hsync +vsync
  # 3840x2160 29.98 Hz (CVT) hsync: 65.96 kHz; pclk: 338.75 MHz
  Modeline "3840x2160_30.00"  338.75  3840 4080 4488 5136  2160 2163 2168 2200 -hsync +vsync
  # 2560x1440 59.91 Hz (CVT) hsync: 89.45 kHz; pclk: 312.00 MHz
  Modeline "2560x1440_59.95"  312.00  2560 2752 3024 3488  1440 1443 1448 1493 -hsync +vsync
  # 1920x1080 119.93 Hz (CVT) hsync: 139.12 kHz; pclk: 369.50 MHz
  Modeline "1920x1080_120.00"  369.50  1920 2080 2288 2656  1080 1083 1088 1160 -hsync +vsync
  # 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
  Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
  # 1280x1024 59.89 Hz (CVT) hsync: 63.67 kHz; pclk: 109.00 MHz
  Modeline "1280x1024_60.02"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
  # 1280x720 59.86 Hz (CVT 0.92M9) hsync: 44.77 kHz; pclk: 74.50 MHz
  Modeline "1280x720_60.00"   74.50  1280 1344 1472 1664  720 723 728 748 -hsync +vsync
  Option "PreferredMode" "1920x1080_60.00"
EndSection

Section "Screen"
  Identifier "Screen1"
  Device     "Device1"
  Monitor    "HDMI-1"
  DefaultDepth 24
  SubSection "Display"
    DefaultDepth     24
    Modes     "1920x1080_60.00" "4096x2160_30.00" "3840x2160_30.00"
  EndSubSection
EndSection

```
Save the file with key combo [Ctrl+o] and exit with [Ctrl+x]
After a reboot it should just work.

---

### Post by JimLS on 2023-08-13
Thanks!  I will give that a try.  I did find another way that I was going to try.  Here's the link (post #5) but I will try your suggestion first.

[https://ubuntuforums.org/showthread.php?t=2472453](https://ubuntuforums.org/showthread.php?t=2472453)

---

### Post by JimLS on 2023-08-13
Well, that was weird!  I created the xorg.conf file and rebooted, then  after a couple minutes turned on the tv.  I was greeted with a tty login  screen.  After logging in I was still in a text session.  The myth  backend was running because I could connect from another machine.   Unless you have some other suggestions that was a bust too.  I will try  out the other way I found.  Maybe that will work...

---

### Post by JimLS on 2023-08-13
Struck out on that one too.  I suppose I should check the logs to see what happened but not sure quite what to look for or where.  Seems like it should be easier to fix the resolution of the display...What now?  Set a cron job to run the resolution setting every minute?  That might just work but clearly a kludge.

---

### Post by JimLS on 2023-08-21
This is crazy.  There must be some way to set a fixed resolution for a display and stop the system from "helping" and adjusting it.  Maybe I should file a bug report that it isn't possible?  I doubt that's the real answer...

---

### Post by JimLS on 2023-08-22
Decided to try X11 config files.
Ran cvt to get modeset line and got this:
```
jim@jim-myth:/var/log$ cvt -v 1920 1080
# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```

Then stuck that in 10-monitor.conf file:
```

jim@jim-myth:/etc/X11/xorg.conf.d$ cat 10-monitor.conf
Section "Monitor"
        Identifier "your output"
        Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
EndSection

```
Tried putting that in several different locations but none seemed to work.  Initially based on:
[https://en.wikibooks.org/wiki/Guide_to_X11/Define_new_resolution](https://en.wikibooks.org/wiki/Guide_to_X11/Define_new_resolution)
I put it at:
/etc/X11/xorg.conf.d/10-monitor.conf
but based on the log I also tried it at:
/usr/share/X11/xorg.conf.d

Here are files and permissions at those locations:
```
jim@jim-myth:/etc/X11/xorg.conf.d$ ls -al
total 12
drwxr-xr-x  2 root root 4096 Aug 21 20:28 .
drwxr-xr-x 11 root root 4096 Aug 13 20:50 ..
-rw-r--r--  1 root root  147 Aug 21 20:28 10-monitor.conf


jim@jim-myth:/etc/X11/xorg.conf.d$ ls -al /usr/share/X11/xorg.conf.d/
total 40
drwxr-xr-x 2 root root 4096 Aug 22 06:58 .
drwxr-xr-x 5 root root 4096 Jul 10 06:56 ..
-rw-r--r-- 1 root root   92 Aug 21  2022 10-amdgpu.conf
-rw-r--r-- 1 root root  147 Aug 22 06:58 10-monitor.conf
-rw-r--r-- 1 root root 1350 Apr  4 01:20 10-quirks.conf
-rw-r--r-- 1 root root   92 Jul 11  2022 10-radeon.conf
-rw-r--r-- 1 root root 1429 Feb 11  2022 40-libinput.conf
-rw-r--r-- 1 root root  590 Apr  6  2020 51-synaptics-quirks.conf
-rw-r--r-- 1 root root 1751 Apr  6  2020 70-synaptics.conf
-rw-r--r-- 1 root root 3458 Apr  6  2022 70-wacom.conf
```
And here is the first of the log file:
```
jim@jim-myth:/var/log$ more Xorg.0.log
[     5.801]
X.Org X Server 1.21.1.4
X Protocol Version 11, Revision 0
[     5.801] Current Operating System: Linux jim-myth 6.2.0-26-generic #26~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Th
u Jul 13 16:27:29 UTC 2 x86_64
[     5.801] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-6.2.0-26-generic root=UUID=0806d544-94e8-44b5-bf91-c8
3cf9121c92 ro quiet splash vt.handoff=7
[     5.801] xorg-server 2:21.1.4-2ubuntu1.7~22.04.1 (For technical support please see http://www.ubuntu.com/sup
port)
[     5.801] Current version of pixman: 0.40.0
[     5.801]    Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
[     5.801] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     5.801] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Aug 22 07:01:54 2023
[     5.802] (==) Using config directory: "/etc/X11/xorg.conf.d"
[     5.802] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     5.803] (==) No Layout section.  Using the first Screen section.
[     5.803] (==) No screen section available. Using defaults.
[     5.803] (**) |-->Screen "Default Screen Section" (0)
[     5.803] (**) |   |-->Monitor "<default monitor>"
[     5.803] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[     5.803] (==) Automatically adding devices
[     5.803] (==) Automatically enabling devices
[     5.803] (==) Automatically adding GPU devices
[     5.803] (==) Automatically binding GPU devices
[     5.803] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     5.804] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     5.804]    Entry deleted from font path.
[     5.805] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     5.805]    Entry deleted from font path.
[     5.805] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     5.805]    Entry deleted from font path.
[     5.805] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     5.805]    Entry deleted from font path.
[     5.805] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     5.805]    Entry deleted from font path.
[     5.805] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[     5.805] (==) ModulePath set to "/usr/lib/xorg/modules"
[     5.805] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[     5.805] (II) Loader magic: 0x559412b52020
[     5.805] (II) Module ABI versions:
[     5.805]    X.Org ANSI C Emulation: 0.4
[     5.805]    X.Org Video Driver: 25.2
[     5.805]    X.Org XInput driver : 24.4

```

---

### Post by JimLS on 2023-08-27
Finally solved this with a custom edid file as detailed in another thread:
[https://ubuntuforums.org/showthread.php?t=2490215](https://ubuntuforums.org/showthread.php?t=2490215)

---

