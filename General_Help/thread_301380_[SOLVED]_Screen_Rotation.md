---
title: "[SOLVED] Screen Rotation"
date: 2006-11-17
forum: General Help
---

### Post by Linuturk on 2006-11-17
[B][SOLVED!]

See last post for the resolution:

Many thanks to 23meg!
Many thanks to joejaxx on irc.freenode.net #fluxbuntu

If a forum moderator could move this thread to the HOWTO section to help others, I'd appreciate it.

[/SOLVED][/B]

First, I'd like to give major props to the Edgy Developers. With each new release, it seems Tablet PC support is getting better and better.

I've noticed that under System > Preferences > Screen Resolution I now have a new option of Rotation that works wonderfully.

I'd like to have my machine automatically rotate the screen when I rotate and lock down my tablet screen.

OR

I'd settle for the commandline option so I can produce a Panel Launcher to simply click on with my Tablet Pen.

Any help?

---

### Post by 23meg on 2006-11-17
Create a launcher with the command ```
xrandr -o left
```to rotate the screen 90 degrees counterclockwise from the normal position. Other options for the command are *-right*, *-normal* and *-inverted*.

---

### Post by Linuturk on 2006-11-17
Thanks!

Now I have two new buttons on my panel. One for Tablet mode, and one for normal mode.

---

### Post by Linuturk on 2006-11-17
Got a problem now when I switch to tablet mode. 

My tablet pen works fine in the normal mode, but when I'm in tablet, the wacom driven pen doesn't recognize the new layout or resolution. This means if I move the pen up, the actual mouse goes left.

Can anyone help me shed some light on this?

---

### Post by 23meg on 2006-11-18
You can rotate the pen layout with xsetwacom, which is in the package wacom-tools.

---

### Post by Linuturk on 2006-11-18
$ xsetwacom --help
Usage: xsetwacom [options] [command [arguments...]]
Options:
  -h, --help                 - usage
  -v, --verbose              - verbose output
  -V, --version              - version info
  -d, --display disp_name    - override default display

Commands:
  list [dev|param]           - display known devices, parameters
  set dev_name param [values...]   - set device parameter by name

$ xsetwacom list
Synaptics Touchpad unknown   
eraser           eraser    
cursor           cursor    
stylus           pad   

$ xsetwacom list eraser
List: Unknown argument 'eraser'
$ xsetwacom list cursor
List: Unknown argument 'cursor'
$ xsetwacom list stylus
List: Unknown argument 'stylus'

Ok, I've played around with xsetwacom a bit, but I can't seem to get any parameters listed so I know what to edit.

The man page is basically empty, and points you to /usr/share/doc/wacom-tools/ which is basically empty as well. 

I also couldn't find a documentation package in Synaptic.

---

### Post by 23meg on 2006-11-18
```
xsetwacom list param
```will list the parameters. For example```

xsetwacom set cursor Rotate CW
```should rotate the cursor clockwise.

---

### Post by Linuturk on 2006-11-18
Ok, got this fixed by running this command after entering tablet mode.

xsetwacom set stylus Rotate CCW

Now I'll map the launchers to a script that runs these commands.

---

### Post by Linuturk on 2006-11-18
Ok, I've made a couple of scripts. Simply download them and follow the directions in the comments of the script.

After you've moved the scripts to /usr/local/bin and chmod +x the scripts, create two panel launchers to switch between the modes.

Tablet Mode:
Type: Application
Name: Tablet Mode
Command: tabletpcmode.sh
Comment: Rotates the screen for tablet mode

Laptop Mode:
Type: Application
Name: Laptop Mode
Command: laptopmode.sh
Comment: Rotates the screen for laptop mode

here is the code for the scripts:

tabletpcmode.sh

```
#!/bin/bash

# Tablet PC Mode Script tabletpcmode.sh
# Made for the Toshiba Sattelite R15-S822
# Running Ubuntu Edgy Eft 6.10
#
# Last Updated: 11-18-2006
# Maintained by Justin "Linuturk" Phelps
# linuturk@gmail.com
# 
# Move this script to /usr/local/bin
# Run 'sudo chmod +x tabletpcmode.sh'
# Be sure laptopmode.sh is installed as well

xrandr -o left && xsetwacom set stylus Rotate CCW
exit 0
```

laptopmode.sh

