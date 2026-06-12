---
title: "mouse config acting strange. xorg looks good"
date: 2008-02-22
forum: General Help
---

### Post by anjilslaire on 2008-02-22
Hey folks.

I have a recurring issue with my ps2 mouse. 
3 button with scroll wheel (5 button essentially)
Kubuntu 7.10
This occurs every few weeks, drives me nuts, then disappears again after a reboot/ xorg restart or 2.

OK:
If I scroll the wheel up, it does NOT move, but displays the right button context menu. Thats correct. When I scroll up, I get the following options normally associated with the right-mouse button:
Back
Forward
Reload
Bookmark
etc
Obviously, the above are browser context options. (Using Firefox). If I'm in Konqueror or Dolphin, it does the same, often highlighting or launching files and folders inadvertantly.
Mouse section of xorg follows:
```

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
EndSection

```

Thoughts? I can't see anything out of the ordinary. This is driving me nuts!
Thanks :)

Update:
Tried switching to ExplorerPS/2. Everything's fixed. Funny, its just a cheap old logitech optical mouse. Whatever, my scroll is working again :)

---

