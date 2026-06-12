---
title: "1080 resolution on HDTV with nvidia drivers"
date: 2007-10-23
forum: General Help
---

### Post by GnarusLeo on 2007-10-23
I have a Nvidia GeForce 8400m GS card, and a 32" HDTV LCD TV connected through DVI. nvidia-settings won't let me set the resolution on the TV higher then 1280x720 .... 

I have manually tried to change this in xorg.conf, but it just seems the tv signal is "lost" ... I am _NOT_ sure how to set this properly though ...

any ideas? adding that I am trying to use twinview, and I have the 100.14.23 (latest) beta driver.

Any help would be appriciated!

EDIT: I am of course trying to set the resolution on the TV to 1920x1080 (Vista lets me set this resolution ...)

---

### Post by UK-Wobbie on 2007-10-23
> **GnarusLeo said:**
> I have a Nvidia GeForce 8400m GS card, and a 32" HDTV LCD TV connected through DVI. nvidia-settings won't let me set the resolution on the TV higher then 1280x720 .... 

I have manually tried to change this in xorg.conf, but it just seems the tv signal is "lost" ... I am _NOT_ sure how to set this properly though ...

any ideas? adding that I am trying to use twinview, and I have the 100.14.23 (latest) beta driver.

Any help would be appriciated!

EDIT: I am of course trying to set the resolution on the TV to 1920x1080 (Vista lets me set this resolution ...)

Hey have you had a go using the Nvidia settings?
Go in to Terminal!

And put his in "nvidia-settings" To get the Nvidia setup window.

What Nvidia plugins are you using? "nvidia-glx" or "nvidia-glx-new"....

"nvidia-glx-new" Is more better on screen resolution.. When you instill the plugins!
Reboot the pc and at the login window hit!
 "CTRL+ALT+BACKSPACE" To restart the X-Server..Then log back in and your done. :)

---

### Post by GnarusLeo on 2007-10-23
Hi, and thanks for fast reply!

It is in "nvidia-settings" I cannot change my HDTV's resolution more than 720, though I want 1080 ... I dont know which nvidia-plugins Im using, because I simply don't know what you mean by that :) in xorg.conf, I am using "nvidia" as driver ...

---

### Post by UK-Wobbie on 2007-10-23
> **GnarusLeo said:**
> Hi, and thanks for fast reply!

It is in "nvidia-settings" I cannot change my HDTV's resolution more than 720, though I want 1080 ... I dont know which nvidia-plugins Im using, because I simply don't know what you mean by that :) in xorg.conf, I am using "nvidia" as driver ...

On your Nvidia card you will be using one of the plugins "nvidia-glx" or "nvidia-glx-new"
You can see this by going to "Synaptic Package Manager" and put in Nvidia..
Instill the new plugins as when instilling Ubuntu it will instill the old ones and the screen resolution will be tiny in the screen resolution tool... So this new plugin may help you! :)

---

### Post by UK-Wobbie on 2007-10-23
I have got a 19" HDTV LCD TV and i got my computer plugged up to it!
Am using the new Nvidia plugins/drivers :lolflag:

The size on the TV is 1028X768.. it's a nice size on my TV...  I can make it bigger but i do not wanna because of my computer monitor... I got the settings so it will copy my desktop from my monitor on to my TV. :mrgreen:

What size have you got your settings at? :)

---

### Post by GnarusLeo on 2007-10-23
Thanks again .. I went installing the nvidia-glx-new drivers, (though the 10.14.23 version is newer), and still no change .. :S "nvidia-settings" simply won't let me set a higher resolution .... My 32" HDTV is not recognized by EDID, so maybe it thinks its not capibable of recieving that high resolution ... who knows ...

---

### Post by UK-Wobbie on 2007-10-23
> **GnarusLeo said:**
> Thanks again .. I went installing the nvidia-glx-new drivers, (though the 10.14.23 version is newer), and still no change .. :S "nvidia-settings" simply won't let me set a higher resolution .... My 32" HDTV is not recognized by EDID, so maybe it thinks its not capibable of recieving that high resolution ... who knows ...

who knows :confused: lol

Am sorry that i can not help you with your problem and i hope that you will get it all working like how you like it one day! :-)

---

