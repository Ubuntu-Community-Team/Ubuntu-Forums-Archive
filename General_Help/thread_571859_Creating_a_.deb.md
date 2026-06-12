---
title: "Creating a .deb"
date: 2007-10-09
forum: General Help
---

### Post by Ryan H on 2007-10-09
I'm trying to create a .deb of Inkscape. I checked out a copy of it from SVN and proceeded to follow the directions listed [here]("http://ubuntuforums.org/showthread.php?t=51003"). I got through every thing fine, but when I finally run the command **dpkg-buildpackage -rfakeroot**, I get the error: > . . .
/usr/bin/make
make[1]: Entering directory `/home/ryan/packages/inkscape-20071009'
make[1]: *** No targets specified and no makefile found.  Stop.
make[1]: Leaving directory `/home/ryan/packages/inkscape-20071009'
make: *** [build-stamp] Error 2


I'm not sure what the exact problem is. . . It says no makefile is found? I know that I have to generate a configure file via autogen, but I already did that?

I'm currently running Gusty Gibbon x86_64.

Thank you!

-Ryan H

---

