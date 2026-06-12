---
title: "disable touchpad while using keyboard (gsettings not working)"
date: 2020-02-27
forum: General Help
---

### Post by pseudotheist2 on 2020-02-27
Title really says it all.  I m trying to disable my touchpad while typing, and I've found instructions using gsettings, but those seem to be ignored.  I've also looked at the device properties in xinput, but there don't seem to be any relevant settings there.  Any help?

Running Disco Dingo, if version is important.

---

### Post by coley9225 on 2020-02-28
Your problem is not unique, I have the same issue on my computer. I have written 2 bash scripts that may help. First, try to run this in terminal 'synclient touchpadoff=1'. no quotes, and spacing is important. If this doesn't disable your touchpad, then my scripts will be of no help. I have 2 versions of each, 1 for lxde desktop, and the other for lxqt. I'll show each, with the lxde version first. I use the lxde version in lubuntu 18.04, and lxqt version in lubuntu 19.10.

#!/bin/bash
#written by Charles Massey with help from the forums
#Feb. 15, 2020
#Toggle touchpad on/off with keyboard input
#will turn answer into all uppercase
#will read only first letter of answer

echo "Do you want touchpad on?"
    read answer
    answer=${answer^^}
    answer=${answer:0:1}
if [[ ${answer} = 'Y' ]] ;
    then $(synclient touchpadoff=0) 
    echo "touchpad on"
else
    $(synclient touchpadoff=1) 
    echo "touchpad off"

fi
#I made a second script to open new terminal and run this bash, then close the new window
#I assigned a hotkey combo to run without needing to open a terminal. 

This will turn touchpad on or off. You have to open a terminal and run this script there.

#!/bin/bash
#start new terminal, run bash script ./tt.sh, and exit terminal after 2 second delay
lxterminal --command "./tt.sh && sleep 2 && exit" 

This script, when run in terminal, will open new terminal, run previous script, then close new terminal. I made a hotkey combo ( windowskey + t) to run this straight from desktop. To run with lxqt desktop, there is a couple minor changes, and I'm   posting the scripts for lxqt below.

#!/bin/bash
#written by Charles Massey with help from the forums
#Feb. 15, 2020
#Toggle touchpad on/off with keyboard input
#will turn answer into all uppercase
#will read only first letter of answer

echo "Do you want touchpad on?"
    read answer
    answer=${answer^^}
    answer=${answer:0:1}
if [[ ${answer} = 'Y' ]] ;
    then $(synclient touchpadoff=0) 
    echo "touchpad on"
else
    $(synclient touchpadoff=1) 
    echo "touchpad off"
    
    sleep 2

fi
#I made a second script to open new terminal and run this bash, then close the new window
#I assigned a hotkey combo to run without needing to open a terminal


#!/bin/bash
#start new terminal, run bash script ./tt.sh, and exit terminal after 2 second delay
#must be run with bash script tt.sh
qterminal -e "/home/charles/tt.sh && exit" 

I hope 1 of these help you out. Good luck.

---

### Post by pseudotheist2 on 2020-02-28
Thanks for the response, but even after installing xserver-xorg-input-synaptics I get "Couldn't find synaptics properties. No synaptics driver loaded?"

Would installing one of the other xserver-xorg-input packages possibly help me?  How would I tell which one?

---

### Post by vanadium on 2020-03-01
It may be enough to disable "tap-to-click", and then, you can use following script and bind it to a hotkey:

```

#!/bin/bash
STATUS=$(gsettings get org.gnome.desktop.peripherals.touchpad tap-to-click)
case $STATUS in
	true )
		gsettings set org.gnome.desktop.peripherals.touchpad tap-to-click false
#		notify-send "Tap-to-click Off"
	;;
	false )
		gsettings set org.gnome.desktop.peripherals.touchpad tap-to-click true
#		notify-send "Tap-to-click On"
	;;
esac

```
Remove the comment marks (#) at the start of the "notify-send" lines to have notifications when you toggle the setting.

---

### Post by pseudotheist2 on 2020-03-14
Yep, disabling tap-to-click also appears to do nothing.  As far as I can tell, it appears like gsettings isn't controlling my touchpad at all.  I did neglect to mention that this is a detachable 2-in-1; does the fact that the touchpad is basically a USB device change what i would have to do to change the settings?

---

### Post by audunmb on 2020-08-06
This seems to be an issue with libinput. I have the same issue. Is there a bug report for his?

---

### Post by SeijiSensei on 2020-08-06
Many reports dating back years.  [https://www.google.com/search?q=bugs+ubuntu+disable+keyboard+while+typing](https://www.google.com/search?q=bugs+ubuntu+disable+keyboard+while+typing)

In particular, [https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1351772](https://bugs.launchpad.net/ubuntu/+source/unity-settings-daemon/+bug/1351772)

Some blame libinput, others blame the Synaptics driver. I [thought]("https://bugs.kde.org/show_bug.cgi?id=419538") the version of libinput that was shipped with Kubuntu 20.04 resolved the problem on my Lenovo with a Synaptics keypad, but it seems to have returned. For the moment I "solved" the problem by plugging in a wireless mouse adapter and telling Kubuntu to disable the touchpad when a mouse is plugged in. Means I have to use the mouse instead of the touchpad which is also annoying.

---

