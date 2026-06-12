---
title: "Keyboard Volume Control Steps"
date: 2007-01-10
forum: General Help
---

### Post by wsmoser2004 on 2007-01-10
I have a wireless keyboard which has a volume knob.  The knob works, but for one tiny little "click" that I turn the knob, the volume increases by a lot (this is Kubuntu Edgy by the way).  The volume jumps by something like 10% per "click", so in 10 clicks (about a quarter turn of the knob) I've gone from 0% volume to 100%.  Is there any way to change the amount that it jumps?  I'd like a more smooth operation.  Thanks.

---

### Post by wsmoser2004 on 2007-01-15
*crickets*

The forums are silent...  Anybody have an idea?

---

### Post by sirlancelot on 2007-01-21
This is also something I would like to change, a 10% step is way too much and pretty much makes my volume knob pointless, I'd like to change it to 2% or 5% even.

**EDIT** I'd prefer it to be done with xmodmap or even the native app that currently adjusts the volume 10% at a time.

---

### Post by wsmoser2004 on 2007-01-25
Well sirlancealot, it looks like we're alone in this one :)

I found a way to do it, although it's kind of a hack and I don't like it very much.  The solution I found is at [http://www.kde-forum.org/artikel/14212/Volume--Hotkeys.html]("http://www.kde-forum.org/artikel/14212/Volume--Hotkeys.html").  Essentially, it involves making two scripts: 

> 
#!/bin/bash
#INCR contains the percentage to increase
INCR=5

VOL="`dcop kmix Mixer0 masterVolume`"
VOL="$((${VOL}+${INCR}))"
if [ "${VOL}" -gt "100" ]; then
  VOL="100"
fi

dcop kmix Mixer0 setMasterVolume ${VOL}


...AND...

> 
#!/bin/bash
#DECR contains the percentage to decrease
DECR=5

VOL="`dcop kmix Mixer0 masterVolume`"
VOL="$((${VOL}-${DECR}))"
if [ "${VOL}" -lt "0" ]; then
  VOL="0"
fi

dcop kmix Mixer0 setMasterVolume ${VOL}


I named them VolumeUp.sh (the first one) and VolumeDown.sh (the second one) and put them in my home directory.  Then, add entries for both of them into the K Menu (right click the 'K', click 'K Menu Editor') and create new entries anywhere in there for them.  (I tried to hide mine).  Just make sure the "command" field points to the script, and make sure you turn OFF launch feedback (very important, otherwise everytime you turn the knob you get the little bouncing thing by your mouse).  Then, go into System Settings -> Keyboard & Mouse -> Keyboard Shortcuts (Left Side) -> Command Shortcuts (Tab).  Find the two entries for volume up and down that you added to the K Menu, and assign your shortcut key (or knob) to each one.  (To assign the knob, do the same thing you would do to set up a button, but instead of pressing a button just turn the knob in the right direction.)

I don't really like it because now the cool bar that shows me how high the volume is has disappeared, and I also have those two extraneous entries in the K Menu.  Maybe I'll come up with something else...if only I knew what program/script was called when I raise or lower the volume!

---

### Post by midorigin on 2007-02-05
I've been feeling the same way you guys are. The step is frustratingly large, to the point where I find myself just avoiding the volume buttons altogether. I really would like to find a more "correct" way to fix it.

Mine also seems to jump by unpredictable amounts each time; sometimes it's 11%, sometimes 9%. Pressing up and then down never brings me back to where I started. Does anyone else's do this too?

(For the record: Kubuntu 6.10 Edgy, ThinkPad X60)

---

### Post by zeltak on 2007-11-08
any progress made with the problem?

i also have the step thing annoying me (its 12% in kubuntu Gutsy). the hack is also really annoying me and could really do without!

thx

Zeltak

---

### Post by craigels39 on 2008-01-12
I have this problem with the volume on both my desktop keyboard and my laptop.  Both running Kubuntu Gutsy, KDE 3.5.8.  As sirlancelot requested, I would like to fix this problem in the native app, rather than with scripts.  Does anyone know exactly what program is doing the volume adjustment.  ALSA mixer?  KMix?

---

### Post by craigels39 on 2008-01-15
OK, here is a bit of a workaround.  Like wsmoser2004's suggestion, you lose the nice OSD for the volume, but it doesn't involve scripts.

-Open the Mixer window in KMix -> Settings -> Configure Global Shortcuts
-Set the shortcuts for volume up and down to 'None'
# I left mute alone, because since it's boolean, might as well have the OSD, but your call
-Close all of that
-From the Run Command dialog or a terminal, run 'kcmshell khotkeys'
# I ran mine without a sudo, so I'm assuming the changes are at the user level, not system-wide
-Under 'Preset Actions', create a new action, name it something smart for Volume UP
-Set the 'Action Type' to 'Keyboard Shortcut -> Command/URL (simple)'
-On the 'Keyboard Shortcut' tab, set the keystroke with the proper keys
-On the 'Command/URL Settings' tab, enter the command 'amixer -q set Master 1+ unmute'
-Apply the settings

-Add another Action in the same manor for Volume DOWN
-Use the command 'amixer -q set Master 1- unmute'
-Apply

-Volume changes will still show up in KMix, so you can check your work.  The only downfall is no OSD.

There you go, you can adjust the step using the integer variable in the command.

You can also create shortcuts for other volume controls, like 'Shift + XF86AudioIncrease' for PCM by changing the 'Master' variable of the command to 'PCM'.  You can see the names of your other controls by running 'alsamixer' from a terminal. (ESC exits alsamixer) This is also useful if your Master isn't called Master.

---

### Post by sirlancelot on 2008-02-09
Using Gnome Gutsy (7.10), Open up Configuration Editor:
Applications -> System Tools -> Configuration Editor

Navigate to this setting:
/apps/gnome_settings_daemon/volume_step

Set it to whatever you want, I used 3. The number indicates percentage.

Hope you all enjoy this as much as I do!

---

### Post by SilvaRizla on 2008-04-12
How do you do it on KDE?

---

