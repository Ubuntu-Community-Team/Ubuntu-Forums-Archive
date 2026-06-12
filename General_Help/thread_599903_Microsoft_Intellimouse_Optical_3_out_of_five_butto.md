---
title: "Microsoft Intellimouse Optical 3 out of five buttons work"
date: 2007-11-01
forum: General Help
---

### Post by spoonie on 2007-11-01
Hi Ive got a  Microsoft Intellimouse Optical 5 button mouse but button 4 and 5 are not found. In  UT2004 and etwq and everything else, when you try to map the buttons button 4 is button 3 and button 5 is button 1 .Ive gone in and change my xorg.conf using this example witch did work when I was running gentoo

[http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations#Microsoft_Intellimouse_Optical]("http://gentoo-wiki.com/HOWTO_Advanced_Mouse/Individual_Configurations#Microsoft_Intellimouse_Optical")

my xorg.conf

> Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option          "ZAxisMapping" "4 5 8 9"
    	Option          "ButtonMapping" "1 2 3 6 7 10 11"
EndSection

There must be something I'm not doing wright.:( 

Any help would be great thanks all

---

### Post by cherryjello on 2007-11-13
check this thread: [http://ubuntuforums.org/showthread.php?t=316441&highlight=five+button+mouse](http://ubuntuforums.org/showthread.php?t=316441&highlight=five+button+mouse)

You got it "almost right".  

```
Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "**ExplorerPS/2**"
Option "ZAxisMapping" "4 5"
Option "ButtonMapping" "1 2 3 6 7"
EndSection
```

That should work for you.
If you have the Emulate3button option, set it to false.

---

