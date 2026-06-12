---
title: "Wacom Intuos3 A4 Problem("
date: 2008-01-11
forum: General Help
---

### Post by ConstanT1ne32 on 2008-01-11
This is video i made about my problem [http://www.youtube.com/watch?v=mrHGz2EnS2w](http://www.youtube.com/watch?v=mrHGz2EnS2w), as you can see my tablet doesnt see the whole screen, plx help!

---

### Post by spayced on 2008-01-12
I have this problem too, on a different tablet though. It's odd because everything else works great: pressure sentitivity, eraser, left click, right click... etc. It seems as though the driver isn't picking up on the screen resolution. My tablet seems to think I'm running 800x600 resolution and when I try to move beyond that I hit an invisible wall (aka the edge of the tablet) like you do there. Would be nice if there was a way to just put in my resolution, i'll keep digging..

---

### Post by spayced on 2008-01-12
Okay I might have solved it, I went through the wacom troubleshooting pages and noticed I had a line missing so I added it. It's not fixed completely but it seems to be better.

open a terminal type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bakw
```
that first line was optional is just makes a backup of your current xorg file
```
sudo gedit /etc/X11/xorg.conf
```
opens up your xorg for editing

go down to this part:
```
Section "InputDevice"
	
	# /dev/input/event
	# for USB
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"cursor"
	#Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection
```

add this line under type cursor:
> 	Option		"Mode"		"relative"

so the section looks something like this now:
```
Section "InputDevice"
	
	# /dev/input/event
	# for USB
	Identifier	"cursor"
	Driver		"wacom"
	Option		"Device"	"/dev/wacom"# Change to 
	Option		"Type"	"cursor"
	Option		"Mode"		"relative"
	#Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection
```

Save.
Close.

Press ctrl+alt+backspace to restart x server.

If that doesn't work you could also try mode absolute instead, another thread suggested doing that with mixed success. Another idea to minimize the effect is to lower your screen resolution.

---

### Post by ConstanT1ne32 on 2008-01-12
Nice job, can explain it again in more detail, specialy how to get to editing part

---

### Post by spayced on 2008-01-13
The second command you put in terminal>
```
sudo gedit /etc/X11/xorg.conf
```
gets you to the editing part.

Keep in mind my solutions don't fix it they just make it a little better...
Did you try reducing your screen resolution? Did that help?

---

### Post by ConstanT1ne32 on 2008-01-16
Hmm i fixed the problem few days ago. Go to device manager> Human Interface devices> Wacom tablet and uninstall the driver then resrt pc.

After that ur tablet should feel ur screen and you will be able to use software change settings.

---

