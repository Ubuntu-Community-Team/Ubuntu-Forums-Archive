---
title: "random low-resolution at boot"
date: 2007-04-13
forum: General Help
---

### Post by total wormage on 2007-04-13
Hello fellow ubuntuers, this is once again a strange 'problem' I encountered.
I couldn't find any similar threads on the forums or on launchpad.

Sometimes when i boot my GDM appears on a resolution of 640*480, when I log in this resolution remains. If i just restart X everything appears fine.
I find this odd, and it could take up very much time for someone who doesn't restart X but tries to look up the problem in xorg.conf or where-ever when encountering this, because there is nothing wrong there. (as far as i know)

I'm using GeForce FX 5200 on a 64-bit system, with Ubuntu 7.04 Feisty Fawn 64-bit
And I'm using this nvidia driver: 1.0-9631

Does anybody else have this problem, is it worth filing a bug for? :]
:KS :KS

---

### Post by fanatik on 2007-04-13
I have seen this problem, but only when I was on Dapper, I believe. I haven't see it since I upgraded to Edgy.

I have a feeling it only occured when my box crashed and I had to physically turn it off - and yes then rebooting did correct it. Or I may have had to copy a saved version of my xorg.conf back.

It'll be interesting to see if it re-appears in Feisty, when I upgrade.

If there isn't already a bug for it and you can re-produce it regularly, you could file a bug report...

James.

---

### Post by total wormage on 2007-04-13
> **fanatik said:**
> I have seen this problem, but only when I was on Dapper, I believe. I haven't see it since I upgraded to Edgy.

I have a feeling it only occured when my box crashed and I had to physically turn it off - and yes then rebooting did correct it. Or I may have had to copy a saved version of my xorg.conf back.

It'll be interesting to see if it re-appears in Feisty, when I upgrade.

If there isn't already a bug for it and you can re-produce it regularly, you could file a bug report...

James.
thank you for saying that, it may point me to some cause
it never occured to me that it may be caused by hard resets, i should keep an eye out for that

---

### Post by grolm on 2007-05-28
I have the same effect - random low-resolution at boot. 
Motherboard ASUS p5ld2-v with Intel 950 graphics on board.

Could some body explain how to fix it or some work around?

---

### Post by total wormage on 2007-05-28
this is going to be a real hard one to file a bug report for, there is absolutely no information.

i can't reproduce this regularly, it just is totally random and happens just once in a great while for me.
silly things.

i wonder if there are more people having this ..

> **grolm said:**
> I have the same effect - random low-resolution at boot. 
Motherboard ASUS p5ld2-v with Intel 950 graphics on board.

Could some body explain how to fix it or some work around?
you know you can easily restart your X pressing CTRL + ALT + Backspace ?
it's not pretty and no solution to the problem, but it is faster than a restart :]

---

### Post by grolm on 2007-05-28
Many thanks to you for the shortcut! I have tryed it and it is really much faster!

I can reproduce it very often (probability about 0.3-0.4) but dont see any significant errors in xorg.log. 
But it is different in successfull and not successfull cases:

In not successfull case it ends with (full log is attached):

> 
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!


