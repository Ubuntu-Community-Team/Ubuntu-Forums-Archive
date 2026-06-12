---
title: "Touchpad Override?"
date: 2008-03-16
forum: General Help
---

### Post by stinkywizzlecheeks on 2008-03-16
Hi,

I hope I'm posting in the right forum; apologies if not.
 I'm running Ubuntu Gutsy on an old Dell Latitude 610 and there is a hardware issue with the mouse - it sometimes goes haywire and the pointer becomes completely uncontrollable. It's a problem that existed in windows and continues now that I'm running Ubuntu exclusively, leading me to believe it's hardware related. The previous owner of the laptop said the problem disappeared when he plugged an external mouse in (he was using WinXP), but this hasn't solved the problem for me. 
So I'm wondering - is it possible to set up my laptop in Ubuntu to only recognize an external mouse when it's plugged in, ignoring the touchpad and nub (that little thing in the middle of the keyboard on some laptops - i don't know what it's called)?

Thanks, any help is appreciated.

---

### Post by justleen on 2008-03-16
yes, the config for your mouse and touchpad  (and the nubby) are in /etc/X11/xorg.conf.
you can try to simply comment everything (add a "#" at the start of the line) out which you dont need.

---

### Post by stinkywizzlecheeks on 2008-03-16
Right, this is a little over my head. Is there maybe an application that will control these sorts of things?
If not, I guess I will just live with it.
Thanks anyway.

---

### Post by hyperandy on 2008-03-16
The only Gui I have seen for touchpads is gsynaptics, you can find it in the package manager. you have to add a line to your xorg.conf file

after you download the package add: 

Option 	    "SHMConfig"  "True"

to the Identifier  "Synaptics" section


REMEMBER TO RESTART
HOW TO DO THIS:

backup and editing xorg.conf:
Code:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
sudo gedit /etc/X11/xorg.conf

Adding the line (Option "SHMConfig" "true") to Synaptics InputDevice Section, the whole section should look like this:
Code:
exmple:
 Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Protocol" "auto-dev"
    Option         "HorizEdgeScroll" "0"
    [COLOR="Red"]Option         "SHMConfig" "true"[/COLOR]	
EndSection

install the Gsynaptics to manage preferences for touchpad. Available in "System > Preferences > Touchpad"
Code:

sudo aptitude install gsynaptics


also try Disabling touchpad while typing:
Put the command below in the start session of gnome, under "System > Preferences > Sessions > Add"
Code:

syndaemon -i 1 -d

the 1 tells it to wait 1 second after a keystroke to give the mouse back to you.

---

### Post by stinkywizzlecheeks on 2008-03-17
Thanks for the response.
It doesn't seem to want to install gsynaptics, though. It keeps telling me "0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded,"

---

