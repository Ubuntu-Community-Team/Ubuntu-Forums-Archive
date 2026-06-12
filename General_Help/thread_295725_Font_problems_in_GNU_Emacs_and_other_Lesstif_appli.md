---
title: "Font problems in GNU Emacs and other Lesstif applications"
date: 2006-11-08
forum: General Help
---

### Post by thom on 2006-11-08
Hi!

I did a fresh install of Edgy and everything worked just fine. Now after about a week I'm having serious problems with fonts in GNU Emacs and other Lesstif applications (like the Matlab installer). They are barely readable:

[IMG]http://beeblebrox.net/images/emacs.png[/IMG]

I didn't change any of the relevant configuration files that I'm aware of: Xorg.conf, .emacs (I did change it as you can see on the screenshot, but I renamed it to exclude it as source of error) or .Xressources.

Does anybody have the same problem?

Thanks.

--thom

---

### Post by thom on 2006-11-09
Changing my font paths in xorg.conf from
```
/usr/share/X11/fonts/
```
to
```
/usr/share/fonts/X11/
```
fixed the problem.

--thom

---

