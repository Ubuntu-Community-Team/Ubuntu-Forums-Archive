---
title: "Optical Mouse Problems"
date: 2007-05-08
forum: General Help
---

### Post by TheFuzzy0ne on 2007-05-08
Hi everyone. I know there are lots of threads spread around on this subject, but I believe the problem I am experiencing is nothing to do with it, so I started a new thread.

I have a Logitech MediaPlay mouse, and although I never had any drivers installed for it, the buttons registered correctly with "xev". This was about a week ago when I was using Dapper. Since then, I've done a totally fresh install of Feisty, and it's done nothing but impress the hell out of me so far, apart from this one problem I have, which is starting to give me a headache.

The problem is that one of the buttons on the side of the mouse, gives the same button number as the right mouse button (button 3). This is also true of the button next to it, which gives the same button number as the middle mouse button (the scroll wheel when depressed), which is button 2. Just about every other button on my mouse sends out a keycode.

I get keycode 234 when I tilt the scroll wheel to the left 234, and keycode 233 when I tilt to the right. But neither of the tilts register until I click the scroll wheel first inside of the xev window, or I scroll with the wheel (in either direction) in the xev window.

I hope this make sense and that you can get the idea of the problems I'm having. What's changed between Dapper and Feisty with regards to anything that could be related to my problem? Is there something I need to configure in order to get the buttons to send the codes they're meant to?

---

### Post by dcstar on 2007-05-09
> **TheFuzzy0ne said:**
> 
........
I hope this make sense and that you can get the idea of the problems I'm having. What's changed between Dapper and Feisty with regards to anything that could be related to my problem? Is there something I need to configure in order to get the buttons to send the codes they're meant to?

Check you /etc/X11/xorg.conf file and see what has been set for the mouse (in both systems, if you can).

---

### Post by TheFuzzy0ne on 2007-05-09
Unfortunately, I can't :(

Perhaps I should reinstall Dapper. Although I binned my DVD as it had seen better days. Hehe.

Thanks for your input.

Daz.

---

### Post by kobewan on 2007-05-13
This mouse will work on Feisty just fine! First, backup your xorg.conf file with ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.bak
``` Then, edit xorg. If you are using Ubuntu then it should be:```
gksudo gedit /etc/X11/xorg.conf
```

Find the section which contains your mouse, which should say something like 'Identifier	"Configured Mouse"'. Change the section so that it reads like this:```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"evdev"
	Option    	"Name"			"Logitech USB Receiver"
EndSection
```

It should now work perfectly! You can also set it up to send custom commands/key strokes, so you can use it like a remote in any application that you want.

---

