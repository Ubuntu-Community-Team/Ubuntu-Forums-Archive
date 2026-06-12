---
title: "Create a deb package from a pre-compiled tar/binary?"
date: 2007-02-11
forum: General Help
---

### Post by disturbedite on 2007-02-11
here is what i wanna do:

i wanna install stratagus 2.2.2 (released last month) but only version 2.2.1 is available in the ubuntu repos.  i have checked everywhere, all over online, and can't find a deb package.

i grabbed the tarball from the stratagus and what i would like to do is create a deb package from the tarball.

i know the normal procedure for creating deb packages with checkinstall after compiling, i do that on a fairly regular basis.  but i've never done it with a pre-compiled package.  is this possible with checkinstall?  and if so, how do i do it?  or is there another program that does that?

---

### Post by Maestro23 on 2007-02-11
Might help: [http://ubuntuforums.org/showthread.php?t=356232](http://ubuntuforums.org/showthread.php?t=356232)

---

### Post by disturbedite on 2007-02-11
thanks for the effort/suggestion.  but i used the forum search (and i searched google) and couldn't find the answer.  the post you linked to is one that i found when i searched the forum and it isn't what i mean.  that is for when you compile from source, cuz you do it in this order (usually), 1. ./configure 2. make 3. sudo checkinstall.  then make your package from there.  i do that all the time.

what i wanna do is a little different.  i already have a pre-compiled binary package (tar) and wanna turn that into a deb package.  i tried pointing checkinstall to the tar package and that didn't work.  i extracted the package and pointed checkinstall to the extracted directory and that didn't work either.

---

### Post by Maestro23 on 2007-02-11
> **disturbedite said:**
> thanks for the effort/suggestion.  but i used the forum search (and i searched google) and couldn't find the answer.  the post you linked to is one that i found when i searched the forum and it isn't what i mean.  that is for when you compile from source, cuz you do it in this order (usually), 1. ./configure 2. make 3. sudo checkinstall.  then make your package from there.  i do that all the time.

what i wanna do is a little different.  i already have a pre-compiled binary package (tar) and wanna turn that into a deb package.  i tried pointing checkinstall to the tar package and that didn't work.  i extracted the package and pointed checkinstall to the extracted directory and that didn't work either.

Sorry, didn't catch the "pre-compiled" part.  Good luck man.

---

