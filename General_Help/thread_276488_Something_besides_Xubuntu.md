---
title: "Something besides Xubuntu?"
date: 2006-10-13
forum: General Help
---

### Post by Cable on 2006-10-13
A while ago I installed Xubuntu on an older computer that originally had Win98 on it (it ran *extremely* slowly).  I wanted to make it more usable (almost nobody used it anymore since it was so slow).  So, I opted for Xubuntu.  While it runs decently, it's still a bit slow.

[U][B]Specs
[/B][/U]Pentium III
320 MB RAM
nVidia GeForce 2 MX400

[U][B]Uses
[/B][/U]Internet browsing
Word processing
Instant messaging
Music
Some others...

This is a family computer.  I will not use it except for when I do maintenance on it (updating, etc.).  So, keep that in mind when I ask the following question:  What would be a good distro to use instead of Xubuntu?  I'd simply like it to run faster.  I'm considering doing a server install of Ubuntu and running IceWM or Fluxbox, and installing programs as they are needed.  Maybe Ubuntu Lite.  I've done a little research, and I'm sort of leaning towards IceWM at the moment, as it looks to be a lot lighter than XFCE but not quite as minimal as Fluxbox.

I'd kind of like to stay with Ubuntu but run something lighter.  I love the package management and it's extremely stable, which is really all this family computer needs.  But, throw all of your suggestions my way.

What do you think?

---

### Post by bionnaki on 2006-10-13
[http://www.vectorlinux.com](http://www.vectorlinux.com)
[http://www.damnsmalllinux.org](http://www.damnsmalllinux.org)
[http://featherlinux.berlios.de](http://featherlinux.berlios.de)
[http://www.puppyos.com](http://www.puppyos.com)

---

### Post by Cable on 2006-10-13
Can anybody speak to the usage of these distros?  Looking at the sites is good, but opinions and suggestions and stories of using them are even better.

---

### Post by aysiu on 2006-10-13
I'm a big fan of IceWM on Ubuntu.

Read more [here](http://ubuntuforums.org/showthread.php?t=263710).

---

### Post by Tamihania on 2006-10-13
...and I am a big fan of Fluxbox+Rox on a server install of Ubuntu - although there is a project of Fluxbuntu(more info in my sig) - Ubuntu derivative based on Fluxbox  which looks very promising. Fluxbox can be very "rich" on the desktop - especially together with Rox  (icons).  [Here _ is a very good howto set it up by bodhi.zazen._]("http://forums.debian.net/viewtopic.php?t=7345&sid=1951ea962cdd2a4f852c8ff87742519b")
....and [here]("http://forums.debian.net/viewtopic.php?t=5382&highlight=&sid=b72fcdb6d9ab3180a5f11d2f322f119d") is a good howto set up good server install...
I personally would not recommend you using any distro based on Slackware or Gentoo if you appreciate/ like Debian package management....(having not very good experience with it in the past).
I hope it will be of a help.
tami

---

### Post by ianmacgregor on 2006-10-13
I use fluxbox on Ubuntu in a PIII and it's nice and fast. Otherwise, I would recommend Damn Small Linux. It's only 50Mb and it runs quite fast on older hardware.

---

### Post by David Corrales on 2006-10-13
I'd stick with something like fluxbuntu. The update system and package management is really nice. Puppy or DSL linux sure are fast, but they're not as good as having a Debian base.

Edit: I just tried Fluxbuntu on a VM. It's not really usable for unexperienced people, the shift is just a pain. Doesn't have a lot installed by default also :(

---

### Post by Cable on 2006-10-14
So if I was to do a server install of Ubuntu + IceWM, what else would I need to install to get sound and other basic home computer needs?  How about syncing the clock automatically every day or something?  I can't think of anything else right now...

---

### Post by aysiu on 2006-10-14
I think your best bet is to install Xubuntu and then IceWM. Xubuntu will make sure you have all the necessary goodies. Then you can just *use* IceWM and not XFCE.

---

### Post by Cable on 2006-10-14
Well, if I did it that way it would sure make things easy.  Xubuntu is already running perfectly on the computer.  However, would there be unnecessary services and such running that wouldn't otherwise be running if I went the long route and did a server install then installed everything else?  I just want to make it as fast and usable as possible, but also have everything necessary for home computer needs.

Vector Linux also looks appealing, by the way.

---

### Post by Littleweseth on 2006-10-14
Actually, I use blackbox installed on my celeron-566 secondary computer w/ 384mb ram, running Ubuntu 6.06. I'm actually surprised at how snappy and usable it is, even while doing a multitude of things at once.

---

### Post by aysiu on 2006-10-14
> **Cable said:**
> Well, if I did it that way it would sure make things easy.  Xubuntu is already running perfectly on the computer.  However, would there be unnecessary services and such running that wouldn't otherwise be running if I went the long route and did a server install then installed everything else?  I just want to make it as fast and usable as possible, but also have everything necessary for home computer needs.

Vector Linux also looks appealing, by the way.
XFCE services (panel applets and such) won't be running when you log into IceWM, but you may have some systemwide processes running that you can stop if you install BUM (boot-up manager): ```
sudo aptitude update && sudo aptitude install bum
gksudo bum
``` The rest is self-explanatory.

Can I assume you have the Universe repositories enabled? That's where BUM is.

---

### Post by Cable on 2006-10-14
> **aysiu said:**
> Can I assume you have the Universe repositories enabled? That's where BUM is.

You can indeed assume this.  I'm not *that* much of a newbie any more.  :mrgreen:

---

