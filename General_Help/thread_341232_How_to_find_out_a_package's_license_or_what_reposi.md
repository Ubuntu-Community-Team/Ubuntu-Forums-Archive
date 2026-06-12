---
title: "How to find out a package's license or what repository it came from?"
date: 2007-01-18
forum: General Help
---

### Post by minneyar on 2007-01-18
I work for a company that does a lot of software development using Linux, and our IT department just recently decided that Ubuntu is going to be our distribution of choice.  This is great and all, but now we have to work out legal issues.  One thing that would be really nice is if we could quickly find out what license a package is available under without installing it; it would also be handy if there was a way to determine what repository & section a particular package is provided by.  I've searched through the manuals for apt-get, dpkg, dpkg-query, and other, similar programs, but I haven't found anything helpful.  Does anybody know if these things are possible?

---

### Post by mcduck on 2007-01-18
'apt-cache show packagename' will tell all info about a package, as well as what repository it's in :)

like this:
```
$ apt-cache show lame
Package: lame
Priority: optional
Section: multiverse/sound
Installed-Size: 696
Maintainer: Ubuntu MOTU Developers <ubuntu-motu@lists.ubuntu.com>
Original-Maintainer: Christian Marillat <marillat@debian.org>
Architecture: i386
Version: 3.96.1-2
Depends: libc6 (>= 2.4-1), libncurses5 (>= 5.4-5)
Filename: pool/multiverse/l/lame/lame_3.96.1-2_i386.deb
Size: 266552
MD5sum: 7b67a73b7d0294a24f9d9d29519aeeec
SHA1: b9042559cb50b48546c7f0be562e0a57ce10277c
SHA256: 82b04ca74726aab446f88eb3a4156d45f83ed7c339441657f19603d373b8f543
Description: LAME Ain't an MP3 Encoder
 Lame is a program which can be used to create compressed audio files. (Lame
 aint MP3 encoder). These audio files can be played back by popular mp3
 players such as mpg123. To read from stdin, use "-" for <infile>. To write
 to stdout, use a "-" for <outfile>.
 .
 This package contains the frontend encoder binary.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu
```

---

### Post by mahiyar on 2007-01-18
Great and I thought apt-cache show showed only installed packages.

---