In successfull it is longer:
> 
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
(WW) I810(0): Extended BIOS function 0x5f05 not supported.
(II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.
(II) I810(0): Setting refresh with VBE 3 method.
(II) I810(0): Display plane A is enabled and connected to Pipe A.
(II) I810(0): Display plane B is disabled and connected to Pipe B.
(II) I810(0): Enabling plane A.
(II) I810(0): Display plane A is now enabled and connected to Pipe A.
(II) I810(0): Display plane B is now disabled and connected to Pipe B.
(II) I810(0): PIPEACONF is 0x80000000
(II) I810(0): PIPEBCONF is 0x80000000
(II) I810(0): Mode bandwidth is 78 Mpixel/s
(WW) I810(0): Extended BIOS function 0x5f28 not supported.
(II) I810(0): xf86UnbindGARTMemory: unbind key 7
(II) I810(0): xf86UnbindGARTMemory: unbind key 8
(II) I810(0): xf86UnbindGARTMemory: unbind key 6
(II) I810(0): xf86UnbindGARTMemory: unbind key 5
(II) I810(0): Rotating Screen to 0 degrees
(II) I810(0): Allocated 8192 kB for the back buffer at 0xc800000.
(II) I810(0): Allocated 8192 kB for the depth buffer at 0xc000000.
(II) I810(0): Allocated 34048 kB for textures at 0x9ec0000
(II) I810(0): 0x81f6618: Memory at offset 0x0c800000, size 8192 kBytes
(II) I810(0): 0x81f6638: Memory at offset 0x0c000000, size 8192 kBytes
(II) I810(0): xf86BindGARTMemory: bind key 5 at 0x0c800000 (pgoffset 51200)
(II) I810(0): xf86BindGARTMemory: bind key 6 at 0x0c000000 (pgoffset 49152)
(II) I810(0): xf86BindGARTMemory: bind key 8 at 0x007bf000 (pgoffset 1983)
(II) I810(0): xf86BindGARTMemory: bind key 7 at 0x09ec0000 (pgoffset 40640)
(II) I810(0): Activating tiled memory for the back buffer.
(II) I810(0): Activating tiled memory for the depth buffer.
(II) I810(0): [drm] init sarea width,height = 1280 x 1024 (pitch 2048)
(II) I810(0): [drm] Mapping front buffer
(II) I810(0): [drm] Front Buffer = 0x2a005000
(II) I810(0): [drm] Back Buffer = 0xdc800000
(II) I810(0): [drm] Depth Buffer = 0x2b800000
(II) I810(0): [drm] textures = 0xd9ec0000
(II) I810(0): [drm] Initialized kernel agp heap manager, 34865152


---

### Post by beermad on 2007-05-28
Not sure if this is relevant to your problem or not, but I have found that with my system, if I boot it and X starts before I power up my monitor, it often starts at low-resolution. As long as I make sure the monitor's up before X I have no problem.

---

### Post by total wormage on 2007-05-28
> **beermad said:**
> Not sure if this is relevant to your problem or not, but I have found that with my system, if I boot it and X starts before I power up my monitor, it often starts at low-resolution. As long as I make sure the monitor's up before X I have no problem.

:D this counts for me too. so i've been browsing launchpad and found that this bug was reported WAY back
look here [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/12301]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/12301")

i don't know anything about programming, but i really do like the idea mentioned over [here]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/12301/comments/11") about xorg choosing the previous resolution when uncertain for at least once

---

### Post by grolm on 2007-05-29
But my monitor is always turned on and I dont change anything but simply reboot several times.

---

### Post by serfcx on 2007-05-31
Just thought I would add my 2 cents.
I have the same random problem using a 19" LCD and Edgy.

---

### Post by Gio-van-I on 2007-05-31
Reminds of one of my current issues.
B.t.w. I have a FX5600...

I just bought a full HD screen and tried to run Ubuntu. The problem is with d-sub I get a ' signal out of range' and with DVI I get a 1280*1024 resolution.
Well that doesn't make any sense at all?!
I've tried all the standard methods to get a 1920*1200 resolution. Nothing worked.

A friend told me to try moving my /etc/X11/xorg.conf file. Did this and wham 1920*1200?! But no new file was formed and to make things worse some graphical effects didn't work (openGL I think).

After a reinstall I got 1600*1200?! Using restricted drivers automatically sets the max resolution to 1280*1024 which persists even after disabling it.

Looking at your description the issues might be related so maybe you can use this information in some way.
I hope there will be some kind of fix for this, it's driving me nuts.

---

### Post by total wormage on 2007-05-31
hm, i only get the low resolution when my monitor is switched off, this is the known problem for which already a bug is reported. so it won't do any good if i file anything

would it be a good idea if you guys with the actual random problem file it as a bug?
maybe under this one or as a new one :]
[https://bugs.launchpad.net/ubuntu/+s...org/+bug/12301]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/12301")

> **Gio-van-I said:**
> Reminds of one of my current issues.

thanks for the reply, that also sounds like a silly event.
i don't know what is supposed to happen if you 'remove' your xorg.conf (going to try it after this reply) but it fixing a problem you had doesn't sound logical. i wonder if the same thing would have happened if you reconfigured xorg.
have you found any other sounds from people with your card reporting the same issues?

---

### Post by gameovr on 2008-06-09
Hell I just noticed this issue tonight on Hardy. I was booting up, noticed my fonts were extremely large, checked my resolutions and noticed only 2 options. I rebooted, and all seemed back to normal.

I am a new user on Ubuntu and have both this and XP on it and have been using this about 80 percent of the time and loving it. Keep up the great work on open source!!

---

