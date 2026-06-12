---
title: "Sound not working - Asus VX2"
date: 2008-03-15
forum: General Help
---

### Post by keithpitt on 2008-03-15
Gday all,

First off, please be gentle, im new to the whole Linux thing :)

Anyways, I've been able to get my system up and running fairly easy, but I'm having some issues with my sound. The ubuntu laptop testing pages say that my laptop sound should work fine, but all I'm getting is a crackling, Im guessing maybe its a driver issue.

When I do a lspci I get this:

```
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
```

Any help would be greatly appreciated :)

Keith

---

### Post by keithpitt on 2008-03-15
Sorry, forgot to mention im running 7,10

Keith

---

### Post by BandD on 2008-03-15
I have a the intel ICH6 card and had some issues with sound too.  There are some issues with the Intel HDA cards with the ALSA driver that ships with Gutsy.  Some people seem to get it working by upgrading to more current versions of the driver.  While others (myself included) seem to get it working by tweaking the default version.

I found this page to be very helpful:


[https://help.ubuntu.com/community/HdaIntelSoundHow to]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

as well as this thread:

[http://ohioloco.ubuntuforums.org/sho...d.php?t=530374]("http://ohioloco.ubuntuforums.org/showthread.php?t=530374")

Good luck my friend!

---

### Post by keithpitt on 2008-03-15
Zing! Got it! After hours...and hours...and hours....I've finally got it. One option was causing it..."i think". "External Aplifier" was checked in my sound settings. I had tried testing it before, but there is a 5 second delay after checking it that it takes effect. I hope this helps someone else!

Yay, now I can move to ubuntu full time....now if only Photoshop worked well...

Thanks!

Keith

---

