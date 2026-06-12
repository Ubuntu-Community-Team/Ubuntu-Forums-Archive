---
title: "Thessalonica Install Problem"
date: 2005-07-01
forum: General Help
---

### Post by Karl S. on 2005-07-01
Absolute beginner here.

I'm trying to install [Thessalonica](http://www.thessalonica.org.ru/en/downloads.html#OOo) for OpenOffice. It looks like a fantastic app for those of us who have to type in foreign characters from time to time (various Middle English and French characters for me), since OpenOffice won't allow me to set up a keystroke combination (say ALT + P) to get a Middle English thorn, as MS Word does.

But I can't get it to work.

I downloaded the thessalonica2.0.uno.zip and moved this file to /usr/lib/openoffice2/presets/uno_packages. Then I go to /usr/lib/openoffice2/program and type pkgchk per the instructions at 4.9.1 in the [OpenOffice Developers' Manual](https://vheissu.mersenne.com/OO/docs/DevelopersGuide/Components/Components.htm#1+9+1+UNO+Package+Installation).

This is what I get:

>  karl@ubuntu:/usr/lib/openoffice2/program$ pkgchk
bash: pkgchk: command not found 

The OpenOffice Manual says that the pkgchk tool is part of the SDK toolset. So, not really knowing what I'm doing at this point, I used Synaptik to install free-java-sdk, kdesk-doc-html, and ladspa-sdk, just hoping that one of these would let pkgchk do its magic.

Needless to say, it didn't work.

What's my next step? Without this functionality, OpenOffice is pretty irritating to a medievalist.

---

### Post by jettjunker on 2005-09-08
I actually use gentoo with gnome 2, but I ran into the same problem.  But, maybe what I did will help you (and anyone else who stumbles here)

instead of plain old 'pkgchk -s', try:

sudo sh pkgchk -s


You may still get an error if you don't have Sun's J2SE Platform (I am using 1.4.2.08-r1)

I simply typed "emerge sun-jre-bin" (sans-quotes, of course), but the procedure may be different for you.  Good luck though, I hope I helped someone.

PS: I also have Blackdown Java Runtime Environment installed, but I am fairly sure it is unnecessary.

---

