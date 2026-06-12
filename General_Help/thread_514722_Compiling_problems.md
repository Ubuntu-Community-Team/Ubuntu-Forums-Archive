---
title: "Compiling problems"
date: 2007-08-01
forum: General Help
---

### Post by ripdog on 2007-08-01
I was trying to compile Avant window navigator, and encountered a few problems.

Put quite simply:```
No package 'glib-2.0' found
No package 'gobject-2.0' found
No package 'gtk+-2.0' found
No package 'gdk-2.0' found
No package 'libwnck-1.0' found
No package 'gconf-2.0' found

```

This MAY sound like an open-shut case of a simple apt-get install glib gobject etc...

But half of these packages seem to exist at all,and the ones that do are already installed.

I check them all in Synaptic, the results are...

Glib appears to be already installed in all incarnations.
Last time i checked, gtk wasn't a single package (I USE KUBUNTU for the record)
The only mention of gdk were a few drawing packages, I installed them anyway, but no difference.
libwnck does exist, and i didn't have the dev package, but getting it made no difference.
I already had all gconf related packages.

Anyway, nothing I install makes any kind of difference, so i guess that means it can't find them. Any help please?

PS: If you want my config.log, you'll have to tell me where it is, I'm not sure.:(

---

### Post by geraldm on 2007-08-01
google on "avant window manager" returned this thread
[http://ubuntuforums.org/showthread.php?p=2093300](http://ubuntuforums.org/showthread.php?p=2093300)

Good luck, 
Gerald

---

### Post by mannheim on 2007-08-01
> **ripdog said:**
> 
Glib appears to be already installed in all incarnations.
Last time i checked, gtk wasn't a single package (I USE KUBUNTU for the record)


Maybe you already have this, but when the compilation complains it can't find glib-2.0 or gtk+-2.0, then you need to install **libglib2.0-dev** and **libgtk2.0-dev** most often.

---

