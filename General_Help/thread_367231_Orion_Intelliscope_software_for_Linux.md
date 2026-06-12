---
title: "Orion Intelliscope software for Linux"
date: 2007-02-21
forum: General Help
---

### Post by daxdog on 2007-02-21
I have an Orion SkyQuest Intelliscope XT8 with the computerized object locator.  I am wanting to interface an old laptop with this telescope.  I have already acquired a Thinkpad 600 for the project.  I put a 20GB HDD that I had laying around, an old wireless network card, and installed Xubuntu 6.10.  Though it is slow, the laptop operates fine.

I found information about making the cable to connect the Intelliscope with the laptop and made the cable.  The only software I have capable of controlling the telescope is KStars.  I have tried different telescopes for KStars, but none of them do any more than just connect.  Data is not properly transferred.  I think the problem is that KStars is not setup to recognize this type of telescope.

Who knows of software available for Linux which interfaces with the Orion Intelliscope system?

Thanks,

George

---

### Post by daxdog on 2007-03-04
Jason Harris (the developer for KStars) wrote to me:

> 
Intelliscope support has been added to the KDE-4.0 version currently
under development, so it's coming soon.

If you're feeling brave, you are welcome to download, compile and
install this development version.  There are instructions on our website:
[http://edu.kde.org/kstars/svn.php](http://edu.kde.org/kstars/svn.php)

They're a little out of date (e.g., dbus is version 1.0 now), but still
pretty good.

If you install the development version, don't expect everything to work
perfectly, but you can expect that most things will mostly work (I'm
talking about KStars specifically, not all of KDE).  If you notice
things that are broken or strange, please do tell us about them!  Either
file a bug at bugs.kde.org, or send a mail to [email]kstars-devel@kde.org[/email].

Anyway, a stable release of 4.0.0 is expected sometime in late 2007, so
you could simply wait for that, if you don't want to bother with the
bleeding edge.

I may give the new version a try.  I have not had much success compiling **any** software for Linux, so I am little reluctant to try with a development version of any software.

---

