---
title: "Broken packages - liblzma5 is broken"
date: 2013-11-12
forum: General Help
---

### Post by euseinaoseithelost on 2013-11-12
Well, I tried to install codelite and it depends of liblzma5, but Ubuntu already have this lib, however, my lib version is *5.1.1alpha+20110809-3_i386*
and codelite needs the *5.1.1alpha+20120614-1_i386* version.


okay, I got the "*20120614-1*" version ( I downloaded the deb package from some site ) and I tried to install it, but the package broke and I cannot do anything.
Someone help-me? please (and thanks (I want not reinstall my system) ).

---

### Post by euseinaoseithelost on 2013-11-12
oh, can close the topic, I found the solution:
[COLOR=#333333][FONT=Ubuntu Mono]$ dpkg --force-depends -P liblzma5[/FONT][/COLOR]

---

