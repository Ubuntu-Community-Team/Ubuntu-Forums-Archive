---
title: "program installation problem"
date: 2013-10-17
forum: General Help
---

### Post by jgw on 2013-10-17
Unity dash tells me that 7zip is available for download, ubuntu software tells me that 7zip is installed.  I then uninstalled 7zip and re-installed 7zip.  Dash still thinks its not installed, ubuntu software tells me its installed.  

Thoughts?

Thank you...........

---

### Post by oldos2er on 2013-10-18
```
which 7z
``` will return /usr/bin/7z if it's installed.

---

### Post by jgw on 2013-10-18
Thanks for the reply.

I will give this a shot although, either way, either dash is confused or ubuntu software link is confused.  Perhaps this might also tell the confused one the truth <g>

I did as suggested and it showed that it was installed.  Now, how do I get dash to recognize that as a fact (I use dash for starting programs, including this one but that won't work if it doesn't think the program is installed)

Thank you......

---

### Post by steeldriver on 2013-10-18
What actual package did you install? I think the p7zip (or p7zip-full) packages only install a command line program (7z)

---

### Post by oldos2er on 2013-10-18
> **jgw said:**
> Thanks for the reply.

I will give this a shot although, either way, either dash is confused or ubuntu software link is confused.  Perhaps this might also tell the confused one the truth <g>

I did as suggested and it showed that it was installed.  Now, how do I get dash to recognize that as a fact (I use dash for starting programs, including this one but that won't work if it doesn't think the program is installed)

Thank you......

steeldriver is right p7zip on Linux is a CLI program, but if you use dash to open file-roller (I think, it's been awhile since I've used Gnome) 7z should be available to use. file-roller acts as a GUI front-end for all the various compression/archiving CLI tools you may have installed.

---

### Post by jgw on 2013-10-20
I tried file-roller and, I think, I got the archive manager.  This is pretty strange.  I will keep messing with it.  I will also mark this solved as I suspect you folks have given me enough that I can make it all work.  Thank you.........

---

### Post by steeldriver on 2013-10-20
it should just add the 7z options to Archive Manager e.g. right click on a .7z file to open the archive

[ATTACH=CONFIG]247099[/ATTACH]

select files and right click then choose 'Compress' and '.7z' or '.tar.7z' 

[ATTACH=CONFIG]247100[/ATTACH]

---

### Post by jgw on 2013-10-21
thanks for the reply.

What I am trying to do is to extract a file from a download by sabnzb which that program failed at.  Under windows I have found that I can, often, manually extract and it works where sab did not.  My problem with archive manager is that, as far as I can tell from their documentation, does not deal with .par files (they are never mentioned).  In windows I had been using parbuddy.  I have no idea what the name of a possible corresponding program, in Ubuntu, is called.

Thoughts?

---

### Post by steeldriver on 2013-10-21
I have no experience with them, but there are a couple of available packages that seem to relate specifically to that

```

$ apt-cache show parchive
Package: parchive
Priority: optional
.
.
.
Description-en: Use PAR files to reconstruct missing parts of multi-part archives
 This utility applies the data-recovery capability concepts of RAID-like
 systems to the posting and downloading of multi-part archives on USENET by
 providing the ability to create and use redundant recovery records.  It
 supports the 'Reed-Soloman Code' implementation that allows for recovery of
 any 'X' volumes for 'X' parity volumes present.  It is popularly used on
 USENET postings, but is not limited to this use.
 .
 The Debian parchive package supports "legacy" version 1.0 PAR files.
 The Debian par2 package supports version 2.0 PAR files.

```

```

$ apt-cache show par2
Package: par2
Priority: extra
.
.
.
Description-en: Parity Archive Volume Set, for checking and repair of files
 A command line implementation of the PAR v2.0 specification.  This
 specification is used for parity checking and repair of a file set.
 If the files in the recovery set ever get damaged (e.g. when they are
 transmitted or stored on a faulty disk) the client can read the damaged
 input files, read the (possibly damaged) PAR files, and regenerate the
 original input files. Of course, not all damages can be repaired, but
 many can.

```

---

### Post by jgw on 2013-10-21
Thank you for the reply!  I will try par2 and see what happens.  I checked symantic and there was a par2 and a pypar2 which is, evidently, a gui for par2.  I will get them both - thanks again!

---

