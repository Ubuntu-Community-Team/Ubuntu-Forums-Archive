---
title: "Amarok 1.4.5 wants to update to 1.4.4 help!"
date: 2007-02-05
forum: General Help
---

### Post by darweth on 2007-02-05
I eventually did compile and build Amarok 1.4.5!  It works beautifully with all my devices, woo!!!  And it was a checkinstall so I can get rid of it easily!!!  But I don't want to get rid of it THAT easily.  Upon installing, I got an Ubuntu update notification to go from 1.4.5 to 1.4.4!!!  I ignored it of course but the orange notification button stays in my systray and I am afraid I might someday install it by accident.  How do I blacklist that evil thing?!?!?

---

### Post by comfurtn on 2007-02-05
> **darweth said:**
> I eventually did compile and build Amarok 1.4.5!  It works beautifully with all my devices, woo!!!  And it was a checkinstall so I can get rid of it easily!!!  But I don't want to get rid of it THAT easily.  Upon installing, I got an Ubuntu update notification to go from 1.4.5 to 1.4.4!!!  I ignored it of course but the orange notification button stays in my systray and I am afraid I might someday install it by accident.  How do I blacklist that evil thing?!?!?

I have to deal with the same thing on my box... I believe that you can "lock" a package version using synaptic... find the package, select it, then go to the package menu and choose "lock version."  

It seems that there is some other more permanent way to do this... but i can't remember it at the moment.. I just have to keep a close eye on what i'm updating to keep my Gaim2 beta 6 from downgrading...

---

### Post by darweth on 2007-02-05
Yeah, I tried sudo aptitude hold amarok but the Notification update STILL pops up.  I will look around Synaptic.

That is interesting about your Gaim though.  I installed 2.0 Beta 6 FROM the Ubuntu update system...

---

### Post by comfurtn on 2007-02-05
> **darweth said:**
> That is interesting about your Gaim though.  I installed 2.0 Beta 6 FROM the Ubuntu update system...

Really?  I had to manually install beta 6 because the version showing up in the edgy repositories is 2.0beta4.

---

### Post by darweth on 2007-02-05
I guess some other repository in my list must have had it.  

Yeah... I tried lock and it doesn't seem to do anything.  Guess I just need to always make sure it is unchecked until I figure this out.

---

### Post by comfurtn on 2007-02-05
I found something that may help us out... 

[this]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html") howto has a section at the end of the page on "pinning" a package version.

---

### Post by comfurtn on 2007-02-05
> **comfurtn said:**
> I found something that may help us out... 

[this]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html") howto has a section at the end of the page on "pinning" a package version.

Apparently, it works!

> Package: gaim
Pin: version 2.0.0beta6-1
Pin-Priority: 1000


Using 1000 will keep it from downgrading... and its off my upgrade list now!

---

### Post by darweth on 2007-02-05
Excellent!  Thank you!  It worked here too.

---

### Post by CompShrink on 2007-02-19
I had to do this for wine, as versions above 0.9.20 will not work with xinerama (dual monitor).

I know in the past locking the version in synaptic worked, so it's a new problem.

After you go to package > lock version, if you highlight that package again, and go back into the menu, is there a check mark next to lock version? There isn't for me, and there used to be when I did that. Is anyone else having this problem?

Pinning worked for me, by the way. But you shouldn't have to resort to that.

---

