---
title: "ubuntu-desktop"
date: 2007-05-06
forum: General Help
---

### Post by sefs on 2007-05-06
HI have a problem with feisty (i rank this as a critcal bug) simply because it does not work as desired.

I want to remove gaim from my machine.  but it also forces me to remove ubuntu-destop.  Before you say its ok to remove ubuntu-destop ... i simply dont want too.  why should i have too.  Anyway, ok i'll remove it but reinstall it immediately after.  But the damn thing wants to force me to install gaim and Network Manager again ..which ... i ... did ...not ...request!!!!

How in Gods green earth can i simply reinstall the ubuntu-desktop package and not the gaim and networkmanager.  Can't a guy simply decide what he needs and does not need?  For goodness sakes man.

---

### Post by aysiu on 2007-05-06
From [the Ubuntu Common Questions page](https://help.ubuntu.com/community/CommonQuestions#head-957d1f0d9534d9e9a43a1ade8e3622bc04a8d812): > **What is a meta-package? Is it safe to remove the ubuntu-desktop package?**
A meta-package is a package that doesn't contain applications within itself, but simply depends upon particular versions of other packages, so that when it is installed, it drags all of them in too. The package manager uses it to know which particular packages to install. For example, the ubuntu-desktop metapackage installs the full GNOME desktop environment, with all the other packages that are in a default Ubuntu install. The existence of meta-packages makes it very easy to install other Ubuntu derivatives on your desktop; see below for more information.

It is technically just fine to remove a meta-package, if required, and this shouldn't necessarily cause any problems. However, it is strongly recommended that you reinstall that package if you decide to manually upgrade to another version of Ubuntu. The package manager requires those packages to be installed for it to successfully perform the upgrade.  I'll rephrase it a bit for you, too: *ubuntu-desktop* is just a pointer to other packages. It is defined as "the set of all packages that come by default in Ubuntu." So if you remove any one of those packages, the pointer no longer applies. 

It's a bit like having a wedding ring, which states "I'm married to somebody." Well, if you get divorced, the ring no longer applies, so you might as well take it off. The ring doesn't make you a more functional human being--it's just a symbol of what's there... a label of you two as a couple. 

Or say you have a label that says "Six-pack of beer." Well, if you take away one of those beers, it's now a five-pack, so the label doesn't really apply. But those five remaining beers are still fully functioning beer cans, which can dispense alcoholic liquid to you.

*ubuntu-desktop* is a lot like that--a symbol of all the default applications being installed. Uninstall one of them, and you **still have a functioning system**, but you don't have "*ubuntu-desktop*," meaning that you don't have the set of all the default applications installed.

---

### Post by CocoAUS on 2007-05-06
ubuntu-desktop is a metapackage.  It points to all sorts of other packages.  If you were to install kubuntu-desktop, it would install a whole bunch of KDE programs.  When you remove one of the packages included in ubuntu-desktop, you no longer have the ubuntu-desktop package installed, because ubuntu-desktop is simply a list of packages, and you're removing part of that list.  Everything else is still installed just as it was, it simply is no longer the ubuntu-desktop package, because by definition, ubuntu-desktop includes gaim.

---

### Post by sefs on 2007-05-06
Will this in anyway brake an upgrade to a future update of ubuntu namely gutsy gibbon?

---

### Post by aysiu on 2007-05-06
> **sefs said:**
> Will this in anyway brake an upgrade to a future update of ubuntu namely gutsy gibbon?
If you want a greater likelihood of a smooth upgrade to Gutsy, keep *ubuntu-desktop* installed.

If *ubuntu-desktop* offends you that much, get rid of it, and when Gutsy Gibbon comes out, install *ubuntu-desktop*, do the upgrade, then remove GAIM and Network Manager again.

---

### Post by sefs on 2007-05-06
It offends me not having it on there.  I feel naked.  for some reason...

But i want to get rid of gaim so i can have pigin

---

### Post by aysiu on 2007-05-06
You can't have Pidgin and GAIM at the same time? Can't you just have GAIM installed and not use it? How big is your hard drive?

---

### Post by sefs on 2007-05-06
250 gb
but i was reading in one of the threads that it conflicted with gaim-data.

---

### Post by ticopelp on 2007-05-06
I have a new sig, thanks to this thread and aisyu. Thanks!

---

### Post by aysiu on 2007-05-06
> **sefs said:**
> 250 gb
but i was reading in one of the threads that it conflicted with gaim-data.
Read [this post](http://ubuntuforums.org/showthread.php?p=2597678&highlight=gaim-data#post2597678).

---

### Post by sefs on 2007-05-06
Thanks for that aysiu.

---

