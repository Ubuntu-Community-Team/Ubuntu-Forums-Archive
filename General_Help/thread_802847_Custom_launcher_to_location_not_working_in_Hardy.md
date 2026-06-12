---
title: "Custom launcher to location not working in Hardy"
date: 2008-05-21
forum: General Help
---

### Post by earther on 2008-05-21
In previous versions of Ubuntu, creating custom launchers to various folders worked perfectly.  In Hardy, a custom launcher to a location - like / - produces this error:

> Couldn't display "/"

There is no application installed for this type of file.


Is this a bug and is there a workaround?

Thankfully, I am just testing on a spare machine and in VirtualBox.  No way I'm going to upgrade to Hardy as this glitch would totally screw up how I customize my desktop.  Bummer.

---

### Post by diaa on 2008-05-21
Yes, this is a known issue with Hardy, I read about it before(I wish I could remember where), I'm not sure whether this is considered a bug or a change in behavior, anyways, the workaround is to use URIs instead of plain paths, so if you want to create a shortcut to /tmp folder, for example, you should set the location to
```
file:///tmp/
```

Note that spaces are replaced with *%20*

Hope this helps

---

### Post by earther on 2008-05-21
THANK YOU! that did the trick.  I spent quite some time searching before I posted and couldn't find any mention of it.  I may yet upgrade to Hardy (but not with FF3, of course - breaks too many addons).

---

