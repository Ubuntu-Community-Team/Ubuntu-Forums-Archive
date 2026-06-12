---
title: "Xsession: unable to start X session :("
date: 2008-02-14
forum: General Help
---

### Post by este on 2008-02-14
Crap. I screwed something up. Here is what I've been doing, probably related, but not sure. I'll just post everything I've done and maybe something will be relevant.


I've been in an engaging battle to get my hardware setup. 

First issues with the ATI 2900 driver, got that working other then what appears to me to be sync issues and a slow repaint on moving windows). Then I had issues getting my Dell 2007WFP to go to 1680x1050 1:1 widescreen, editted the xorg and got the right values. 

Next, I had to get my mouse buttons working, I installed IMWheel got that going but it wouldn't trigger forward and backward for Dolphin. So I removed IMWheel (removed the 57XModMap file or whatever it was - this may have been a problem, but I left the .save file) then installed BTNX. Mouse works, move on.

Now, I've been having trouble getting my Bluegears b_Enspirer (CMI-8788)  to work. The card the kubuntu detected by default was my 2900XT's HDMI audio controller which I don't want to use. Ok, I do a little research and find that I need Alsa 1.0.16 to support my card. Adept thinks that 1.0.14 is the latest release so I go to alsa and get the 1.0.16 driver (note: JUST the driver). Odd thing is that now the system sounds work fine. But when something asks alsa to play a sound (aplay, vlc, mplayer, kaffine, amorak) they all report "Audio Unavailable - Device is Busy (!)". 

So... I go into adapt and remove all Alsa packages that have the version 1.0.14, there were probably 6 or so. Then reboot.


Now, instead of the login screen, I go right into terminal and upon trying 'startx' I get a basic window telling me **"Xsession: unable to start X session --- no "/home/user/.xsession" file, no "/home/user/.Xsession" file, no session managers, no window managers, and no terminal emulators found; aborting."**. I'm forced to hit 'Okay' and return to terminal.

I found some other people with a similar problem and saw that it might help to post my ~/xsession-errors file.

> [B]Xsession: X session started for user at Thu Feb 14 12:07:03 MST 2008

/etc/X11/Xsession.d/40guidance-displayconfig_restore: 11: /usr/bin/displayconfig-restore: not found

Xsession: unable to start X session --- no "/home/user/.xsession" file, no "/home/user/.Xsession" file, no session managers, no window managers, and no terminal emulators found; aborting.

Warning: Cannot convert string "vlines2" to type Pixmap [/B]


I have no idea whats going on. I used the recovery cd to go and get all the 1.0.16 packages (tools, utils, lib, etc) and extract them, booted back to my broken session and installed them all. No change. The only other thing that I could think of is that I did add the 57xmodmap (sic) file wass right next to the 40guidance-displayconfig_restore file that seems to be having a problem now.

I know thats all long winded but I'm new and have no idea what I'm doing :)  Any help ?
Thanks

---

### Post by este on 2008-02-14
Hmpf..... 

I tried restoring a known working xorg.conf thinking it was something with the screen.

Not it.

I'm running out of options here ::confused:

---

### Post by UK-Wobbie on 2008-02-14
> **este said:**
> Hmpf..... 

I tried restoring a known working xorg.conf thinking it was something with the screen.

Not it.

I'm running out of options here ::confused:

Sounds a bit F**KED to me :lolflag:
Have you got any work on it? You may need to backup all your work and start over!
As i say you deleted your x server, So you can not login or do anything.

Boot up the live CD and go into the Ubuntu desktop on it, 
Go to Places -> Computer ->Filesystem -> Home
You will see your user name! 
Back up ever thing from there and reinstall Ubuntu.

---

### Post by xeth_delta on 2008-02-14
Could you please post the output of:
```
cat /var/log/Xorg.0.log | grep -i EE
```

---

### Post by TheCowGod on 2008-02-14
Try logging in as a different user. I seem to remember something like that happening when I accidentially deleted my entire home directory. If I remember right I logged in as root, X worked then, I deleted my user from the user CP and added it again making sure to use the same UID.

---

### Post by este on 2008-02-14
Ok, here is the output from /var/log/Xorg.0.log

	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(**) |-->Screen "Default Screen" (0)
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
(II) Loading font FreeType
(II) Loading extension XFree86-DRI
(II) Setting vga for screen 0.
(II) fglrx(0): Year: 2006  Week: 33
(II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
(II) fglrx(0): 	21100103802b1b78eeee91a3544c9926
(II) fglrx(0): Year: 2007  Week: 0
(II) fglrx(0): redX: 0.652 redY: 0.331   greenX: 0.277 greenY: 0.597
(II) fglrx(0): [pcie] 258048 kB allocated with handle 0xdeadbeef
(II) do I need RAC?  No, I don't.
(II) fglrx(0): driver needs X.org 7.1.x.y with x.y >= 0.0
(II) fglrx(0): doing DRIScreenInit
(II) fglrx(0): [drm] mapped SAREA 0x2000 to 0x2b41d1ee2000
(II) fglrx(0): DRIScreenInit done
(II) fglrx(0): Largest offscreen area available: 1728 x 1378
(II) fglrx(0): Using XFree86 Acceleration Architecture (XAA)
	Screen to screen bit blits
	Driver provided ScreenToScreenBitBlt replacement
[atiddx] ASYNCIO init succeed!
(II) Initializing built-in extension XFree86-Bigfont
(II) GLX: Initialized MESA-PROXY GL provider for screen 0
(II) Configured Mouse: ps2EnableDataReporting: succeeded
(II) fglrx(0): [drm] unmapping 8192 bytes of SAREA 0x2000 at 0x2b41d1ee2000
FreeFontPath: FPE "/usr/share/fonts/X11/misc" refcount is 2, should be 1; fixing.

That font does come up after I return to terminal, but I forgot to mention it.

I tried logging in as root - no go, same error.

I'm pretty sure I'm not ******. It seems like there is an obvious problem somewhere, I just haven't found it yet. I'm going to log back in and see what else I can find,

Thanks for the help!

---

### Post by este on 2008-02-15
Meh,

Maybe I'm ******. 

I installed 'kdm' and it when I started it told me my previous session is now invalid. I should choose the default. I did so and it went back to the same error as before. 

I didn't really have anything installed except drivers so I'll probably just wipe it and try again.... Kind of lame though.  

Linux for humans my *** :)

---

### Post by jocko on 2008-02-15
Maybe when you uninstalled ALSA, you automatically uninstalled all other dependencies for kubuntu-desktop (I think aptitude would do that, not sure about adept)?
Try this:
```
sudo apt-get install kubuntu-desktop
```

---

### Post by este on 2008-02-15
Nope

Just tried it, same error..... Im not so much pisses abput having to start over right now but what if i had been running and set up for weeks. Kinda sucks it can just STOP lole that.  

It was worth a shot,

---

