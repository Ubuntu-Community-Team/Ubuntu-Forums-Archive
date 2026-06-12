---
title: "[SOLVED] pkg-config Query"
date: 2008-03-22
forum: General Help
---

### Post by gmjs on 2008-03-22
Hi,

I've been trying to compile some software (Banshee 0.98 - and making a mess of it as usual :() and, after installing some prerequisites (including 'mono') I convinced its **./configure** that gstreamer was not installed.

I decided that this was something to do with pkg-config, but the PKG_CONFIG_PATH variable was blank and this had been detecting libraries fine until I got this far.

I took the latest copy of pkg-config and installed it.  Now **configure** reports that Glib2 and lib2xml are missing.  I'm pretty sure they're not.

Is there a way of getting pkg-config to search for libraries and repopulate what's on the system?  I don't understand what pkg-config actually does or how, even after reading its **man** page.

Does anyone have any suggestions as to what I should do to get the system to acknowledge Glib2 and gstreamer?

Many thanks,

Graham

---

### Post by gmjs on 2008-03-22
OK.  I think I know what I did wrong.

I think I overwrote the contents of /usr/lib/pkgconfig with the pkgconfig folder created when installing mono.  Probably irreversable without reinstalling the libraries or adjusting the version numbers (which I'm not clever enough to do)!

Never mind!

---

