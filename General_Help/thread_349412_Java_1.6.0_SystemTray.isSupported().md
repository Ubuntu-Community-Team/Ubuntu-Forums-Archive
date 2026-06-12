---
title: "Java 1.6.0 SystemTray.isSupported()"
date: 2007-01-30
forum: General Help
---

### Post by donut_irl on 2007-01-30
Hi,

I've just started trying to use java 1.6. I'm trying to create a system tray icon/menu but SystemTray.isSupported() returns false.

I'm running Gnome/Beryl, java version 1.6.0-b105

As far as I can tell from google under gnome it should be supported but is still returning false?

Thanks

---

### Post by Patiek on 2007-02-12
I am having the same problem.

Not sure what you are using as far as Beryl goes... but it seems to me that this is a (for me) XGL problem.

The SystemTray functionality of jdk 1.6 was working fine for my various java programs under standard gnome session using Xorg 7.1.

Unfortunately it appears that it is _not_ working under XGL. Does anyone have any other information (possible solutions)?

---

### Post by Patiek on 2007-02-12
I don't think this is an XGL problem. I am having the same problems without XGL now.

Does anyone have any other information?

---

### Post by Patiek on 2007-03-11
Forgot to post this:
[http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6438179](http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=6438179)

If you are using beryl or similar, you can work around by loading metacity, then loading your program, and finally switching window manager in beryl. Unfortunately, this is just a work around for the client rather than the software itself.

Does anyone have a better work around?

---

### Post by Ryba on 2007-03-27
Well at least this explains why my program only works on my laptop (using metacity) but not on my desktop at home (feisty with 3d effects enabled).

OMG i can't believe their "test" for tray support was "is the name of the application metacity or kwin".

That seems to be about the stupidest test I could ever imagine to see if tray support is enabled. They should have at least said "true" by default since all newer managers are supporting it (can't think of 1 that doesn't anymore by default).

---

