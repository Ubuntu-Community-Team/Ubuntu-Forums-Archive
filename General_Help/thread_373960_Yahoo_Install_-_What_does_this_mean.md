---
title: "Yahoo Install - What does this mean?"
date: 2007-03-01
forum: General Help
---

### Post by lsutiger on 2007-03-01
I tried downloading the Debian package from [this site]("http://messenger.yahoo.com/unix.php"). hen I try to instal I get this message:
```

Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

```
What does this mean?

---

### Post by Iced_Kirby on 2007-03-01
> **lsutiger said:**
> I tried downloading the Debian package from [this site]("http://messenger.yahoo.com/unix.php"). hen I try to instal I get this message:
```

Unpacking ymessenger (from ymessenger_1.0.4_1_i386.deb) ...
dpkg: dependency problems prevent configuration of ymessenger:
 ymessenger depends on libgdk-pixbuf2 (>= 0.13.0); however:
  Package libgdk-pixbuf2 is not installed.
 ymessenger depends on libglib1.2 (>= 1.2.0); however:
  Package libglib1.2 is not installed.
 ymessenger depends on libgtk1.2 (>= 1.2.0); however:
  Package libgtk1.2 is not installed.
 ymessenger depends on libssl0.9.6; however:
  Package libssl0.9.6 is not installed.
 ymessenger depends on xlibs (>> 3.3.6); however:
  Package xlibs is not installed.
dpkg: error processing ymessenger (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ymessenger

```
What does this mean?

Did you follow the installation steps correctly? And did you use the right steps?

Also, why not use GAIM?

---

### Post by kerry_s on 2007-03-01
It's not compatible, it says right there in the system requirements"woody". It would probably work if it didn't have any dependency's. Remember when going outside the repos you want apps that are self contained and don't depend on anything.

---

### Post by lsutiger on 2007-03-01
OK Thanx..still learning here. day # 4! YAY!
I bought these two books on amazon:
[http://www.amazon.com/gp/product/1593270348/104-8375352-9684718](http://www.amazon.com/gp/product/1593270348/104-8375352-9684718)
and 
[http://www.amazon.com/gp/product/1590596277/104-8375352-9684718](http://www.amazon.com/gp/product/1590596277/104-8375352-9684718)
I read the reviews and did a little research, and from what I saw these were pretty much essential reading. Any other info will be greatly appreciated. :)
Thanx!

---

