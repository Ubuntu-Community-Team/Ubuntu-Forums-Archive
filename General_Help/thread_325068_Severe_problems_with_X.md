---
title: "Severe problems with X"
date: 2006-12-24
forum: General Help
---

### Post by HyperHacker on 2006-12-24
So I've never really used Linux before but I installed Ubuntu 6.10 on this older computer to use as a MythTV box. It has a serial mouse (has a PS/2 port, but I have a perfectly good serial mouse here already) and that old pre-PS/2 keyboard port that's big and round, whatever it's called.

The first problem I noticed was that the graphical installer requires a mouse, and doesn't support serial mice. This not only prevents people using older systems, but also people using some special devices for the physically handicapped, from using the graphical installer. Instead you have to download another 900MB file and boot from that to install in text mode.
I did manage to get the mouse working after install by editing /etc/X11/xorg.conf, took a lot of trial and error though.

So once I got it installed I booted it up and it asked for a login. OK, type my username... it comes out as "hhhhyppeeeeeeeeeeeeeeeeeeee...". There's a major problem with the keyboard repeat rate; characters are randomly repeated about 2-200 times for each press. It's almost impossible to type this way. I thought the keyboard must have been defective but it works just fine in the consoles, only in the graphical interface it has a problem.
"modprobe psmouse rate=40" did nothing, the other workarounds [here](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/39315) all seem to be for laptops.

After about 20 minutes I managed to log in and went to the menu to turn off the key repeat. Except any time I click any of the menu buttons after logging in, it just freezes right up. The mouse still moves, but nothing responds. Restarting X shows the login prompt again, then the system quite literally slows to a stop; the cursor blinks slower and slower and eventually it completely locks up; mouse not moving, Num Lock not working, etc.

---

### Post by cilynx on 2006-12-25
Ok, I hate to put it this way, but that's kinda neat.  I've never heard of Ubuntu dying from old simple input devices.  I hope someone more important than me reads this.  All I can really do is pass this on to the guys at UbuntuLite and hope it gets resolved there.

---

### Post by HyperHacker on 2007-02-15
I apologize for the bump, but I went out and bought a PS/2 keyboard... when I went to plug it in I realized this machine doesn't have a PS/2 *keyboard* port, only a PS/2 *mouse* port. >_< A USB keyboard should work, shouldn't it? There are USB ports but I don't know if they work.

---

### Post by gradedcheese on 2007-02-15
What you have is called an AT keyboard :)  I can't remember the last time I've used one, and I've never used one with any Linux system, so I have no idea about support for them.  Yeah, USB keyboards will work fine.  I assume the USB ports are via some PCI card, hopefully the card works.  Serial mice do work, but (by design) there isn't much an OS can do to "detect" them, as far as I know.

---

### Post by HyperHacker on 2007-02-15
Yeah, they're on the same card as the PS/2 mouse port and an IR connector.

---

### Post by pxwpxw on 2007-02-15
I remember having to go into the bios setup and enable usb keyboard. On a pc.
It had ps/2 and usb onboard stuff..

---

### Post by HyperHacker on 2007-02-22
Well I got a PS/2 -> USB convertor which seems to work nicely. However, the key repeating problem is still there! :mad: It happens less often, and the repeated keystrokes are fewer (generally 1-5) but can still be enough to fill the keyboard buffer and cause much beeping for one keypress. And though I didn't change anything else, my serial mouse once again does not work. I managed to move the cursor once and then nothing. I would have thought I could bring up the menu with a keypress, but I pressed just about every key in sequence and nothing happened, except after I finished with the F keys, it started endlessly spawning Ubuntu Help Center windows which I had no way to close. I mean there was one popping up every second, I had about 8 when I hit the reset button.

Honestly what the hell. Ubuntu is supposed to be easy to use, great for beginners etc? Shouldn't it at least support one of the three computers I've tried it on enough to be useable then? -_- (Especially given one of them is a Gateway XG843 laptop, which I really hope isn't "too old to run Linux".)

[edit] After the hard reboot the mouse is working again, and the keys don't seem to be repeating anymore. O_o Now what's the command to give my mouse a longer cord? ;-)

The Screensaver Preferences has a problem. I clicked HyperSpace and found it to be some very CPU-intensive screen saver that on this computer just locks up the program. I managed to force it closed but now every time I open it, guess what, HyperSpace is selected again. Fortunately after a few attempts I managed to click another before it loaded. And if you have an old computer like mine don't even *think* of clicking Skyrocket, unless you're veeeery patient.

The display doesn't work correctly. At 800x600@75hz, it's shifted far to the right, leaving a big black spot at the left while the right edge of the screen is right up against the edge of the monitor.

Well it's working (slowly, obviously) for now, so let's see if I can get a network card installed. Maybe even a TV tuner that Windows rejects like sour milk. :-p

[edit 2] It won't boot at all with one network card (D-Link DFE-538TX RevD2). With another it boots, but once again, the mouse does nothing. In fact, trying to move the mouse on the login screen locks up the entire system! Virtual Console is acting funny now; I have to press right Alt+Ctrl+Fx to enter one, but left Alt+Ctrl+F8 to return to the GUI. Doing this actually only displays a blinking cursor, then Ctrl+Alt+F7 shows the GUI again. :confused: After that I can move the mouse once, then it locks up completely and I can't even enter a Virtual Console anymore.

Might these be signs of overheating? After the lockup it wouldn't even POST (blinking cursor) until I unplugged it, and it's taking longer now on the part of the boot screen that it gets stuck on with the other network card.

Also key repeat is just as bad as it used to be now. >8^(

[more edit] Actually it won't boot with either network card, I just hadn't pushed the second one far enough in for it to be powered on.

---

