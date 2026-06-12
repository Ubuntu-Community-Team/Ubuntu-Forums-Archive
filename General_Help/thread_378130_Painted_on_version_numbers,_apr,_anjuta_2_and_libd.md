---
title: "Painted on version numbers, apr, anjuta 2 and libdb all wrapped into one cohesive ARG"
date: 2007-03-06
forum: General Help
---

### Post by Mr. Picklesworth on 2007-03-06
I am trying to configure Anjuta 2 for compiling, and finally I have installed all the required packages (sorry, I didn't keep track of which ones I needed; in retrospect, I should have documented that). However, there are a few bits of extra functionality, such as its SVN plugin, which I also want compiled and there are still some more unmet dependencies for that.
Most of these dependencies are easily dealt with, with the exception of one: libaprutil1-dev.

To compile Anjuta 2 (or much else that is a Gnome app), I need libgnome-dev. However, both libgnome-dev and libaprutil1-dev depend on a package known as libdb-dev (the Berkley Database Libraries). The problem? Some oaf decided it a good idea to have libdb named with its version number (libdb3-dev, libdb4.3-dev, libdb4.4-dev) in natural "this isn't backwards compatible but if you want you can install the older version" fashion, but also to have each version conflicting with its predecessors. (!!!!!)
This, by the elementary law of "No one package is the center of the universe!", means that if another package, say libgnome-dev, happens to depend on libdb3-dev but not pay *close attention* to its further development because the current one works fine and no self-respecting database library breaks back compatibility with every update after 3 major versions (right?!), it gets broken by any other package which happens to depend on that future version, such as libaprutil1-dev.

Granted, this isn't too uncommon; the kernel packages and in fact a vast number of other packages have version numbers in their names too, but they do not *conflict* with each-other!

Brilliant, hm?

So, what I'm hoping for is a fix, of course.
How can I have both libgnome-dev and libaprutil-dev installed at the same time when they both depend on a package which hates itself?


Disclaimer:
I know nothing about packages, dependencies or Linux development in general.
Please forgive my ignorance if my above rant is totally incorrect and instead feel free to laugh at my stupidity. After all, "a laugh a day keeps the doctor away", remember? I'm doing you a favour.

---

### Post by Mr. Picklesworth on 2007-06-11
Bumped into this one again trying to install libglade-gnome0-dev, where libdb3-dev conflicts with the other libdbs, resulting in the death of a package required by libsvn-dev, which I need.

I guess I should forumulate a question from this rant:
-Is there a sane reason for this?
-Can I 'trick' the thing into not caring about this particular package conflict? (Or, better, does a different version of libgnome depend on a different / newer version of libdb?).

Edit:
Ah, libgnome2-dev. Looks like libglade-gnome is all I need anyway.

---

