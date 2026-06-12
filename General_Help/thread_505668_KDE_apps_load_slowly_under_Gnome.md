---
title: "KDE apps load slowly under Gnome"
date: 2007-07-20
forum: General Help
---

### Post by stchman on 2007-07-20
Hello all, I have a question.

When running Gnome apps that were made for Gnome load very quick.  When I run KDE apps (K3B, K9Copy, KTorrent) the load very slowly.  K3B takes about 15 secs to load.  Is this just the way it is?  Is there a way to speed up the loading of KDE apps under Gnome?  Do KDE apps when using Kubuntu load quickly?

Thanks

---

### Post by qamelian on 2007-07-20
Unfortunately, yes. When you run Gnome apps under Gnome, most of the necessary libraries are already loaded, so the apps load quickly. SInce KDE apps running under Gnome also have to start the necessary KDE libraries, there is a slightly longer startup time.

---

### Post by Happy_Man on 2007-07-20
> **stchman said:**
> Hello all, I have a question.

When running Gnome apps that were made for Gnome load very quick.  When I run KDE apps (K3B, K9Copy, KTorrent) the load very slowly.  K3B takes about 15 secs to load.  Is this just the way it is?  Is there a way to speed up the loading of KDE apps under Gnome?  Do KDE apps when using Kubuntu load quickly?

Thanks
When KDE apps load under GNOME, they have to load all the QT libraries. GNOME apps don't do this because all their shared GTK libraries are already loaded. 

So, when using Kubuntu (or any KDE) all KDE apps load quick, but GNOME apps take forever.

---

### Post by stchman on 2007-07-20
> **qamelian said:**
> Unfortunately, yes. When you run Gnome apps under Gnome, most of the necessary libraries are already loaded, so the apps load quickly. SInce KDE apps running under Gnome also have to start the necessary KDE libraries, there is a slightly longer startup time.

So I gather that the same thing happens when you run Gnome apps under KDE?  Is there a way to have the necessary KDE libraries load up at start or is this not a good idea?  I mean most modern PCs have a 1GB of RAM or better.

I gather that Gnome uses the GTK+ and KDE uses QT.

---

### Post by stchman on 2007-07-20
One solution I was reading about was to load kdeinit at startup in session under preferences.  Has anyone else tried this?

---

### Post by Happy_Man on 2007-07-23
> **stchman said:**
> One solution I was reading about was to load kdeinit at startup in session under preferences.  Has anyone else tried this?
You can try it..... logging in will take longer than usual, though.

---

### Post by stchman on 2007-07-23
> **Happy_Man said:**
> You can try it..... logging in will take longer than usual, though.

I did and yes the login was a touch longer but no biggie.  More importantly KDE apps load really fast now!!!!

---

