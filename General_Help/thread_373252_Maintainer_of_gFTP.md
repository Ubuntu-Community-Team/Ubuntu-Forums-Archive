---
title: "Maintainer of gFTP"
date: 2007-03-01
forum: General Help
---

### Post by cstrom on 2007-03-01
Hi Ubuntus,

I've got a simple question. What would be the best way to contact a maintainer of a particular package? In this case it's regarding gFTP and specifically that it does not have SSL support built in. Obviously it's not difficult to download and compile the source (just done that), but it would be nice if the package could actually have SSL support from the start.

So, how would I send this request to the maintainer?

Many thanks for your help,
Chris

---

### Post by theslut on 2007-03-01
i don't think you will have much luck. it's not been updated in years. There is so much work that needs to be done on it too.

---

### Post by scxtt on 2007-03-01
you could email the person below and see if you get a reply :-p
```
[font=courier]:> aptitude show gftp
Package: gftp
New: yes
State: not installed
Version: 2.0.18-11ubuntu1
Priority: optional
Section: universe/net
Maintainer: [color=red]Aurelien Jarno <aurel32@debian.org>[/color]
Uncompressed Size: 77.8k
Depends: gftp-gtk (= 2.0.18-11ubuntu1), gftp-text (= 2.0.18-11ubuntu1)
Description: X/GTK+ FTP client
 gFTP is a multithreaded FTP client, available in two versions:
 * version for X, written using GLib and GTK+
 * version for the console, using only GLib

 This is an upgrade convenience package, it's only useful for depending on.[/font]
```

---

