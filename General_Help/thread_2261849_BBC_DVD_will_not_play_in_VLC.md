---
title: "BBC DVD will not play in VLC"
date: 2015-01-21
forum: General Help
---

### Post by CaptainMikeRak on 2015-01-21
I've been having some issues trying to get a BBC DVD to play in VLC for a bit of time now (specific DVD: "Doctor Who: Resurrection of the Daleks" which is a region 2+4 DVD and before you ask it's a legal copy made by the BBC [I never pirate]). I like VLC since it's multi-regional so that doesn't appear to be the problem. It doesn't work in Windows 7 (using VLC) either, but I do most of my work in Ubuntu so it would be nice if I could play this (and other DVDs) in Ubuntu.

Basically, when I start up the DVD in VLC, it doesn't display anything other than the VLC logo. I cannot jump to any chapters, the menu, or anything else. No error messages appear, and the buttons are locked.

Note, I already tried this fix:
```
[COLOR=#333333][FONT=UbuntuRegular]Tools > Preferences > Show settings: ALL Input codecs > Access modules > DVD with menus Uncheck the option "Start directly in menu". Save the preferences, close and restart VLC.[/FONT][/COLOR]
```
All this did was make it so I could see the copyright notice screen followed by the BBC logo screen (a 21 second portion before the menu). I tried jumping to other chapters and it did nothing, so I reverted the changes.

Also, works in Windows Media Player if I set the region to 2.

---

### Post by CaptainMikeRak on 2015-01-21
Oh, before anyone asks this (I forgot to mention). It *is* recognized by Ubuntu as a DVD and it *is* using the right mounting point in VLC.

---

### Post by raptir on 2015-01-21
Did you install libdvdcss2?

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

DVD playback on Linux is a legal gray area because of the CSS DRM that is used on DVDs. Keep in mind that depending on where you live the use of libdvdcss2 may be illegal, and that is why it is not installed even along with the ubuntu-restricted-extras (you need to run the script after installing the package).

If it is illegal in your country, Fluendo OnePlayer is a legal way to play DVDs in the US:

[http://www.fluendo.com/oneplay/oneplay-dvd-player/](http://www.fluendo.com/oneplay/oneplay-dvd-player/)

But, it's not free.

---

### Post by CaptainMikeRak on 2015-01-21
Thanks! It worked! I looked up the issue, has something to do with the DMCA from 1998. In fairness, it seems that stupid law is contradictory to developing any sort of open source software since it would need these types of libraries in order for an OS to function with anything not specifically designed to run with it. Also, wouldn't that make it illegal to even ethically hack (as in legally hacking for defensive purposes). Well, guess this is an issue for another thread. Thanks for the help!

---

