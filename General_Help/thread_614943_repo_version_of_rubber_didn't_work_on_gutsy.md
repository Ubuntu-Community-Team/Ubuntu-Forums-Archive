---
title: "repo version of rubber didn't work on gutsy"
date: 2007-11-16
forum: General Help
---

### Post by izahn on 2007-11-16
Sorry if this is the wrong place to post this. It's not a question really, just something that was annoying that I thought others might want to know about.

I'm using gedit with the LaTeX plugin. The gedit latex plugin uses rubber to compile the LaTeX source file (using, in my case, pdftex). Unfortunately this didn't work at all, and I soon discovered that rubber didn't work properly from the command line either (just says "compiling..." over and over, never finishes). After "sudo apt-get purge rubber" I downloaded and manually installed development version from the rubber web site. All works fine now. Maybe there is a problem with the version of rubber in the Ubuntu repo's?

---

