---
title: "Where's the documentation for insstalled APIs?"
date: 2007-11-29
forum: General Help
---

### Post by ecsd on 2007-11-29
I'm trying to install Asterisk on Ubuntu and it won't compile because (evidently) its autoconf is not written to be able to find the needed support on Ubuntu. Specifically it fails saying "no termcap support found", but it could use ncurses instead - IF IT COULD FIND IT. For some reason although ncurses5 is installed, the Asterisk autoconf-generated configure file fails to figure out that ncurses5 is available.

But then I find that although ncurses5 is installed on the system, THERE IS NO INFORMATION ABOUT IT WHATSOEVER. Given that ncurses is a well-known API, what the hell is it doing installed on my system without my being able to do "man ncurses" or "apropos ncurses"? So although I have this library installed THERE IS NO INFORMATION AVAILABLE about what functions it provides, or anything.

REALLY BAD!!

So do I have go go to GNU? Why is the BASIC INFORMATION about this thing HIDDEN or SUPPRESSED? Do I have to issue some obscure "apt-get the details please"?

Grrr.

---

