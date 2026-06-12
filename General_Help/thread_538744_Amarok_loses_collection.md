---
title: "Amarok loses collection"
date: 2007-08-30
forum: General Help
---

### Post by ohzopants on 2007-08-30
FIrst:
Amarok 1.4.5
Using MySQL for collection database

Ever since I have set Amarok to load at startup, it loses my collection and needs to rescan it everytime.  However, if I don't set it to load at startup my collection is maintained just fine.  I suspect this is because the mysql service loads after amarok starts... but I'm not sure.

Can I control that somehow?

Thanks

---

### Post by forestpixie on 2007-08-30
you might try updating Amarok to 1.4.7 - I hadd a few collection issues previously which are now all resolved

---

### Post by Butthead on 2007-08-30
Hmm, did you set up a personal playlist under Amarok? :confused:

If so, it's as easy as going over to the "collection" tab menu on the left side and clicking on it to reload it.

---

### Post by ohzopants on 2007-08-31
I resolved it (sort of) myself.  It was a combination of things... my music is stored on an NTFS partition which is shared with my windows xp install.  Often when I'm in windows my system crashes (duh!) and Ubuntu can't properly mount a filesystem that was not properly unmounted by windows... therefore sometimes there were issues with the collection.

Hopefully the new video card I installed will fix my crashing issue (overheating of the onboard video I suspect).

Thanks anyway for the replies.

---

