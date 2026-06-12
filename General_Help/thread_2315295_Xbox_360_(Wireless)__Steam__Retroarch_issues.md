---
title: "Xbox 360 (Wireless) / Steam / Retroarch issues"
date: 2016-02-27
forum: General Help
---

### Post by chamerjr on 2016-02-27
*Disclaimer* I am an advanced computer user who has only dabbled in Linux.

I recently decided to leave Windows and I'm struggling not to return.  I'm currently running the latest version of Ubuntu 15 (Unity desktop environment).  I have followed every guide out there for getting a 360 controller to work.  First, I installed Steam.  Worked fine.  Then I compiled Retroarch 1.3 from scratch and installed that.  No controller recognized.  Ok.....google away.....I find xboxdrv, ubuntu-xboxdrv, and qjoy.  First, I tried ubuntu-xboxdrv.  Ran it, calibrated controller, saved a profile.  Ran Retroarch.  No controller.  Clearly, like I said, I'm a noob so I F...ED something up.  Uninstall.  Read some more.  Ok....ubuntu-xboxdrv isn't officially supported.  Maybe there's a bug.  I installed xboxdrv.  Every single setup guide followed, including disabling xpad (completely forgetting that Steam uses xpad), then I get this "LIBUSB_ERROR_ACCESS".  Again....my F up.  Google....follow all instructions....got rid of the error.  Not registering any keypresses in terminal even though not in silent.  I tried it in Retroarch.....recognized, but not configured.  Ok....lets configure a controller.  I move over using the keyboard.....no keys register....I escaped through it.   Now NO KEYS WORK.  GFD!  Ok....I did this once on windows.  Find the retroarch.cfg and delete.  Wait, I can't....need permissions....fine.  chmod some permissions in.  Delete the file.  Restart Retroarch.....no keys work still.  I finally said "F this."  I clicked Steam and figured I'd just play a game that I could get on Steam.  ........AAANNNNNNDDD......controller doesn't work.

Any help would be appreciated.

Here's a bit of advice from someone working in marketing.... 
So far, my only successes have been getting hdmi audio to work, installing kodi, and compiling retroarch.  I'm not claiming to be the smartest user out there.  Far from it.....but I cannot help but think of early versions of windows (3.1 and 95).  Linux has gotten prettier and far more functional.  But the basic, download a package, install it, and have it work, AND have native hardware support work is missing from every version of Linux.  In the last 3 days, I've run 4 different distros.  Each one is as difficult to find resources that work (keyword there) as the next.  The whole thing that inspired me to completely leave windows was following the Scale14 event on youtube, engadget, etc.  I have to agree with the "Linux Sucks" portion.  It's not that Linux is terrible.  It's not.  But it is plagued by something I've noticed happens with a lot of open-source software....fragmentation.  I've literally spent about 16 hours in the past two days just searching for resources to troubleshoot getting these things to work.  Users want things that "just work".  I have run Linux for no more than a few months every year as a secondary driver.....either my goof off laptop, or slapping it on a tablet or phone for fun.  If the majority of distros worked together, there would be a larger user base, which will in turn open up the floodgates for more advanced users, as well as developers.  Imagine no more work arounds to get Netflix to work on Linux.

---

### Post by blueridgedog on 2016-02-28
Just for clarity...are you using the wireless adaptor or the USB cabled version?

Some general advice...stick with one controller connection method and use their support channels, such as the forums for xboxdrv.

As to the general state of affairs with Linux and hardware, or package installation, yes it is difficult.  Linux is not centrally managed and you can have various library versions, locations, kernel versions etc etc.  You can install most current distros and get out of the box networking and sound and have a fully functioning office suite, email and web, but you will get into deep water with more esoteric hardware.  This is also a problem when you think about binary software distribution.  The variety in the Linux landscape makes that challenging. 

I was in your shoes in '94 and things have improved a small bit, but what has changed is my perspective that a community/volunteer driven OS will always have some very rough edges and that things that should be simple can be very hard (and oddly things that should be hard can at times be easy - like installing a LAMP server).  I have constantly said that Linux makes difficult things easy at the expense of making some easy things difficult.

---

### Post by chamerjr on 2016-02-29
Thanks for your advice.  I think the biggest hurdle they have made for noobs is the GUI install.  I remember my first attempt at installing Linux, probably Gnome, circa '98.  I gave up until an older (I was 16 and kinda dumb), nerdier friend helped me out.  I could play any of my games on it so I ditched it.  For now, I've relegated my 3 of my windtop computers and my Pi2 to play with it, rather than my main PC.    I'll search the xboxdrv forums, though I've been reading xpad (what steam uses) and xboxdrv don't play nice together.  Thank you again.

---

