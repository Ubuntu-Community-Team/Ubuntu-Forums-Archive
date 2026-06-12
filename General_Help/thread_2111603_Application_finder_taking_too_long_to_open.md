---
title: "Application finder taking too long to open?"
date: 2013-02-02
forum: General Help
---

### Post by nhanb on 2013-02-02
I originally had Ubuntu 12.10, but recently installed xubuntu-desktop, following the guides from [this post]("https://sites.google.com/site/easylinuxtipsproject/alternative").

Everything is snappy, except for the Application Finder: it takes at least 5 seconds to open up. I don't know if this is normal, but it is the only thing that bugs me so far. Without this annoyance, I'd say xubuntu is perfect. So, does this happen to you? Does anyone know how to fix this?

---

### Post by The Cog on 2013-02-02
Sorry, I've been using Xubuntu for a couple of years but I don't know what you mean by the "Application Finder". Can you explain? 

I haven't noticed anytihng that takes that long to open.

---

### Post by nhanb on 2013-02-02
Here it is. Can you help me? It lets you type the name of the application you want to start, pretty much like Unity's App lense, I guess.

[IMG]http://i45.tinypic.com/154f2p0.png[/IMG]

---

### Post by tgalati4 on 2013-02-02
What program comes up if you hit Alt-F1?

---

### Post by nhanb on 2013-02-02
Pressing Alt-F1 opens the application menu on the default panel:

[IMG]http://i48.tinypic.com/35iuhag.png[/IMG]

**UPDATE**:

Turns out this problem has already been addressed here: [http://ubuntuforums.org/showthread.php?t=2031253](http://ubuntuforums.org/showthread.php?t=2031253) . The solution is simply append **--disable-server** to the command like so:
> xfce4-appfinder --disable-server

Thanks for your time, guys. And sorry for not searching thoroughly enough :P

---

