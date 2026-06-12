---
title: "Upgrading to Gnome 3.8 breaks it all"
date: 2013-07-07
forum: General Help
---

### Post by leosubhadeep on 2013-07-07
Hi, good to be back here after a while. :popcorn:

**Facing a problem with Ubuntu 13.04 X64**. Installed Gnome shell and created two accounts, on one Unity is default, on another gnome is default DE. Everything was working well with gnome 3.6, but after hearing that gnome for Ubuntu 13.04 can be upgraded to 3.8, did that.

Now, Unity DE is broken, and is acting illogically (like hangs, wallpaper /bar disappears etc. to name a few!). I installed gnome 3.8 from gnome 3 stable ppa.:-k
What to do now? Should I revert back to 3.6 (don't know how to do that, if possible at all without uninstalling! [-o

---

### Post by monkeybrain2012 on 2013-07-07
I have only tried it once, apparently the gnome3 ppa is not meant to work with Unity.

You can revert back to gnome 3.6 by purging the ppa
First install ppa-purge if you haven't already
```
sudo apt-get install ppa-purge
```
then run it
```
sudo ppa-purge ppa:gnome3-team/gnome3
```

I assume that you installed gnome-3.8 from the above ppa, if not, change it to whatever ppa you use.

---

### Post by markbl on 2013-07-07
You did a "sudo apt-get update and sudo apt-get dist-upgrade" after adding the gnome3 ppa didn't you? (as the instructions say). I used to have a problem with the Unity background when using the gnome 3 ppa but I noticed that has been fixed very recently. Make sure you are running Nautilus to "manage the desktop" of course as Unity requires that (set it via gnome-tweak-tool).

---

### Post by leosubhadeep on 2013-07-08
> **markbl said:**
> I used to have a problem with the Unity background when using the gnome 3 ppa but I noticed that has been fixed very recently.

Well according to source, **gnome 3.8 is far better** (I can see why) *but it shouldn't be installed before Ubuntu 13.04 (Canonical) fully supports it*. They say, it's buggy too, though I found only one or two bugs that I had reported to [launchpad]("https://www.launchpad.net"). Gnome always has some bugs :p, what's the big deal?

**What do you (and all others) suggest about staying with gnome 3.8 (for freshness and features) or downgrade to 3.6+ (for support and stability)?** :confused:
I wish I could use fedora gnome spin! It uses newer version of gnome!

 > **markbl said:**
> Make sure you are running Nautilus to "manage the desktop" of course as Unity requires that (set it via gnome-tweak-tool).

**What was that??**

---

### Post by grahammechanical on 2013-07-08
Did you follow these instructions? There are warnings there. Also instructions for removing.

[http://www.omgubuntu.co.uk/2013/04/gnome-3-8-ppa-for-ubuntu-gnome](http://www.omgubuntu.co.uk/2013/04/gnome-3-8-ppa-for-ubuntu-gnome)

Regards.

---

### Post by monkeybrain2012 on 2013-07-08
> **leosubhadeep said:**
> 

I wish I could use fedora gnome spin! It uses newer version of gnome!

 

What is stopping you? :)

---

### Post by leosubhadeep on 2013-07-11
> **grahammechanical said:**
> Did you follow these instructions? There are warnings there. Also instructions for removing.

Yes I did. But didn't get seamless gnome+unity integration as it was with gnome 3.6. While trying to downgrade, I was getting "broken package" error. I followed the available commands/hacks but in vain.:(
One more thing I forgot to mention.. I had cairo dock installed on both my unity and gnome desktop. can this be anything? Should I remove them and retry?

> What is stopping you? :smile: 
**The same reason you are wasting your time in here and throwing stupid jokes instead of being helpful**! :D

---

### Post by leosubhadeep on 2013-07-12
It's latest: the USC or Ubuntu Software Center is not opening at all from unity DE; and it's crashing from gnome 3.8 DE! Is there a fix for this?

---

