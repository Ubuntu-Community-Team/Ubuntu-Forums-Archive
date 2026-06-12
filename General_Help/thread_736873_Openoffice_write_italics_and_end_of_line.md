---
title: "Openoffice write italics and end of line"
date: 2008-03-27
forum: General Help
---

### Post by Gavla on 2008-03-27
Anybody else experience a bug in Openoffice writer where if you're writing with italics and reach the end of the line, you can't turn italics off?

---

### Post by Gavla on 2008-03-27
I misdiagnosed that. It can also happen in the middle of a line.

---

### Post by MarkusRTK on 2008-04-14
Hi Gavla--
I was having the same problem. Seems it's a known bug in OpenOffice 2.3.0 (which is the version still in the Gutsy repositories). Recent updates to OpenOffice have fixed it, so the solution is to update to a newer version. Unfortunately you cannot do that using apt-get/synaptic (afaik).

Instead, you can download the newer OpenOffice here -- [http://download.openoffice.org/other.html](http://download.openoffice.org/other.html) -- choose "Linux DEB" for whichever language you prefer. Installation is simple, instructions can be found at [http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68](http://user.services.openoffice.org/en/forum/viewtopic.php?f=16&t=68) (the short version is, uninstall all your preexisting OpenOffice packages first, then install all the debs included in that tarball). That ought to solve your problem, plus you'll have a shiny new (and constantly updating) OpenOffice!

Hope that helps

---

