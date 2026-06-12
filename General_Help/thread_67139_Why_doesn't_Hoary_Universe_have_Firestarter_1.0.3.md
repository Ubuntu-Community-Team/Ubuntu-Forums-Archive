---
title: "Why doesn't Hoary Universe have Firestarter 1.0.3?"
date: 2005-09-19
forum: General Help
---

### Post by rlcarr on 2005-09-19
The firestarter home page says that Firestarter 1.0.3 is out and is available to Ubuntu Hoary users just by using apt-get.  However, when I "apt-get update" and then "apt-get install firestarter", it can only find 1.0.1, which I already have installed.

Interestingly, if you go to the repository and look in the relevant pool directory, you'll see that a 1.0.3 firestarter .deb is there:
   [http://us.archive.ubuntu.com/ubuntu/pool/universe/f/firestarter/](http://us.archive.ubuntu.com/ubuntu/pool/universe/f/firestarter/)
 
However, universe's Packages.gz still lists 1.0.1.  Is there a specific reason for this, or are the Package.gz update people just running behind?

---

### Post by John.Michael.Kane on 2005-09-19
use synaptic search for firestarter and you should get the newest one..

---

### Post by ranf on 2005-09-19
[QUOTE=rlcarr]Interestingly, if you go to the repository and look in the relevant pool directory, you'll see that a 1.0.3 firestarter .deb is there:
   [http://us.archive.ubuntu.com/ubuntu/pool/universe/f/firestarter/](http://us.archive.ubuntu.com/ubuntu/pool/universe/f/firestarter/)
 
However, universe's Packages.gz still lists 1.0.1.  Is there a specific reason for this, or are the Package.gz update people just running behind?[/QUOTE]

The pool is used for Hoary and Breezy (just like it is with Debian stable/unstable/testing).

Breezy has version 1.0.3. See:
[packages.ubuntu.com](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=firestarter&searchon=names&subword=1&version=breezy&release=all)

---

### Post by rlcarr on 2005-09-19
[QUOTE=ranf]The pool is used for Hoary and Breezy (just like it is with Debian stable/unstable/testing).[/QUOTE]

Ah!  Thank you!  That makes sense.

So it looks like the error was on the Firestarter home page, where it claimed that 1.0.3 was part of the Hoary universe but apparently instead should say that it's part of the Breezy universe.

Thanks!

---

