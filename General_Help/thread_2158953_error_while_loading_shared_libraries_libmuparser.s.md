---
title: "error while loading shared libraries: libmuparser.so.2: wrong ELF class: ELFCLASS64"
date: 2013-07-01
forum: General Help
---

### Post by Bladeforce on 2013-07-01
Hi I am getting this error in Ubuntu 13.04 x64

error while loading shared libraries: libmuparser.so.2: wrong ELF class: ELFCLASS64

Could anyone point me in the right direction to help with this error please?

Many thanks

---

### Post by dino99 on 2013-07-01
see details inside : /usr/share/doc/libmuparser-dev/changelog.Debian.gz

---

### Post by Bladeforce on 2013-07-01
I dont have a libmuparser-dev but i do have a libmuparser2 dir and this is the contents of that file

muparser (2.1.0-3) unstable; urgency=low

  * Merge from experimental to unstable.
  * Added symbols file, using pkgkde-symbolshelper to manage c++
    symbols
  * D S-V 3.9.3, no changes

 -- Scott Howard <showard@debian.org>  Mon, 26 Mar 2012 16:19:32 -0400

muparser (2.1.0-2) experimental; urgency=low

  * Fix FTBFS on GNU/Hurd (Closes: #533817).
    debian/patches/FTBFS_hurd.patch

 -- Scott Howard <showard@debian.org>  Sun, 08 Jan 2012 17:55:15 -0500

muparser (2.1.0-1) experimental; urgency=low

  * New upstream release, updated debian/watch
    - soname reset to "2", previously it was "0" for all releases
  * Corrected include directory in pkgconfig file (LP: #418081)

 -- Scott Howard <showard@debian.org>  Mon, 19 Dec 2011 18:23:41 -0500

muparser (1.34-2) unstable; urgency=low

  * Team upload.
  * Debian specefic SONAME libmuparser.so.0debian1 until upstream resets
    versions after next release (Closes: #606120)
    - Binary package renamed libmuparser0debian1, and moved to optional
      priority
  * Moved to Vcs-Git

 -- Scott Howard <showard@debian.org>  Thu, 07 Apr 2011 22:48:22 -0400

muparser (1.34-1) unstable; urgency=low

  * New upstream release.
  * Bump standards version to 3.9.1
  * Switch to dpkg-source 3.0 (quilt) format

 -- Gudjon I. Gudjonsson <gudjon@gudjon.org>  Sun, 05 Dec 2010 13:13:16 +0100

muparser (1.32-1) unstable; urgency=low

  * New upstream release
  * Bump standards version to 3.8.4
  * Add misc dependency
  * Switch to dpkg-source 3.0 (quilt) format

 -- Gudjon I. Gudjonsson <gudjon@gudjon.org>  Tue, 13 Apr 2010 22:09:31 +0200

muparser (1.30-1) unstable; urgency=low

  [ Gudjon I. Gudjonsson ]
  * New upstream release
  * Bump standards version to 3.8.3, no changes needed
  * Remove patch 01_fix_ftbfs_gcc4.3.diff, not needed anymore
  * Remove quilt dependency, no patces.
  * Add Vcs fields for debian-science
  * Copy config.{sub,guess} to build/autoconf at build time (Closes: 536116)

  [ Andreas Tille ]
  * Group maintenance in Debian Science tesm, added myself as Uploader
  * debian/control: library package inherits section from source
  * debian/copyright: s/(C)/©/
  * mv debian/muparser.doc-base debian/libmuparser-doc.doc-base
    (doc-base works per binary package
  * debian/libmuparser-doc.doc-base:
    - Fixed Spacing
    - Section: Science/Mathematics (according doc-base manual section 2.3.3)

 -- Andreas Tille <tille@debian.org>  Tue, 17 Nov 2009 21:33:02 +0100

muparser (1.28-3) unstable; urgency=low

  * Fix prefix in rules file. (Closes: #518470)
  * Bump Standards-Version to 3.8.0, no changes needed.
  * Bump compat/debhelper to 7.
  * Fix watch file.
  * Change from dh_clean -k to dh_prep.
  * Add version to Debian packaging license, GPL v2.

 -- Gudjon I. Gudjonsson <gudjon@gudjon.org>  Sat, 07 Mar 2009 11:00:05 +0100

muparser (1.28-2) unstable; urgency=low

  * Add a patch to fix compilation with gcc-4.3. (Closes: #455642)
  * Bump Standards-Version to 3.7.3.
  * Add a watch file.
  * Use Homepage field.
  * Bump compat/debhelper to 6.
  * Build with --as-needed linker flag.

 -- Gudjon I. Gudjonsson <gudjon@gudjon.org>  Sun, 27 Jan 2008 22:59:01 +0100

muparser (1.28-1) unstable; urgency=low

  * New upstream release.
  * Switch to quilt patch system.
  * Replace deprecated Source-Version by binary:Version.
  * Add some configure options:
    * --enable-shared=yes
    * --enable-samples=no
    * --enable-debug=no

 -- Gudjon I. Gudjonsson <gudjon@gudjon.org>  Sun, 29 Jul 2007 15:23:14 +0200

# For older changelog entries, run 'apt-get changelog libmuparser2'

---

### Post by mc4man on 2013-07-01
When is this error occurring?
Sounds like some app needing the i386 version of libmuparser & you only have the 64 bit version installed

If that's the case then run this, just a simulation, nothing happens
```
sudo apt-get [COLOR="#FF0000"]-s[/COLOR] install libmuparser2:i386
```

If all seems ok then re-run command but remove the [COLOR="#FF0000"]-s[/COLOR]

---

### Post by Bladeforce on 2013-07-01
I'm trying to run an emulator called Raine. I tried your command then tried it without the "-s" everything seem to go fine except it wanted to remove raine. So i did then reinstalled raine and i'm back with the same error.

Edit

Sorry I managed to get it sorted by manually installing the emulator by following this post

[http://rainemu.swishparty.co.uk/msgboard/yabbse/index.php?topic=1845.0](http://rainemu.swishparty.co.uk/msgboard/yabbse/index.php?topic=1845.0)

Thank you again

---

### Post by mc4man on 2013-07-01
What a pita - 
assuming you're using the Debian package (tried 0.6.2.0 from [http://rainemu.swishparty.co.uk/html/archive/debian/dists/unstable/main/binary-amd64/](http://rainemu.swishparty.co.uk/html/archive/debian/dists/unstable/main/binary-amd64/)

Installed it with gdebi so it would resolve deps - installed what is in screen 1. Notice only a couple of i386 packages

Then each time I ran raine from terminal something wouldn't be found (I think if wine was installed the list would be shorter. Worked thru them all & it now opens - screen 2

list -  (each one installs a bunch of other packages
libpng12-0:i386
libgl1-mesa-glx:i386
libglu1-mesa:i386
libmuparser2:i386
libsdl-image1.2:i386
libsdl-ttf2.0-0:i386
libsdl-sound1.2:i386

(note - happened to be on a 13.10 install, should be the same names for 13.04, otherwise don't know

---

