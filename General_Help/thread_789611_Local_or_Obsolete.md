---
title: "Local or Obsolete"
date: 2008-05-10
forum: General Help
---

### Post by Exsecrabilus on 2008-05-10
When you enable **hardy-backports** updates, do the package you install from updates get sectioned as **Installed (Local or Obsolete)** in Synaptic Package Manager?

---

### Post by sdennie on 2008-05-10
It shouldn't matter which repo a particular package comes from.  If you've installed it via apt-get or synaptic rather than calling dpkg directly, installed packages should appear under just regular "Installed".

---

### Post by Exsecrabilus on 2008-05-10
I meant updating packages with Update Manager. You know?

Like if you go to **System** >> **Administration** >> **Software Sources**, you can choose which type of updates you can install.

There's *hardy-security*, *hardy-updates*, *hardy-proposed*, and *hardy-backports*.

What I'm saying is *hardy-security*, *hardy-updates* and *hardy-proposed* are normal updates.

But *hardy-backports*, it says unsupported updates.

One day I saw updates available for certain packages so I opened up **Update Manager** and installed the new packages.

After that, while I was in **Synaptic Package Manager**, I checked the **Installed (local or obsolete)** tab and all the packages I updated were there.

What I'm asking is: Are they there because I enabled *hardy-backports* and they aren't official supported updates?

---

### Post by Endolith on 2008-12-08
I'd like to know this, too.  I have a number of packages in Local or obsolete that I installed from getdeb or checkinstall that I want to keep, but also a bunch that are useless as far as I can tell.  It seems some of these are "transitional" packages from upgrading?  But I wonder if others are leftovers from having backports and proposed updates enabled?  This would be helpful in figuring out which ones I can remove.

Also, it would be nice if I could somehow tag the packages I manually installed so I remember that they were installed by me and not by the system.

---