```
#!/bin/bash

# Laptop Mode Script laptopmode.sh
# Made for the Toshiba Sattelite R15-S822
# Running Ubuntu Edgy Eft 6.10
#
# Last Updated: 11-18-2006
# Maintained by Justin "Linuturk" Phelps
# linuturk@gmail.com
# 
# Move this script to /usr/local/bin
# Run 'sudo chmod +x laptop.sh'
# Reverses the effects of tabletpcmode.sh

xrandr -o normal && xsetwacom set stylus Rotate none
exit 0

```

This should work for any machine with a stylus installed via the wacom-tools package in the repositories. Also make sure you can set your screen rotation via the System > Preferences > Screen Resolution.

---

### Post by jstroot on 2006-11-27
Does this work with Beryl and aiglx? At work, I have dual Samsung syncmaster 213T monitors.  It would be interesting to flip both monitors on end and use the cube.

--jstroot

---

### Post by Linuturk on 2006-11-27
It doesn't seem to work correctly on my laptop with Beryl and AIGLX.

---

### Post by 23meg on 2006-11-27
My screen is messed up when I rotate using Beryl as well. I'll investigate the cause and post back sometime later.

---

### Post by Mirandur on 2006-12-05
I tried this on my Acer C312, but it seems something is blocking me from rotating my screen. The 'Screen rotation' in System/Preferences/Screen resolution is grayed out, and xrandr gives the following errormessage:
```
$ xrandr -o left
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```

I've added the line ```
 Option "RandRRotation" 
``` to the nvidia driver section in my xorg.conf file, but it seems it's *still* not working...

Any help, anyone?

---

### Post by Linuturk on 2006-12-13
As my howto says, this will only work if you have the option to rotate your screen in the System/Preferences/Screen Resolution. Anything more technical than that is way beyond me.

---

### Post by smitty5533 on 2007-01-24
Thanks 23Meg!
:D

---

### Post by PreseliComputing on 2007-02-24
Try  Option "RandRRotation" "On"

As I always say: it wont work unless its plugged in!! :)

---

### Post by giuliastro on 2007-03-18
> **23meg said:**
> My screen is messed up when I rotate using Beryl as well. I'll investigate the cause and post back sometime later.

Any news on this? Beryl seems to keep have this problem when rotating the monitor.

---

### Post by 23meg on 2007-03-18
> **giuliastro said:**
> Any news on this? Beryl seems to keep have this problem when rotating the monitor.

I don't use Beryl anymore, so I have no means of investigating it. Search the Beryl forums for the issue, and if it hasn't been discussed, start a thread there.

---

### Post by andrew frank on 2007-03-22
the two scripts work very well on my fujitsu siemens stylistic 5032 tablett (under 7.04)

thank you linuturk!  very well done!

andrew

---

### Post by Linuturk on 2007-09-26
Here is a nice fat update for all you tablet users.

I've managed to get this rolled into one script with the help of some internet resources. Let me start with the script.

```
#!/bin/sh

# Change System Input orientation for Tablet Mode
# Created by Sebastian Henschel for Toshiba m200
# Modified by Justin "Linuturk@gmail.com" Phelps on 9/24/2007
# to work with Ubuntu 7.04 Satellite R15-S822
# Depends on wacom-tools from repo
#
# 9/24/2007
# Copied original from http://tuxmobil.org/toshiba_portege_m200_tablet_linux.html
# Modified to include the stylus orientation change.
# Change keycodes to match buttons on R15-S822
#
# Make executable and move to /usr/local/bin
#
orientation=`/usr/bin/xrandr --query | /bin/grep "Current rotation" | /usr/bin/awk '{print $4}'`
if [ "$orientation" = "normal" ]; then
	/usr/bin/xrandr -o left
	/usr/bin/xsetwacom set stylus Rotate CCW
	/usr/bin/xmodmap -e "keycode 10 = KP_Left"
	/usr/bin/xmodmap -e "keycode 12 = KP_Up"
	/usr/bin/xmodmap -e "keycode 11 = KP_Right"
	/usr/bin/xmodmap -e "keycode 13 = KP_Down"
	/usr/bin/xmodmap -e "keycode 14 = KP_Enter"
