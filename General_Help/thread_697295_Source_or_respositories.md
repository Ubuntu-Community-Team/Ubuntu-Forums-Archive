---
title: "Source or respositories?"
date: 2008-02-15
forum: General Help
---

### Post by enoughsaid05 on 2008-02-15
Ok, probably i need as in a different way

which is safer to install the software?

by compiling soure (i.e. tar -xvf, make, make install, etc)

or by installing straight from the respositories?

The last time i installed virtual box from repositories it destroyed my system....

so is source better?

---

### Post by santiagoward2000 on 2008-02-15
> **enoughsaid05 said:**
> Ok, probably i need as in a different way

which is safer to install the software?

by compiling soure (i.e. tar -xvf, make, make install, etc)

or by installing straight from the respositories?

The last time i installed virtual box from repositories it destroyed my system....

so is source better?

Hi!
Generally, the software on Ubuntu's repositories has been checked to see if there are any problems, and is "safer". However, it is often out of date.
Compiling from source gives you the very lastest version of that program. This may have some bugs fixes, but it may be unstable too.
I'd say Ubuntu's repositories are safer in general.

---

### Post by Tatty on 2008-02-15
It is always better to install things from the repositories if you can...  Firstly its easier, click and go, but its also much better when it comes to maintaining your software over time.

Your package manger will deal with keeping your software up to date, but also make removing software much easier - as the software can get installed across several directories on your hard disk, and maintaining it all manually can get very complex.

**EDIT:**Damn, beaten to it by someone with a better explanation! :)

---

### Post by santiagoward2000 on 2008-02-15
> **Tatty said:**
> **EDIT:**Damn, beaten to it by someone with a better explanation! :)

I won! \\:D/
But your explanation isn't bad at all.

---

### Post by mbsullivan on 2008-02-15
If you used Gentoo or FreeBSD you could do both at the same time (Portage is like a repository that gives you tarballs and makefiles, etc)...

But yeah, what the others said. If the repository version is new enough for your purposes, use it. If not, check the backports. If that isn't newer, check the Hardy repositories. Only then go for source (typically). 

The package system tracks library dependencies, but can only operate if it "knows" what is installed on your system (i.e. if you use the repositories to install things). Also, the packages in the repositories have been tested on Ubuntu, so they shouldn't thrash your system. No more than source, anyway... Some programs (like VMWare, KVM, VirtualBox, drivers, kernel stuff) may be more risky than others, but that is unavoidable.

Mike

---

