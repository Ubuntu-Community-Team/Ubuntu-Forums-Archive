---
title: "Texinfo docs?"
date: 2007-03-08
forum: General Help
---

### Post by x1a4 on 2007-03-08
Hi,

Many tools use texinfo for documentation with the man pages providing only a cursory glance, yet my copy of Xubuntu (Edgy) didn't come with *info* nor info pages installed.  I've installed *info* and *-doc packages for everything I have but it simply isn't enough.

Many tools' man page refers me to *info <whatever>* for details, yet when I run it I just get the man page.  

Is there a separate repository, or perhaps a specific package naming convention I can do a search on, or something, I can use/do to get the missing texinfo documentation?  

Thank you.

---

### Post by lhtown on 2007-03-08
I am not exactly sure what you are referring to. What programs are you looking for information on?

It sounds to be like maybe you didn't install all of the support dependencies to your program. For instance, with python, you might also have to install the python2.54-doc package to get all of the help documentation.

I usually find that the man pages are pretty complete if somewhat cryptic for most command line programs. Of course programming languages are a big exception.

---

### Post by x1a4 on 2007-03-08
I'm referring to info files which are stored in /usr/share/info and typically viewed using the GNU Info Documentation Browser (*info*).  I've spent quite a bit of time ensuring I have installed all *-doc packages for everything I have on my system, yet many tools don't have corresponding info documentation.

For example, when I run *info coreutils chmod* I get the chmod man page instead of the info page, yet I have the coreutils package installed.

---

