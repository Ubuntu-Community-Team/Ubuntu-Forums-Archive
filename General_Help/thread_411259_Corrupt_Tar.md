---
title: "Corrupt Tar"
date: 2007-04-16
forum: General Help
---

### Post by markusfarkus on 2007-04-16
I have a corrupt tarball.  It is only 97M.  Does anyone know of some free/open source tools for restoring a corrupt tarball?  I can find some commercial products, but some are as expensive as $800.  

Any ideas?

---

### Post by rmemm on 2007-04-16
GNU tar itself does have some options that are suprose to help -- but they may not work for y ou.  Check out the full tar options list particularly --ignore-zeros may help.  There are a variety of options also to see where the file goes bad and only restore parts of the file.

Rob

---

### Post by rkathey on 2007-10-24
I tried upgrading from 7.04 to 7.10 and the darn thing hung halfway through.  I created a boot CD, backup up my home dir to a tgz file.  When I untar, things scream along.  I see the files extracting then I get this

[INDENT]media/disk/home/rkathey/Win32-iq127__dev.zip

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: media/disk/home/rkathey/.blender/scripts: Directory renamed before its status could be extracted
tar: media/disk/home/rkathey/.blender: Directory renamed before its status could be extracted
tar: media/disk/home/rkathey/g2: Directory renamed before its status could be extracted
tar: Error is not recoverable: exiting now
[/INDENT]
Here's the options I tried with untar.

tar --ignore-failed-read -xzvif backup2.tgz

Any other suggestions?

---

### Post by rkathey on 2007-11-05
Here's what I finally did to fix it.

[http://texasdrifter.blogspot.com/2007/10/failure-to-recover.html](http://texasdrifter.blogspot.com/2007/10/failure-to-recover.html)

Basically you download gzrecover, compile it and run it against the corrupt tarball.

---

