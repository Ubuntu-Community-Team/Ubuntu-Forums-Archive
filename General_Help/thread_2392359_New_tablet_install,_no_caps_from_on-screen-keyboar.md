---
title: "New tablet install, no caps from on-screen-keyboard"
date: 2018-05-20
forum: General Help
---

### Post by Schotty on 2018-05-20
As title says, I nuked the God awful Win10 off a new Dell tablet (Latitude 5285) and dropped 18.04 on, but the OSK from GDM/GNOME is wonky.

Even though I press the shift key (on the OSK), no cap letters appear in anything I care about.

* no caps show up in the terminal
* no caps in the wireless password prompt
* YES caps in the GNOME app search (not like I need it here, but, hey cool)
* no OSK in Firefox or Chrome-stable

Any resolutions here?  Sofar my mitigation is the opposite of what I should be doing with a tablet --- using a mouse+keyboard dock :/

Thanks,
Andrew.

EDIT:  KDE OSK is flaty out unusable.  Not handling touch input correctly at all.  Laggy.  Arrggh.

---

### Post by cruzer001 on 2018-05-20
I'm no help with your current problem, but since this is a fresh install I would also look at other options.

Earlier Dell tablets were certified for use with Ubuntu 16.04.  May be a better choice for you.
Also Mate seems to be a good choice for tablets.

Good luck

---

### Post by Schotty on 2018-05-20
> **cruzer001 said:**
> I'm no help with your current problem, but since this is a fresh install I would also look at other options.

Earlier Dell tablets were certified for use with Ubuntu 16.04.  May be a better choice for you.
Also Mate seems to be a good choice for tablets.

Good luck

Thanks for the tips, but I need very new kernels, so a 2 year old release isnt going to go well.  In fact, 4.16 is where I get my hardware support finished off (both webcams).

As for Mate, I thought at first you were on to something.  Might have been.  But it is the worst out of the three.  At least, with as bad KDE is, I could navigate (just no OSK), GNOME the OSK is hit/miss.  Mate its just gone satanic and fights me.  Clicking with my digitizer pen, or finger on the Menu button, I get a pop up nightmare of what looks to me like its trying to change my login picture, it flips too fast to see.

I am gonna sit on this unless someone else has an idea.  I have my keyboard module on its way still along with the rugged case.  Worst case I drop a fresh install of this (18.04 GNOME) or Fedora on it and just not use the touch.  Or even ChromiumOS (Android x86).

---

### Post by risacher on 2018-05-22
Having the same problem - also with a Dell Tablet and also with 18.04.  No caps.  Typing '*' with OSK results in '8' in Terminal.

---

### Post by Schotty on 2018-05-26
I wanted to update people on this -- a recent update did fix things.  I ran apt on the cli to update before I took it to work with me, and when I got there it worked correctly.

This is a Dell 5285 2in1

Quirks:

* The rotation of the screen is .,.. not Android/iOS level of smooth.  The screen blanks, and will only rotate 2 of the 4 possible directions.  One landscape, one portrait position.
* Not sure if its me, but although the digitizer pen was fidgety on Win10, its virtually unusable.  Haven't had time to see if there are any drivers that I would need to use.  The screen registers as a Wacom screen, so that may be a good start.
* Did have abysmal battery prior to using LTP and PowerTop.  Now its about %90 of what Win10 reported.  Alot better than my son's and my Dell 5577's.
* No suspend/hibernate oiptions, although turning the screen off apparently is a suspend,  Would be nice to have a button.  My son who runs Ubuntu on his Dell 5577 has one, not sure if thats from an addon, or since it is still on 17.10.

Note, I am a RHEL fanboy, so if these are things that either RH patched in, or Canonical left out for whatever reason, not sure, too much a Ubuntu moron to know offhand.  Plus alot has changed since GNOME 3.22, so it very well might be that.  These are just my observations.

I think my recommendation of Dell based purely on what I could see and what the sales folks are saying is panning out to be true -- Dell stated that all devices regardless if they offer Linux, will run it, by design.  This is good.  I've alrteady sent a message to thank them for their support.  So us Americans have two viable options, Dell & System76.

---