else
	/usr/bin/xrandr -o normal
	/usr/bin/xsetwacom set stylus Rotate none
	/usr/bin/xmodmap -e "keycode 11 = 2 at twosuperior oneeighth twosuperior oneeighth"
	/usr/bin/xmodmap -e "keycode 13 = 4 dollar onequarter currency onequarter currency"
	/usr/bin/xmodmap -e "keycode 10 = 1 exclam onesuperior exclamdown onesuperior exclamdown"
	/usr/bin/xmodmap -e "keycode 12 = 3 numbersign threesuperior sterling threesuperior sterling"
	/usr/bin/xmodmap -e "keycode 14 = 5 percent onehalf threeeighths onehalf threeeighths"
fi
```

**Please note this script is specific to my model (Toshiba R15-S822)**

You should be able to adapt this to any tablet though. I'm attaching a tar.gz file with all my source files, including a .desktop file to copy to your panel. I'm also including all the original, depreciated scripts from earlier in this thread.

First, use xev to map out your tablet buttons.
Second, modify the script with the correct keycodes for your buttons. (If you don't want to do this, just comment out the lines that have xmodmap) 
This script is also specific to the default us keyboard. If your keys are laid out different, you'll have to figure out the original configs for the second have of the xmodmap sections.

Move the screen_orientation file to /usr/local/bin/ and make it executable. 

I've also been able to get the onboard keyboard a smaller size, and I have it starting up on GDM so I can use the tablet pen to input my login and password. There are forum posts elsewhere that demonstrate that process.

I highly recommend Jarnal as a One-Note replacement. You can find it at GetDeb.net

---

### Post by High Camp on 2007-09-30
> **Mirandur said:**
> I tried this on my Acer C312, but it seems something is blocking me from rotating my screen. The 'Screen rotation' in System/Preferences/Screen resolution is grayed out, and xrandr gives the following errormessage:
```
$ xrandr -o left
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  155 (RANDR)
  Minor opcode of failed request:  2 (RRSetScreenConfig)
  Serial number of failed request:  12
  Current serial number in output stream:  12
```

I've added the line ```
 Option "RandRRotation" 
``` to the nvidia driver section in my xorg.conf file, but it seems it's *still* not working...

Any help, anyone?

Did anyone find a solution to this problem? I have an Acer C310 and I get the same error. These are tablet pc's so the video card can handle rotation. I have added "Option" "RandRRotation" "true" to the xorg.conf file and that got nothing.

Any help will be appreciated,

---

### Post by Linuturk on 2007-10-01
That's beyond my expertise. Wish I could help you. Try searching Google for your issue if you haven't found anything on the forums.

---

### Post by smurtguy on 2007-10-14
someone already posted the solution to your rotation problem on the previous page.

the correct option is not just

 Option "RandRRotation"

you have to add either on or true after it 

Option "RandRRotation" "On"


And this needs to go in the screens section.

BTW I was having this exact problem as well and found this fix in another post.

---

### Post by Ansset Mikal on 2007-11-23
I've been trying to implement Linuturk's solution, but I can't seem to get it working.  I'm very new to Linux, but there isn't anything in the solution that doesn't make sense to me; it just fails to do anything when I try to run any of the scripts.  I'm running a Toshiba R15 S829 with Ubuntu 7.10, so things shouldn't need to be too different from what was posted, should they?  Thanks to Linturk for his work on this and anyone else who wants to try to help me out.

---

### Post by High Camp on 2007-11-23
I've found this ([http://ubuntuforums.org/showthread.php?t=590747](http://ubuntuforums.org/showthread.php?t=590747)) the method the best to use. As you will see in one of my posts you will also have to make sure "RandRRotation" is set to "on".

Post here or there if you need more help,

---

### Post by Cresho on 2007-12-27
Boy! what a treat it was for me to read this thread and finaly rotate my screen.

I am running

compiz
ubuntu 7.10

on a

8800gt graphics card
HP w2408 monitor 16:10 19200x12000 resolution TFT screen.

Now to get the rotation working, i

sudo gedit /etc/X11/xorg.conf

and added
 Option "RandRRotation"
so it looks like this.

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
    Option         "NoLogo" "true"
    Option "RandRRotation"
EndSection


rebooted just for the effects to take place.

now in
System->Preferences->Screen resolution

the option to rotate is now available and working.

thanks all!

small update, if I use the nvidia to rotate screen, I see problems with compiz.  using ubuntu screen resolution to rotate screen is way way better.

---

