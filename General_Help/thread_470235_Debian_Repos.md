---
title: "Debian Repos?"
date: 2007-06-10
forum: General Help
---

### Post by moore.bryan on 2007-06-10
[I]practical+philosophical question for the class:
practical: i'm trying to install xmms2, but don't feel like going through the hassle of individually installing a million packages; debian has xmms2 in its repos...
philosophical: if ubuntu is debian-based, why shouldn't we put debian repos in our sources.list?

[/I]

---

### Post by CocoAUS on 2007-06-10
I'm not sure if that was one question or two.

Either way, putting Debian repos in your sources.list will probably cause you all sorts of headaches.  Ubuntu has (for some reason) seemingly gone out of their way to make sure that their repos won't work with Debian's.  In fact, this is one of the big complaints the Linux community has about Ubuntu.  Technically speaking, there's no reason why Ubuntu wouldn't keep everything compatible with Debian.  We often wonder why Canonical shafted Debian like they did.

Anyhoo, you could try simply downloading an xmms2 Debian package and then letting dpkg figure things out.  Since it's only one program, it might work out for you.

---

### Post by moore.bryan on 2007-06-10
[I]i'm not sure either...

i figured the same as you and hoped aptitude would be as brilliant as usual; alas, it was only "gifted" and unable to resolve my issues.  for anyone keeping score, though; removing a dysfunctional xmms2 is worth -310.  

:-)
[/I]

---

