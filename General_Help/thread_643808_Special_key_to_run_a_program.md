---
title: "Special key to run a program"
date: 2007-12-18
forum: General Help
---

### Post by r-mo on 2007-12-18
I've got some special keys on my tablet, one of them being rotate screen and another I want to use to launch an on-screen keyboard.  They didn't have keycodes so I've given them some with setkeycodes so now they show up with xev (do I need to add these commands to rc.local or are they remembered?)

Now I'm just missing the final step to make the keys: a) run a script to rotate the screen using xrandr, and b) run xvkbd.  Where can I set this up? I've been into prefs->keyboard shortcuts but can't find anything in their to make a custom one.

---

### Post by weblordpepe on 2007-12-19
Yeah I'd like to know that too. Me too me too.

---

### Post by r-mo on 2007-12-19
> **r-mo said:**
>  They didn't have keycodes so I've given them some with setkeycodes so now they show up with xev (do I need to add these commands to rc.local or are they remembered?)


The answer to that was yes :) I'll do some more googling today to try and find an answer to the mapping thing, unless someone pops up with the answer on here.

---

### Post by roadkillbunny on 2007-12-20
Hi guys,

Here is what I do. I also have a automatic rotation script based on orientation of the laptop (has a built in accelometer) which I'll document later. Anyways, here is the script that rotates the screen 90 to the current position and fixes the stuff for the wacom device named "stylus". You will also need the python-xrandr extension, available via PPA here: 

deb [http://ppa.launchpad.net/displayconfig-gtk/ubuntu](http://ppa.launchpad.net/displayconfig-gtk/ubuntu) gutsy main

```

#!/usr/bin/python
import os,time,re,sys;
from xrandr import xrandr

def listDevices():
        return ["stylus"];

def rotate(mode):
        codes={xrandr.RR_ROTATE_0:"0", xrandr.RR_ROTATE_90:"2", xrandr.RR_ROTATE_180:"3", xrandr.RR_ROTATE_270:"1"}
        if(mode!=screen.get_current_rotation()):
        #                               log(str(x)+","+str(y))
        #                               log(str(screen.get_current_rotation())+"rotate"+str(nextMode))
                screen.set_rotation(mode);
                screen.apply_config()
                for i in listDevices():
                        os.system("xsetwacom set "+i+" Rotate "+codes[mode])
                time.sleep(1);

def main():
        #only rotate in tablet mode
        nextMode = {
                xrandr.RR_ROTATE_0: xrandr.RR_ROTATE_90,
                xrandr.RR_ROTATE_90: xrandr.RR_ROTATE_180,
                xrandr.RR_ROTATE_180: xrandr.RR_ROTATE_270,
                xrandr.RR_ROTATE_270: xrandr.RR_ROTATE_0
                }[screen.get_current_rotation()]
        rotate(nextMode);

screen=xrandr.get_current_screen()
main()

```

Make sure to give it execute permissions.

The next step is to bind that command to your button. Just open up gconf and go to /apps/metacity/keybinding_commands and set command_1 to the path to the script. Then go to global_keybindings and edit run_command_1 to the keycode of your button. You have to type in the keycode converted to hex. For example, my rotate button was reported by xev to be 219 so I typed in 0xdb.

You can then set command_2 to your onscreen keyboard. I use cellwriter, you might give it a try. Wery good handwriting recognition.

---

