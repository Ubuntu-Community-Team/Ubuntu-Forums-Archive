---
title: "Aptitude Question"
date: 2006-08-31
forum: General Help
---

### Post by cssutto on 2006-08-31
I have decided to learn to use aptitude.

I understand aptitude's concept of dependencies when downloading new packages.

However, when you click on view, audit...you get a long list of packages at the top half of the screen and at the bottom half a line that says something like "rsync recommends xxxxx".

Are these dependencies that were not properly installed by apt-get or synaptic and that should be installed or are these packages that are nice to have but not really necessary.

There are, in my case, lots of them and some of them are large files.

Some are obviously not required....Russian or whatever .doc, etc., but others like the "rsync recommends" are confusing to me.

CSSJR

---

### Post by LKRaider on 2006-08-31
> or are these packages that are nice to have but not really necessary
Yes.

Packages sometimes recommend other packages that would add to the use of that particular package, but are otherwise not required to make it work (like dependencies).

So you can install from the recommended list only the ones you like, or none at all. :)

---

### Post by cssutto on 2006-08-31
Thanks for the quick reply.

Another one that bugs me is language-support-en.

It is described as a metapackage for language support, but to a non-tech like me, does not really say what it does for you.

CSSjr

---

### Post by cssutto on 2006-08-31
Brazil.

That always facinates me.

To get help from so far away so quickly.

Judging by your image, when I was your age, high tech was a table radio from Sears and a phonograph that could play 8 records.

CSSJR

---

### Post by DigitalAxis on 2006-08-31
Metapackages are packages whose sole function is to install a lot of other packages.

For instance, ubuntu-desktop is a metapackage.  It installs no program itself, it just claims to require all the packages that make up the Ubuntu GNOME desktop before it... well, does nothing. (but the package manager doesn't know that)
When a package manager tries to install ubuntu-desktop, it sees the long list of required programs and installs all of them, and voila, fully functioning new shiny GNOME desktop with no missing libraries.

So that language-support-en package probably depends on all the other packages someone has deemed required for proper language support.

---

