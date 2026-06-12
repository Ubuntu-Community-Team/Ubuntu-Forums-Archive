---
title: "Adding (deb) sources to synaptic"
date: 2004-11-02
forum: General Help
---

### Post by v79 on 2004-11-02
Hi
New to Ubuntu. Very nice so far. Anyway, i've been trying to install ruby-gnome2 on my system for some development work. It depends on libgda2-ruby (both of these are in universe, which is fine). But libgda2-ruby depends on a later version of libxslt than is in universe (libxslt-1.1.8 or greater).

So I thought I'd find a deb of libxslt-1.1.8, add the following address as a repository:

[http://www.backports.org/debian/dists/woody/libxslt/binary-i386/](http://www.backports.org/debian/dists/woody/libxslt/binary-i386/)

And bob's your uncle. Didn't work though. And now that server is down.

So, where can I go from here? Is libxslt-1.1.8 in hoary, and if so, how do I add hoary as a source (I presume it's a bit like 'cooker' on mandrake?)?

Many thanks

v79

---

### Post by diebels on 2004-11-02
You could replace all that says warty with hoary. But it's recommended to wait a week or two. At the moment it's more like debian experimental than debian unstable?

---

### Post by v79 on 2004-11-02
[QUOTE=diebels]You could replace all that says warty with hoary. But it's recommended to wait a week or two. At the moment it's more like debian experimental than debian unstable?[/QUOTE]

I found that on another forum. Replaced warty with hoary, installed libxslt, then went back to warty. Worked for me!

---

