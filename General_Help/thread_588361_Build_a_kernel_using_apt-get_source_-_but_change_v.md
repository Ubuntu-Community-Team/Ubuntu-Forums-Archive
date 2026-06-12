---
title: "Build a kernel using apt-get source - but change version"
date: 2007-10-23
forum: General Help
---

### Post by ormandj on 2007-10-23
Hi,

I'm trying to build a custom kernel for my workplace. I followed the wiki guide on building the kernel - and that worked - but I ran into a problem.

I created a repository with the image/header debs, and added it to my system. Apparently, my debs were build with the same version information as the standard kernel, so they were not seen as an "upgrade".

How do I change the version, or at least append something like -myworkplace1 so in the future, when I push out updates to my repository, machines with the packages installed will auto-upgrade?

I tried doing a make-kpkg build, and that worked fine, but restricted modules are too much of a pain to deal with in that situation. So I'd prefer to do it the "right" way. 

I didn't know what forum to put this in, hopefully I choose the right one. My apologies if not!

Cheers,
David

---

