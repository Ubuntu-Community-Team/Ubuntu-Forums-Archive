---
title: "Please need to Turn OFF the monitor by command line !"
date: 2019-04-27
forum: General Help
---

### Post by strik3 on 2019-04-27
Hi, please is there a way to turn off the monitor/display from command line ?
I tried several ways but no result, xrandr works but after few 2 seconds return the display without moving mouse or press a key, not possible to keep it permanent, please I really really need it.
A command shortcut to switch on - off would be amazing !!
Ubuntu is 18.04 .

Thanks

---

### Post by strik3 on 2019-04-27
Why this command don't remain permanent but disappear after 2 seconds ?? :
xrandr --output DP-1 --off

---

### Post by Holger_Gehrke on 2019-04-28
Try 'xset dpms force standby'.

Holger

---

### Post by strik3 on 2019-04-28
xset doesn't work at all !!! vbetool , xrandr, none of this works ?
Is there someone who can turn off the monitor in Ubuntu 18.04 ??

Need it very much this feature !
Thanks

---

### Post by dragonfly41 on 2019-04-28
Some more ideas in this thread ..

[https://ubuntuforums.org/showthread.php?t=1786695](https://ubuntuforums.org/showthread.php?t=1786695)

---

### Post by strik3 on 2019-04-28
Thanks very much for your help, but none of the commands related above is working on ubuntu 18.04, unfortunately !

---

### Post by Rubi1200 on 2019-04-28
Perhaps this would work?

To turn off monitor

```
busctl --user set-property org.gnome.Mutter.DisplayConfig /org/gnome/Mutter/DisplayConfig org.gnome.Mutter.DisplayConfig PowerSaveMode i 1
```

To turn on:

```
busctl --user set-property org.gnome.Mutter.DisplayConfig /org/gnome/Mutter/DisplayConfig org.gnome.Mutter.DisplayConfig PowerSaveMode i 0
```

Source:
[https://askubuntu.com/questions/253818/manually-turn-off-monitor/1062631#1062631](https://askubuntu.com/questions/253818/manually-turn-off-monitor/1062631#1062631)

---

### Post by strik3 on 2019-04-28
Thanks but not working, after less than a seconds monitor goes back on

---

### Post by him610 on 2019-04-28
If the suggestions by Rubi1200 in #7 work, it might be a good idea to assign the Off/On functions some combination of function keys so you are not fumbling around in the dark.

---

### Post by strik3 on 2019-04-28
Really, I would celebrate if the suggestion #7 would work more than u can imagine, but it doesn.t work, monitor turn off but after 1 second comes back on, doesn't remain off. !! Thanks anyway for your reply ... I didn't know this was so impossible to achieve in linux !!

---

### Post by Holger_Gehrke on 2019-04-28
Two ideas:
Have you got something like caffeine or the XFCE Presentation Mode running ? If you do, those work by inhibiting screen savers through DBus and producing synthetical input events. That would explain the behaviour of xset and xrandr ...

If your display is external and the connection between PC and display includes DDC/CI (Display Data Channel / Command Interface; VGA, HDMI, DVI and Display Port usually include this feature) you could try ddccontrol. Install it from the repositories with 'sudo apt install ddccontrol', then run 'sudo ddccontrol -p' to find out what i2c-bus is used for DDC/CI and whether you display offers Power Control through DDC. Mine does, the relevant piece of the output looks like this:
```

    > Power control
        > id=dpms, name=DPMS Control, **address=0xd6**, delay=-1ms, type=2
          Possible values:
            > id=on - name=On, value=**1**
            > id=standby - name=Standby, value=**4**
          supported, value=1, maximum=5

```
So if i run
```

ddccontrol -r 0xd6 -w 5 dev:/dev/i2c-1
``` the display behaves as if I had pressed the power button to put it into standby (no, the 5 is not a typo; sending the 4 that the display tells me to has absolutely no effect; must be some kind of bug, either in the display firmware or in ddccontrol ...). Running
```

ddccontrol -r 0xd6 -w 1 dev:/dev/i2c-1
``` makes it switch back on.

Holger

---

### Post by sisco311 on 2019-04-28
Try to delay the command:
```
sleep 0.3 && xset dpms force off
```

---

### Post by him610 on 2019-04-28
I normally turn my monitor off with the (low tech) power switch.

---

### Post by strik3 on 2019-04-30
I would REALY like to do as Holger_Gehrke wrote, sounds really but, but here I got problem to detect the bus code with ddcontrol ...
I tried this commands :

```
sudo ddccontrol -p
```
```
sudo ddccontrol -d dev:/dev/i2c-4
```
```
sudo LANG= LC_ALL= ddccontrol -p -c -d
```
Results is a whole Warming ...
```
ddccontrol version 0.4.3
Copyright 2004-2005 Oleg I. Vdovikin (oleg@cs.msu.su)
Copyright 2004-2006 Nicolas Boichat (nicolas@boichat.ch)
This program comes with ABSOLUTELY NO WARRANTY.
You may redistribute copies of this program under the terms of the GNU General Public License.

Probing for available monitors..........I/O warning : failed to load external entity "/usr/share/ddccontrol-db/monitor/ROW0000.xml"
Document not parsed successfully.
.I/O warning : failed to load external entity "/usr/share/ddccontrol-db/monitor/SAM0AC6.xml"
Document not parsed successfully.
.....
Detected monitors :
 - Device: dev:/dev/i2c-5
   DDC/CI supported: Yes
   Monitor Name: VESA standard monitor
   Input type: Digital
  (Automatically selected)
 - Device: dev:/dev/i2c-4
   DDC/CI supported: No
   Monitor Name: VESA standard monitor
   Input type: Digital
Reading EDID and initializing DDC/CI at bus dev:/dev/i2c-5...
Invalid sequence in caps.
Invalid sequence in caps.
Invalid sequence in caps.
I/O warning : failed to load external entity "/usr/share/ddccontrol-db/monitor/ROW0000.xml"
Document not parsed successfully.

EDID readings:
    Plug and Play ID: ROW0000 [VESA standard monitor]
    Input type: Digital
=============================== WARNING ===============================
There is no support for your monitor in the database, but ddccontrol is
using a basic generic profile. Many controls will not be supported, and
some controls may not work as expected.
Please update ddccontrol-db, or, if you are already using the latest
version, please send the output of the following command to
[EMAIL="ddccontrol-users@lists.sourceforge.net"]ddccontrol-users@lists.sourceforge.net[/EMAIL]:

LANG= LC_ALL= ddccontrol -p -c -d

Thank you.
=============================== WARNING ===============================

= VESA standard monitor 
```
Not so lucky mmmmm !!!!!!!!!!!!

---

### Post by Holger_Gehrke on 2019-04-30
If I read this right, you've got two displays connected, one with DDC/CI and one without and neither known to ddccontrol (they are not even in the current version on [github]("https://github.com/ddccontrol/ddccontrol-db/")). Since the dpms power-management register at 0xd6 is part of the VESA standard according to /usr/share/ddccontrol-db/monitor/VESA.xml, you could try 'ddccontrol -r 0xd6 -w 4 dev:/dev/i2c-5'  or - if it has the same problem as my display '-w 5'. Or you could try the other register in the VESA-Profile labelled  "power" at 0xe1 with -w 0 for off and -w 1 for on (although that one doesn't do anything on my display, neither good nor bad ...).

Holger

---

### Post by strik3 on 2019-04-30
Thanks for your help but none, I tried this commands but same errors, 
```
sudo ddccontrol -r 0xd6 -w 4 dev:/dev/i2c-5    OFF
sudo ddccontrol -r 0xd6 -w 5 dev:/dev/i2c-5    OFF
sudo ddccontrol -r 0xd6 -w 1 dev:/dev/i2c-5    ON

sudo ddccontrol -r 0xe1 -w 0 dev:/dev/i2c-5    OFF
sudo ddccontrol -r 0xe1 -w 1 dev:/dev/i2c-5    ON
```

In Task manager none of Caffeine or XFCE Presentation Mode are running .

I think I should give up, too complicated turn off the Display in Ubuntu 18.04, I would like to have the button on the Display but I don't have unfortunately, one Display is my tv samsung via Hdmi, but the main Display is a laptop display dismantled and used as monitor with a LVDS Cable and dedicated card, I have an NVIDIA card and the driver is NVE4.
Thanks anyway for your kind help, very much appreciated .

---

### Post by dragonfly41 on 2019-04-30
Currently I can turn off my display in Ubuntu 16.04 by toggling SuperKey+P
SuperKey is the one with Window icon, bottom left in keyboard.
I can go through three cycles of pressing these two keys.

---

### Post by strik3 on 2019-05-01
> **dragonfly41 said:**
> Currently I can turn off my display in Ubuntu 16.04 by toggling SuperKey+P
SuperKey is the one with Window icon, bottom left in keyboard.
I can go through three cycles of pressing these two keys.

Yes, in ubuntu 16.04 I had this option too, then in Ubuntu 18.04 this option its off unfortunately, and was a very very very usefull options.

---

