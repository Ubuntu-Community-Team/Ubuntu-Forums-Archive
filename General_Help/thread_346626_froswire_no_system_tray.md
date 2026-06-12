---
title: "froswire no system tray"
date: 2007-01-26
forum: General Help
---

### Post by warkro on 2007-01-26
I installed frostwire from Automatix.  in the previous versions I would get a system tray.  Now, I can't get it to work.   The option for the system tray icon does not exist.  anyone know how to get it to work.

---

### Post by warkro on 2007-01-27
Bump...did they disable the tray on this version?

---

### Post by jackrobinson on 2007-01-29
> **warkro said:**
> I installed frostwire from Automatix.  in the previous versions I would get a system tray.  Now, I can't get it to work.   The option for the system tray icon does not exist.  anyone know how to get it to work.

apparently they did. I cant find it either.

---

### Post by PacShady on 2007-07-03
After much frustration trying to find out why the tray icon doesn't seem to exist anymore, and even more frustration trying to work out why only a few people seem to have NOTICED (ie. no one has really bothered to question why there once was a tray icon and now there isn't), I found this in the Frostwire blog:

> *Originally posted at [http://www.frostwire.com/blog/?p=23](http://www.frostwire.com/blog/?p=23), bold mine*

Thanks to the Linux community for reporting the problem with FrostWire crashing on startup if you have Java 1.6.0.

You can download any of these installers and the problem will be solved.

frostwire-4.13.1.5-1.i586.deb (Ubuntu/Debian)
frostwire-4.13.1.5-1.noarch.rpm (RedHat)
frostwire-4.13.1.5-1.noarch.tar.gz (TGZ)

For those who want to know the details, it was an incompatibility issue between JDIC (SystemTray) and Java 1.6.0 which now brings its own Desktop Integration components. For now we’ve **turned off the Icon Tray on Linux**, until jdic updates, or we can find a better work around.

So that explains it. Due to some weird compatibility problem between Frostwire's tray icon and the latest Java, they disabled the tray icon to stop the whole thing from crashing. Fun. Unfortunately, I kinda NEED a tray icon, so now I'm on the lookout for a decent Gnutella (or better) program I can use that CAN use a tray icon, at least until the Frostwire developers can work out a way to fix this irritating bug in Java. I hope they can fix it soon!

'Shady

---

