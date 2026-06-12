---
title: "What is the difference between Ubuntu Software Center and Synaptic Package Manager?"
date: 2013-12-28
forum: General Help
---

### Post by asiancraig2 on 2013-12-28
Whats' the difference between Ubuntu software Center and Synaptic PAckage MAanger?  don't they both do the same thing?
is ubuntu software center just more high level and Synaptic package manager is MORE powerful?
do synmaptic package manger provide more updated applications as opposed to ubuntu software center? cause i've noticed this personally but i'm not sure if it's true.

---

### Post by Bashing-om on 2013-12-28
asiancraig2; Hi !

Both USC and synaptic are but front ends for "dpkg".
USC is the more user friendly, and yes you are correct in that synaptic has greater functionality.
All the package management tools/utilities operate from the same sets of data (software repository) so same same versions are available in any medium used to access the repository for a particular version.

[INDENT][INDENT]hope this helps
[/INDENT][/INDENT]

---

### Post by asiancraig2 on 2013-12-28
> **Bashing-om said:**
> asiancraig2; Hi !

Both USC and synaptic are but front ends for "dpkg".
USC is the more user friendly, and yes you are correct in that synaptic has greater functionality.
All the package management tools/utilities operate from the same sets of data (software repository) so same same versions are available in any medium used to access the repository for a particular version.
[INDENT][INDENT]hope this helps
[/INDENT]
[/INDENT]


i thought they were front ends for APT?  so they are based on APT and APT is based on DPKG?

---

### Post by Bashing-om on 2013-12-28
asiancraig2; 

Yeah, Imagine this operating system with no package management system, there was a time ! .. and some real smart folks came up with "dpkg";
aptitude is a another layer on that foundation ,from aptitude was developed apt-get, then along comes the graphical front ends, the two that have lasted are synaptic and the currently encouraged/direct-supported Ubuntu Software Center.

[INDENT][INDENT]just keeps getting better
[/INDENT][/INDENT]

---

### Post by vasa1 on 2013-12-28
> **asiancraig2 said:**
> i thought they were front ends for APT?  so they are based on APT and APT is based on DPKG?
Here's a link [http://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html](http://www.debian.org/doc/manuals/debian-faq/ch-pkgtools.en.html) and a quote from there> It is important to understand that the higher level package management tools such as aptitude or dselect rely on apt which, itself, relies on dpkg to manage the packages in the system.

---

