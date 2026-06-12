---
title: "Restricted driver manager not working, screen size won't go above 800x600"
date: 2008-04-29
forum: General Help
---

### Post by JamesBowen on 2008-04-29
After making the switch from 7.10 to 8.04, the first thing I notice is a pretty serious nerfing of the "Just Works" motto of Ubuntu. That is, my desktop screen size has defaulted to 640x480, and refuses to go any higher than 800x600.

Now, mind you, I'm using an ATI card (x1600 pro), and for some reason it felt like disabling the restricted driver during the upgrade process, so I figured I'd just click on the restricted driver manager button, and...oh.

Where'd that button go, again?  Huh.  No big deal, I figure -- I'll go into the administrative tab and fool around a bit.  Hardware drivers, meh, sounds about right.  Oh!  Here it is!  Just like before, but with a new name and not as easy to find, and lacking in the nice tab that automatically pops up and tells me proprietary drivers are available!

Okay.  I'm willing to live with this.

However, upon restarting my system, I discover two things: first of all, it has a heck of a weird startup path.  Instead of what I'm used to seeing, the ubuntu load screen spitting out a bunch of information on what's booting up, and then directing me to a login page, it randomly sits at a command prompt with login@<computername>, occasionally flashing on and off.  When I get ready to log in and see if I can figure out what's up, hey, it flashes back to the normal login screen.  At a resolution that is still nerfed, but at least it isn't totally broken.

I figure, hey, maybe now that I'm using the restricted driver, I can give my resolution a boost.

Nope.  I go into the Screen Resolution widget, and lo and behold, it is still only displaying 640x480 and 800x600.

Before I was fine, if a tiny bit disappointed.  Now I'm annoyed.

Seriously, what exactly happened between Gutsy and Hardy that created a problem like this?  Wasn't Hardy supposed to be a bug fix release, setting us up for the next support cycle?  Why is it that the interface, usability, and ease of hardware support -decreased-?  I felt similarly about the transition from Feisty to Gutsy, but at least that only created problems when you tried to -do- things, like run dual monitors on an ATI card or some such.

Anyway.  Any help denerfing my screen resolution would be helpful.  Some reassurances that these bugs are going actually going to be fixed before the next release would prevent me from telling all of my friends who are on the tipping point for trying Ubuntu that they should just stick with Windows.

---

### Post by TwiceOver on 2008-04-29
Don't think I can help, but with the ATI card in my laptop I had to do an apt-get update before it would pick up the correct restricted driver.  After that my resolution was perfect and the driver was working fine.

Before the update it was showing as an ATI Fire GL...  Which is not the card in this laptop.

---

### Post by sailor2001 on 2008-04-29
I believe you could set your resolution for ati at /usr/applications/screen & graffics

---

### Post by JamesBowen on 2008-04-29
No luck on either of those.

apt-get update, while a great thing to do, didn't change its recognition of my graphics card -- of course, it recognized it for what it is, anyway.

Actually, there's no 'usr/applications/' path, nor is there anything under my 'applications' tab which has something related to the screen resolution or graphics in any way.  The program which changes resolution, 'Screen Resolutions' under the systems->preferences gui path  does allow me to change resolutions...between 800x600 and 640x480.

If I had to guess, the options in xorg probably aren't being updated, or that those options aren't being recognized by the Screen Resolution program.

If that's the case, I'm rather unimpressed.  I recall reading that hardy was supposed to "make editing xorg.conf manually obsolete".  If I can't even get a decent resolution without playing with xorg, then hardy seems to be a regression rather than an upgrade.

---

