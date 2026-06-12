---
title: "evdev makes X not start"
date: 2007-10-28
forum: General Help
---

### Post by Excalibre on 2007-10-28
I'm trying to configure a logitech mx610 mouse; I've found various guides but I can't get them to work.

Bear with me, I'm going to try to be thorough. By changing the mouse part in xorg.conf to this

```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ExplorerPS/2"
	Option		"Buttons"	"7"
	Option		"ZAxisMapping"	"4 5"
	Option		"ButtonMapping"	"1 6 3 2 7"
	Option		"Emulate3Buttons"	"false"
EndSection

```

I was able to get 7 buttons to work, but there don't seem to be any settings that will make it recognize 9, which is what this mouse has. I can't seem to get it to recognize the horizontal tilt buttons on the mousewheel.

So most of the guides I find say to use the evdev driver instead, but when I try, X fails majorly when it tries to start (I'm using Gutsy 64-bit and an nVidia 8500GT video card, if that matters. Video is working fine other than this.) Ubuntu resorts to trying to make it start in some sort of low resolution mode or something, but even that doesn't work right and the display was so screwed up I had to ctrl-alt-backspace and fix my xorg.conf from the console.

I know that evdev is installed - I checked. How do I use it, though? As far as I can tell, it's necessary to use it to enable more than seven buttons on a mouse (or at least that's what every guide I find says.) But I can't.

I found this thread [http://ubuntuforums.org/showthread.php?t=436101](http://ubuntuforums.org/showthread.php?t=436101) and it looks promising but I'm a bit too new and dumb to understand how to do what it says. It seems I should be mapping my mouse to some particular "event"? How do I do that?

---

