---
title: "Enabling 5 button mouse in Ubuntu 8.04"
date: 2008-04-24
forum: General Help
---

### Post by skuter on 2008-04-24
Hi all

I wonder if anyone knows how to set this up.  I want enable the 5 button mouse.  I have logitech mx510 mouse.


Thanks.

---

### Post by yaknowwat on 2008-04-25
in 8.04 everythings been relayed out for how you set up the xorg.conf to simplify it.
(its not as hack styled but that also means not all the settings are visible in it.)

I've done an xserver-xorg reconfigure and this is the output style it now has.

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

I suggest backing up your /etc/X11/xorg.conf file

then doing the
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

after which your multi button mouse should be enabled (worked for me.)
oh yeah when it ask about emulating a 3 button mouse i chose no.

---

### Post by ztheory on 2008-04-25
Open up your xorg.conf file using your file browser. this is in /etc/X11/xorg.conf

Locate the lines that probably look like this:

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
EndSection

Comment out those lines, puting # before all the lines. Put this right below it:


Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ExplorerPS/2"
Option "Buttons" "7"
Option "ZAxisMapping" "4 5"
Option "Emulate3Buttons" "false"
Option "ButtonMapping" "1 2 3 6 7"


If this doesn't work, try changing the 6 and 7 to 4 and 5, *** those represent your side buttons and scroll-clicks.

---

### Post by yaknowwat on 2008-04-25
> **ztheory said:**
> Open up your xorg.conf file using your file browser. this is in /etc/X11/xorg.conf

....

erm not so sure about that idea because what i posted was the new xorg-xserver layout design for mouse and keyboard they use and it has my 5 button mouse working flawlessly in 8.04

Its just the xorg.conf file is not upgraded correctly when upgrading to 8.04 from and older version it only makes a proper xorg.conf on a clean install or a reconfigure.

Also the whole mouse mapping thing in 7.10 has never worked for me personally. (and i tried it so many times)

---

### Post by skuter on 2008-04-26
will try your suggested solutions.

Thank you.  Will let you know if it works :)

---

### Post by dandellion on 2008-04-26
try btnx [http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

---

### Post by skuter on 2008-05-19
I have tried yaknowhat your suggestion but i am not that linux advance to this as yet 

i had reinstall ubuntu already sincei got my mouse killed off completely

any chance of a step by step?

---

