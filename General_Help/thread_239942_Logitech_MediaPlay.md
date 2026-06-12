---
title: "Logitech MediaPlay"
date: 2006-08-20
forum: General Help
---

### Post by isez2001 on 2006-08-20
I've found what may be a solution to the world's Logitech MediaPlay woes.  I've already posted in the Gentoo forums (as I'm currently running Gentoo), but I always see links pointing here from there, so I thought I'd give the great community here a chance to comment on this too.

First, the link to the Gentoo thread:  [http://forums.gentoo.org/viewtopic-t-490456-highlight-.html](http://forums.gentoo.org/viewtopic-t-490456-highlight-.html)

Basically, I've found that by configuring my MediaPlay with evdev and "SendCoreEvents," all the keys become available to X.  The mouse buttons appear to work as normal mouse buttons, and the media keys become keystrokes.

It seems to me that with a fairly simple (for someone more knowledgeable than myself) remapping of keys, we could be using fully-functional MediaPlays without any really nasty hacks.

My X config and startup log are in the Gentoo thread (I hope it's not that's not a problem... I could post them here too, if need be).  I'd really like some help with this, it would make a lot of MediaPlay owners very happy, I think.

---

### Post by isez2001 on 2006-09-03
It turns out things will be getting even simpler in the near future.

I am currently running Xorg 7.1 (evdev 1.1.2) on Arch Linux, and all of the buttons are recognized with no special tricks--just a Udev rule to set my mouse at /dev/input/event9, and an xorg.conf to set event9 as the CorePointer.

Now, all that should need to be done is map the keys properly, and assign the extra ones functions.

---

