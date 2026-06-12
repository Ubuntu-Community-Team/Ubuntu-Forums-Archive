---
title: "Ways to increase speed in Xubuntu for really old PC's?"
date: 2008-01-14
forum: General Help
---

### Post by diablo75 on 2008-01-14
I am looking for a collection of ways to increase speed of ubuntu/xubuntu for installs done on older PC's.  I just set my father up with a 450 MHz Celeron with about 192 megs of ram, and I'd like to see how fast I can make it run.

What services could I disable?  What else could I do to increase overall system speed?  Etc.

Thanks for the help!

---

### Post by ugm6hr on 2008-01-14
Maybe try a different Window Manager?

*icewm* is a reasonable choice.  There are plenty of threads about icewm.

---

### Post by Craigus on 2008-01-14
Consider trialling a fluxbox based distro:

[http://antix.mepis.org/index.php/Main_Page]("http://antix.mepis.org/index.php/Main_Page")

[http://pcfluxboxos.wikidot.com/]("http://pcfluxboxos.wikidot.com/")

---

### Post by RedSquirrel on 2008-01-15
Start with a minimal installation and use a light window manager (Openbox, IceWM, Fluxbox...)

[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

K.Mandla's blog has some speed tips:

[http://kmandla.wordpress.com](http://kmandla.wordpress.com)

---

### Post by HermanAB on 2008-01-15
Add more RAM.

Cheers,

Herman

---

### Post by articpenguin on 2008-01-15
one way is too use the JFS file system. It uses less cpu than the other linux filesystems.

---

### Post by aysiu on 2008-01-15
> **diablo75 said:**
> I am looking for a collection of ways to increase speed of ubuntu/xubuntu for installs done on older PC's.  I just set my father up with a 450 MHz Celeron with about 192 megs of ram, and I'd like to see how fast I can make it run.

What services could I disable?  What else could I do to increase overall system speed?  Etc.

Thanks for the help!
I would not use Xubuntu at all. Xubuntu uses a lightweight desktop environment, but it is still a desktop environment.

Instead use a window manager (much lighter than desktop environments). I'd recommend IceWM or Fluxbox.

---

### Post by diablo75 on 2008-01-16
What are the differences between fluxbox and IceWM?  Since his system is already set up with xubuntu, using xfce (right?), what would I need to do to switch that environment over?

---

### Post by ugm6hr on 2008-01-16
> **diablo75 said:**
> What are the differences between fluxbox and IceWM?  Since his system is already set up with xubuntu, using xfce (right?), what would I need to do to switch that environment over?

Read here for info on WMs: [http://xwinman.org/](http://xwinman.org/)

To install icewm (enable all repos first):
```
sudo apt-get install icewm menu
```

Once installed, you can chose icewm in "session" from the login screen.

You will have to configure the WM though: for example, starting thunar (for desktop) & thunar-volman (for auto-mounting USBs etc) in startup.  Details about how to do that is in the icewm website (or you can use *iceconf* I think).  

And you will probably want a new theme: [http://www.box-look.org/index.php?xsortmode=high&page=0&xcontentmode=7311](http://www.box-look.org/index.php?xsortmode=high&page=0&xcontentmode=7311)

Hope that helps.

---

### Post by jerrykenny on 2008-01-16
I'd use ext2 for everything (well except swap)

Mount the ext2 partitions noatime.

Caveat, . . . if you have a bad crash, you'll want a knoppix or other bootable linux disk you can run e2fsck from . . . . . and do regular backups

---

