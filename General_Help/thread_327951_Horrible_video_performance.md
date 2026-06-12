---
title: "Horrible video performance"
date: 2006-12-30
forum: General Help
---

### Post by stembot on 2006-12-30
I've been using Debian for a couple years and tried installing Ubuntu 6.10.

The video display is horrible.  The screen gets warbled and choppy anytime anything happens.  I can view it great when nothing's going on.  Running the glxgears is an abolute mess.

I read some items in [http://www.ubuntuforums.org/showthread.php?t=221672](http://www.ubuntuforums.org/showthread.php?t=221672) as that's the video card I use (ATI Radeon RV100 QY [Radeon 7000/VE]).

Apparently the driver for my card is built-in?  What can I do to get this working?

---

### Post by pay on 2006-12-30
Try looking here [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by stembot on 2006-12-30
That page looks pretty helpful, but I can't get past the "Ubuntu Edgy (6.10) installation with AIGLX" section.

When I do "glxinfo | grep vendor" I get 

libGL warning:  3D driver claims to not support visual 0x4b
server glx vendor string:  SGI
client glx vendor string: SGI
OpenGL vendor string: Tungsten Graphics, Inc.

I understand this isn't what I want to see, I need to be seeing ATI somewhere here, but I've done the steps below:

sudo apt-get remove xorg-driver-fglrx; sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri

And all it says to me is that xorg-driver-fglrx is not there, and the other two are already up-to-date.

I made a few alterations to my xorg.conf file as notated in the remainder of the doc, but I think my problem stems from the SGI vendor strings showing in my glxinfo.

What now?

---

### Post by stembot on 2006-12-30
I changed the refresh rate from 85 Hz to 60 Hz and it's great now.

How can I get glxgears to output my FPS?

I type glxgears and I get the libGL warning again:

3D driver claims to not support visual 0x4b

I understand this isn't a critical error, but I'd be interested in seeing my FPS rates and can't figure out how.

---

### Post by WalmartSniperLX on 2006-12-30
> **stembot said:**
> I changed the refresh rate from 85 Hz to 60 Hz and it's great now.

How can I get glxgears to output my FPS?

I type glxgears and I get the libGL warning again:

3D driver claims to not support visual 0x4b

I understand this isn't a critical error, but I'd be interested in seeing my FPS rates and can't figure out how.

I get the same thing with my laptop using the OpenSource ati driver. To see the fps rates use ```
glxgears -printfps
```

---

