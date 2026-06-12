---
title: "cd-rom and hdd constantly being accessed"
date: 2005-10-31
forum: General Help
---

### Post by demiurge on 2005-10-31
No sure if this is the right forum but I have a very strange question.
Just did a fresh install of breezy on my Fujitsu S6120 and for some
reason my removable cd is constantly being accessed (the cd-rom 
icon on the computer is constantly flashing but drive not actually 
spinning since it's empty), I removed the drive and this hard locks 
the computer. In fact my hdd is also being accessed every 5 second
so it couldn't spin down, but after I started laptop-mode it went back
to normal. Is there some new process that's doing this? Everything
was smooth under 5.04.

Also the battery meter doesn't work anymore and that's a bit annoying.

EDIT: well after a long of tinkering the culprit was hald-addon-storage,
stopping it solves the problem. Now if only I could get battery going...

---

