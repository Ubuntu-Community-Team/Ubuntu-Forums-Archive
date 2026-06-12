---
title: "ATI driver on Sony Vaio PCG-K17"
date: 2006-07-10
forum: General Help
---

### Post by caish5 on 2006-07-10
Hi people,

I'm curious to know if anybody has got the proprietary ATI graphics driver to   work on this laptop, or perhaps a similar sony.

So far i've followed the guides on here and got no further than the Fatal Error - No Screens Found part.

Any help at all is appreciated.

Thanks
Andy

---

### Post by abstrakt on 2007-02-10
Hi, I'm sorry to dig up a very old post, but I was searching for Vaio topics and came across this one.

Under edgy, with my vaio vgn-a690 (with an ati x600), the built-in mesa 3d drivers worked fairly well, and the ubuntu repo drivers (I think version 8.28.8) worked well too. The most recent drivers from ATI (which as of this posting are around version 8.33.x) did not work very well.  I can still see my desktop in 1920x1200 res, but I get no 3d acceleration at all.

I think the problem is similar to something I see happen in Windows XP - if I use the latest ATI drivers, my system has a heart attack.  For some reason, I need to use Sony proprietary drivers for my video card.  If I had to guess it's not a standard ATI design, and that might be causing our Linux headaches.

---

### Post by blueglow on 2007-02-10
Hey abstrakt,

I too just had a problem installing this ATI driver. And just today my my fglrx (ATI fast) driver died after the kernel update and I was left with the Mesa one, which is indeed slow.

I recommend the package and instructions on this page - fixed my Vaio a397xp with ATI X600 card:
**[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")**

Don't worry about it mentioning only nVidia, it does work on ATI... I would download and install it, log out, press ctl-alt-F1 to bin X then log in and type...
```
sudo envy
```
...then choose "Uninstall ATI driver".

[You may want to reboot after this stage completes to be uber-sure (I did but then I'm paranoid) and when ubuntu comes back up do the above again (after the download/install bit), then run envy again]

Now choose "Install ATI driver", wait... it'll download the latest from ATI (8.33.6) and install it. I agreed to let it edit my xorg.conf (actually I reverted it back to an original first anyway to ensure I had default graphics) and rebooted when it asked.

Worked like a dream on toast for me, loads better than the dozen or so HowTos i've seen until this one. Good luck!

Jim

---

### Post by blueglow on 2007-02-10
Also, assuming install/config went ok can you post the output of fglrxinfo?

---

### Post by abstrakt on 2007-02-11
Thanks for the reply,

I do know about the envy script, I actually just discovered it this morning :)  It worked perfectly on my desktop machine with a not-so-great geforce fx5200.  However when I tried to remove/reinstall the ati driver for my vaio x600 chip, it caused a huge number of problems.  At this point I think my OS may just be corrupted due to way too much fiddling around (with xgl/aiglx/compiz/beryl/various drivers), so the old nuke-and-pave gets my vote.

After I reload Egdy I'll skip straight to the envy installer rather than mucking around with the tutorials.  I'll be sure to post how it went.

---

### Post by abstrakt on 2007-02-12
Ok - Here's what I have done:

Fresh load of Ubuntu 6.10
Restricted repos enabled in synaptic
I did do ```
apt-get update
```
I did NOT ```
apt-get upgrade/dist-upgrade
```

I used envy from a pure terminal environment
I told it to install the ATI drivers

Here's my fglrxinfo output:
```
eric@Mouse-Ubuntu:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X600 Generic
OpenGL version string: 2.0.6286 (8.33.6)

```

The logical conclusion would be that everything is working fine now.  That's wrong.  I get NO graphical acceleration with these drivers - 2d or 3d.  Any time I move a window, open a program, or view an image, my draw rate slows to a stumbling, drunken stagger.

I actually get better performance with the Mesa 3d package.

<shrug>

I think this laptop is just cursed.

I was able to get to this point before, without using the envy installer, just by following the ATI tutorials.  I don't seem to be having trouble getting the driver installed, it's just that the driver doesn't seem to work in my computer.

Such is life... I'll be attempting an uninstall with envy here in a few minutes.

---

### Post by blueglow on 2007-02-12
That's a pain in the A, mate. If it's slower than Mesa, it must be hell!

Are you using any additional kernel parameters that could be interfering with the driver? 

If you run this you may see some error messages in driver initialisation?:
```
cat /var/log/Xorg.0.log | grep "(EE)"
```

This is outside my knowledge now really, but you could try some other settings in your **/etc/X11/xorg.conf** you'll have to Google these though as I've already forgotten the few I knew.

I guess you'll have to go back to the older 8.28 driver if that's working better - maybe send ATI an email?

---

### Post by abstrakt on 2007-02-12
Interesting that you mention the log file, take a look at this:

```
eric@Mouse-Ubuntu:~$ cat /var/log/Xorg.0.log | grep "(EE)"
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(EE) AIGLX error: dlsym for __driCreateNewScreen_20050727 failed (/usr/lib/dri/fglrx_dri.so: undefined symbol: __driCreateNewScreen_20050727)
**(EE) AIGLX: reverting to software rendering**
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom
(EE) xf86OpenSerial: Cannot open device /dev/wacom

```

The item in bold would certainly explain my problem, but the item above it makes no sense to me.
I'm also not sure what device "wacom" refers to.

---

### Post by abstrakt on 2007-02-12
I have some good news and bad news,

I discovered the cause of the software rendering error was AIGLX, so I added the following code into my xorg.conf file:

```
Section "ServerFlags"
	Option	"AIGLX" "off"
EndSection
```

The good news is that the error message is now gone when I look at the log file.

The bad news is I still have no 3d acceleration.

---

