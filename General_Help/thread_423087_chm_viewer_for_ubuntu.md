---
title: "chm viewer for ubuntu"
date: 2007-04-25
forum: General Help
---

### Post by Qwerty9119 on 2007-04-25
Hey all I'm trying to install a chm viewer for ubuntu via (as root):

apt-get install gnochm

or 

apt-get install xchm

Both results in:

Package gnochm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gnochm has no installation candidate


Any suggestions and anybody know where I can get a .chm viewer?
Thanks Q

---

### Post by beerorkid on 2007-04-25
I know [automatix]("http://www.getautomatix.com/") will install it, but I have no fricking clue what a chm is ;)

EDIT ahhhhhhhhhhhhhhhhhhhhh [http://en.wikipedia.org/wiki/Microsoft_Compiled_HTML_Help](http://en.wikipedia.org/wiki/Microsoft_Compiled_HTML_Help)

> This format was originally intended only for encoding help files, but other uses have since been found. It is very handy for packing saved HTML pages in one compact and browsable archive and for creating compact e-books. Some people use it to keep personal notes, because it can organize them in an ordered hierarchical table and allows quick text searching. There is a Firefox extension capable of viewing CHM files

---

### Post by rsambuca on 2007-04-25
I just tried installing gnochm via Synaptic and it installed fine.  Took less than 30 seconds, in fact.

Just go to System -> Adminstration -> Synaptic Package Manager

do a search for gnochm, click install.

---

### Post by Qwerty9119 on 2007-04-26
I've gone to Synaptic Package Manager, click the search button, it still doesn't show gnochm. When was the last time anybody successfully installed this?

Thanks,

Q

---

### Post by rsambuca on 2007-04-26
Go to System -> Administration -> Software Sources and enter your password.

Make sure you have main, universe, restricted and multiverse are checked.

Then close the software sources, and try Synaptic again after hitting the Reload button.

---

### Post by Qwerty9119 on 2007-04-26
That did the trick!

Thank you,

Q

---

### Post by jrock2004 on 2007-04-26
just to let you know xchm installed fine for me but congrats on fixing your issues

---

