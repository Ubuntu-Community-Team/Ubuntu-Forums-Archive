---
title: "Two issues: Flash players are extremely jerky and Compiz w/ videos is iffy."
date: 2008-05-12
forum: General Help
---

### Post by EvenStevens on 2008-05-12
**Ubuntu 8.04 Hardy**

Firstly: Anything like Youtube or the like that uses flash to embed its videos turns out VERY jerky, almost unwatchable - especially when embedded into an external page.
I can't/don't know if there's a way to change the flash plugin or ...what. Is this even fixable?

Within Firefox 3's preferences, "Shockwave Flash File (application/futuresplash)" has the action "Use Shockwave flash".
"Shockwave Flash File (application/x-shockwave-flash)" has the action "Use Shockwave flash" also.

I can change both of these to use "libflashplayer.so" but it doesn't seem to make a difference.

Note - all flash content appears as a giant grey block with a big "Play" symbol on it (a small arrow).

Secondly: When I use Totem's audio visualiser or play videos and subsequently move the windows around, the videos don't move with it... instead they stay where they are until I've dropped the window down.
Highly annoying.

A similar thing happens when I use the Desktop zoom to zoom in on a video, except the video stays where it is... but like in a black void of nothingness. It's odd to explain, but anyone who's witnessed it will know what I'm on about.

Any help on this at all?

My laptop is a Dell 640m inspiron with Intel's 950GMA graphics chip.

---

### Post by EvenStevens on 2008-05-13
Bumping this.

---

### Post by asrai on 2008-05-13
The play button in firefox means you have a non-adobe flash plugin installed.

To get rid of the play button in firefox flash, type the following into the terminal:

sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport

this is from reassuringly offensive's excellent how-to located here: [http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

There are also some great tutorials there to install alternate media players if you're not happy with totem.  I'm using mplayer/gnome media player and it works very well.

---

### Post by EvenStevens on 2008-05-14
Thankgod.

Thankyou, I appreciate it

---

