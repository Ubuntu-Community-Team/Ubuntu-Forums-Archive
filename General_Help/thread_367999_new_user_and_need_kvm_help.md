---
title: "new user and need kvm help"
date: 2007-02-22
forum: General Help
---

### Post by uglytruckling on 2007-02-22
I'm a new ubuntu user and am slowly feeling my way around the linux world (definatley a novice!!!).

I just installed ubuntu 6.10 onto one of my Dell Latitude D810 laptops.  My problem involves using it with my KVM switch for my desktop monitor (an ImageQuest L70S).

I usse a Port Authority2 four port USB KVM Switch ([http://www.cablestogo.com/product.asp?cat%5fid=3411&sku=35555](http://www.cablestogo.com/product.asp?cat%5fid=3411&sku=35555)) to access my 3 laptops and desktop computer. Two of the laptops are identical Dell Latitude D810's. 

When I attempt to push the video from the laptop screen to the monitor ( FN + F8) I get part of the screen showing on the monitor. I've changed resolutions on the laptop to no avail. On the desktop monitor, I can see the bottom right 3/4's of the screen. I can't see the status bar at the top at all.

The resolution on the desktop monitor is 1280x1024, and on the laptop the max resolution is 1680x1050.

The windows laptop squeezes the display down to fit it all onto the desktop monitor (while maintaining the correct display on the laptop screen).

Is there a way for ubuntu to do this?

---

### Post by allwin on 2007-02-22
> **uglytruckling said:**
> I'm a new ubuntu user and am slowly feeling my way around the linux world (definatley a novice!!!).

I just installed ubuntu 6.10 onto one of my Dell Latitude D810 laptops.  My problem involves using it with my KVM switch for my desktop monitor (an ImageQuest L70S).

I usse a Port Authority2 four port USB KVM Switch ([http://www.cablestogo.com/product.asp?cat%5fid=3411&sku=35555](http://www.cablestogo.com/product.asp?cat%5fid=3411&sku=35555)) to access my 3 laptops and desktop computer. Two of the laptops are identical Dell Latitude D810's. 

When I attempt to push the video from the laptop screen to the monitor ( FN + F8) I get part of the screen showing on the monitor. I've changed resolutions on the laptop to no avail. On the desktop monitor, I can see the bottom right 3/4's of the screen. I can't see the status bar at the top at all.

The resolution on the desktop monitor is 1280x1024, and on the laptop the max resolution is 1680x1050.

The windows laptop squeezes the display down to fit it all onto the desktop monitor (while maintaining the correct display on the laptop screen).

Is there a way for ubuntu to do this?

1.  See if you can find, online, some doc or man pages for the EXACT video driver you are using.  For example, I found mine on the nVidia website, and another system, with ATI, I was able to find man pages on the ATI open source driver.  

2.  Look for something about "EDID".  You want to sprinkle lines of code into your /etc/X11/xorg.conf which "ignore" EDID.  If your driver permits, you may also be able to specify the correct DPI.  For nvidia, you add Option "UseEdidDpi" "false" and Option "DPI" "96x96".

I can't help if you are using Intel graphics, and the examples I cite work only with the 9631 version of the nVidia driver (proprietary one).

Edid stands for something like extended device identification data, and it's a message sent to Linux from the display circuit which is supposed to enumerate the available screen formats and resolutions.  I have a similar KVM here, and apparently, it messes up this data.  So you need to tell X not to use it, but to use your fixed settings.

This will take you a couple of edits and is just a little frustrating to get it to work right if you are having the same problem I had, which was ENORMOUS LETTERS (like 8 letters filling up a whole screen width) on LOGIN.

Heh, once you get this figured out...don't lose the magic mojo commands!  You will need them even if you try other Linux distros.  I have encountered several which screw up similarly.

I often wonder why, when X first comes up, it just doesn't ask you HEY DO I LOOK GOOD? and if you say NO offer you some alternatives...you know, like real human software should!  Trying to deduce all this from hardware is IMHO totally dicey and works only about 5% of the time.  Please, let ME tell YOU, Mr. X, how I want my type to appear!

---

