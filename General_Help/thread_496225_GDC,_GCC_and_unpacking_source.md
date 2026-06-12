---
title: "GDC, GCC and unpacking source"
date: 2007-07-08
forum: General Help
---

### Post by gdwatson on 2007-07-08
I'm trying to [build GDC]("http://dgcc.sourceforge.net/gdc/install.html"), and to do so I need to rebuild GCC.  (GDC is a front-end for GCC.)  I was hoping to do a D-only build of GCC with a prefix in a subdirectory of my home, if I can pull it off.

But I can't even start that, because apparently I'm not smart enough to unpack the sources. ;-)  I could just untar them, but I figure there must be a better, proper Debian/Ubuntu way, given the rules.foo files I see-- and I don't know if any of those patches are significant to what I'm doing, so I wanted to be on the safe side and use the same patches as the pre-built GCC on Feisty.

I found instructions about [using dpkg-source]("http://ftp.debian.org/debian/doc/source-unpack.txt") to unpack things, but that seems to require a .dsc file, which I don't have.

Am I missing the obvious?

---

### Post by gdwatson on 2007-07-09
For what it's worth, I got it working without any patches; I just untarred the source and followed the instructions, except for two key bits.  You have to configure gcc with --disable-multilib --disable-shared for D to compile, at least on my (Feisty amd64) machine:

../gccsrc/configure --prefix=/home/gdwatson/gdc --disable-cpp --enable-languages=d --disable-multilib --disable-shared
make
make install

That did the trick.

---

