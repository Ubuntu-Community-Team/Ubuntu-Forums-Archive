---
title: "installing programs from source."
date: 2005-07-27
forum: General Help
---

### Post by woedend on 2005-07-27
i am very new to linux but I do like ubuntu.  Synaptic/apt-get is great.  However, naturally not all programs I want are in apt, so it appears you have to download source.  The package in question for time being is xmmsmplayer-0.5.  Xmmplayer from synaptic freezes me so I heard this one worked better(working at all is better than current).  Anyhow, I extract the tar.gz file.  First time I tried to ./configure, it says no C compiler found.  So I searched synaptic and found gcc, and installed it.  Now I get a little further into ./configure to the message:
*** The gtk-config script installed by GTK could not be found
*** If GTK was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GTK_CONFIG environment variable to the
*** full path to gtk-config.
configure: error: *** GTK+ >= 1.2.2 not installed - please install first ***

any idea what I do here?

---

### Post by varunus on 2005-07-27
First of all, install the "build-essential" package; it contains stuff you'll need to compile every piece of software.  :)

You need to look up all the dependencies for Xmmplayer and install their "dev" packages from Synaptic.  The problem you have below can be solved by installing libgtk1.2-dev from synaptic.

---

### Post by woedend on 2005-07-27
[QUOTE=varunus]First of all, install the "build-essential" package; it contains stuff you'll need to compile every piece of software.  :)

You need to look up all the dependencies for Xmmplayer and install their "dev" packages from Synaptic.  The problem you have below can be solved by installing libgtk1.2-dev from synaptic.[/QUOTE]
 wow...thanks varunus.  After installing libgtk1.2, it went further to give me an xmms error, so i installed xmms-dev.  that was the first time installing something from source so I had no idea whether it worked or not(confusing), but i looked in xmms and there it was.  Thank you so much!

---

