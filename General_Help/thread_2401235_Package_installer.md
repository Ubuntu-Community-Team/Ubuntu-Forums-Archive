---
title: "Package installer"
date: 2018-09-15
forum: General Help
---

### Post by jbcohen on 2018-09-15
Was reviewing the packages in the installer and noticed that some say universe and others say multiverse while some say neither.  What is the difference?

---

### Post by yetimon_64 on 2018-09-15
This Ubuntu Documentation [[COLOR=#0000ff]--link--[/COLOR]]("https://help.ubuntu.com/community/Repositories/Ubuntu") has a description for the 4 usual repos used in ubuntu; main, restricted, multiverse and universe.

Here is another [[COLOR=#0000ff]--link--[/COLOR]]("https://help.ubuntu.com/community/Repositories") with a bit deeper explanation of the main 4 repositories and with further links to related subjects that may help you understand the repository system and how it can be used.

---

### Post by jbcohen on 2018-09-15
Why is there a package installer and a snap installer.  Wouldn't one be enough, perhaps one could say there are three because of the command line installations.

---

### Post by TheFu on 2018-09-15
> **jbcohen said:**
> Why is there a package installer and a snap installer.  Wouldn't one be enough, perhaps one could say there are three because of the command line installations.

Because snaps are new and packages are from the 1990s.  Snaps require certain other tools to be useful.
APT is the package management system for Debian/Ubuntu systems. There are many user-front-ends to APT - Synaptic, apt-get, apt, dpkg, aptitude and a few others.  These all work with the APT backend database for a consistent dependency model.

Snap is a new way to install and use programs. It is outside the APT management system. You can google to find more about snaps, but in general, they try to be self-contained programs with all dependencies pre-included.  They run in a lite-container trying to segment the program from harming the OS.  This is great and terrible, depending on your needs.  For something like an email program and web browser, having them contained and limited is a good idea for security.  But if you need lots of external support libraries to be available and they are outside the "container", unavailable,  that will likely prevent those external addons from working.

You can have a fully functional system without any snaps.
You cannot have a fully functional debian/ubuntu system without APT.

---

### Post by jbcohen on 2018-09-15
Now that I have a better concept of the package libraries is there any pages that teach me to browse it.  I understand the search function but I have a hard time understanding the results of the search

---

### Post by TheFu on 2018-09-15
> **jbcohen said:**
> Now that I have a better concept of the package libraries is there any pages that teach me to browse it.  I understand the search function but I have a hard time understanding the results of the search

I don't think you mean to use the term "package libraries" - "repositories" is the term, I think you mean.  Package libraries would be too much like library packages which the normal desktop APT interface hides from end-users.  If you use a different front-end to APT (like any of those I've listed), then you can see thousands of "library packages".  If you aren't a software developer, they'd be of little use.   I suspect you'd be happy with **synaptic**, but don't really know.

As for snap lists, I haven't a clue. Perhaps someone else can offer help.

---

