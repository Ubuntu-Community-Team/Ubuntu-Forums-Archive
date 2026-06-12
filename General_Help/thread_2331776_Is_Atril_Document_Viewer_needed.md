---
title: "Is Atril Document Viewer needed ?"
date: 2016-07-25
forum: General Help
---

### Post by 4kh3RAm on 2016-07-25
Since LibreWriter can do anything that Atril does, would it be save to un-install it. ?

---

### Post by &amp;KyT$0P# on 2016-07-25
> **4kh3RAm said:**
> Since LibreWriter can do anything that Atril does, would it be save to un-install it. ?
Sure, if that's what you want to do, why not? ;)

You can get a preview of what would happen, using -s flag to apt-get, for example:
```
sudo apt-get -s purge atril
```

---

### Post by QIII on 2016-07-25
Hello!

Sure.  Probably safe enough.

Are you running out of disk space?  If not, remember that an installed application that is not running is using no resources other than a bit of disk space.

There really isn't a reason to be in a rush to remove such software.

Can you articulate a compelling reason to remove it?  If not, it might be better to simply leave it be and avoid unintended results.

---

### Post by 4kh3RAm on 2016-07-26
> **QIII said:**
> Hello!

Sure.  Probably safe enough.

Are you running out of disk space?  If not, remember that an installed application that is not running is using no resources other than a bit of disk space.

There really isn't a reason to be in a rush to remove such software.

Can you articulate a compelling reason to remove it?  If not, it might be better to simply leave it be and avoid unintended results.

QIII,

I am in no rush, but I also would benefit in not having any unnecessary programs that I will never use.

Variety can be good.

Linux often has many programs that do much the same thing.

Text editors is one example.

I do not need 4 different text editors which some distros have.

---

### Post by bapoumba on 2016-07-27
Sorry I cannot test right now. It is the document viewer for Mate, so it probably is in one of the Mate desktop meta-packages. Changing your distribution packages choices (via ppas or removing meta-packages) is something you have to keep in mind next time you upgrade. Your [dependency tree will probably thank you]("https://en.wikipedia.org/wiki/Dependency_hell").

You can see if atril has been installed on its own or if it is linked to other packages :
```
apt-cache rdepends atril
```

---

### Post by 4kh3RAm on 2016-07-27
What does this tell me ?

> apt-cache rdepends atril
atril
Reverse Depends:
  atril-dbg
  ubuntu-mate-desktop
  ubuntu-mate-core
  ubuntu-mate-cloudtop
  mate-desktop-environment
  glabels
  atril-common


I do not understand this statement.
Can you break it down to simpler statements ?

> Changing your distribution packages choices (via ppas or removing  meta-packages) is something you have to keep in mind next time you  upgrade. Your [dependency tree will probably thank you]("https://en.wikipedia.org/wiki/Dependency_hell").

---

