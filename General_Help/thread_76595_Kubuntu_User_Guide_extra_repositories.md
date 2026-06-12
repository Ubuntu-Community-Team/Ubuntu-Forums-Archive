---
title: "Kubuntu User Guide extra repositories"
date: 2005-10-15
forum: General Help
---

### Post by xbaez on 2005-10-15
Has anybody enabled these extra repositories from the Kubuntu guide?

# KDE 3.4.2 Mirrors (i386 only)
deb [http://mirror.cc.columbia.edu/pub/software/kde/stable/3.4.2/kubuntu](http://mirror.cc.columbia.edu/pub/software/kde/stable/3.4.2/kubuntu) hoary-updates main

Changing subjects do I need to download the Kubuntu CD and the Ubuntu CD in order to upgrade my KDE and Gnome to Breezy?
or should I just change the repositories?

the archive.ubuntu.com respositories have been slow during these days

---

### Post by t2kburl on 2005-10-15
Breezy comes with KDE 3.4.3 so no need for that repository.

How you choose to upgrade is up to you. I downloaded the kubuntu CD and did a fresh install on one machine and have been testing Breezy on another by changing all "hoary" in /etc/apt/sources.list to "breezy" and doing a dist-upgrade then updating packages as I went along ... probably downloaded 6 CDs worth of packages over the past few weeks that way.

Breezy is different ...  be prepared

---

### Post by xbaez on 2005-10-15
[http://kudos.berlios.de](http://kudos.berlios.de)

This is the Unofficial Kubuntu guide, an adaptation from the Ubuntu guide

Folks by reading this you'll be able to create your own DVDs with repositories and add them to your sources (for instance it's great for me since I could take all my .debs from the office to my house)

It provides a bit more information as well as more repositories, I didn't enabled any debian repositories (skype and marillat) but the rest of them seem to work ok

Only problem that I got was Kdevelop Interface designer (crashes), I'm going to install the old version for that one

---

### Post by Rory on 2005-10-15
[QUOTE=t2kburl]
Breezy is different ...  be prepared[/QUOTE]

Such an ominous comment.  :)  How so?  Please explain.

---

### Post by xbaez on 2005-10-16
today I was able to follow the Kubuntu Guide and burn my own DVD with all the updates that I have at my office for Kubuntu 5.04

really neat, now I can just have one DVD as a repository, burn it in my office, and keep my house laptop in sync :)

---

### Post by t2kburl on 2005-10-16
[QUOTE=Rory]Such an ominous comment.  :)  How so?  Please explain.[/QUOTE]
Didn't mean it to sound ominous ... just that it has a bit of a different feel to it than Hoary. Some things that Just worked in Hoary (Like installing vmware) needed extra tweaking and some new things are definite improvements (Adept over kynaptic).

---

