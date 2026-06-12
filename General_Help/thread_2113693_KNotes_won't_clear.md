---
title: "KNotes won't clear"
date: 2013-02-08
forum: General Help
---

### Post by Stonecold1995 on 2013-02-08
KNotes seems to have duplicated itself 12 or so times, and I can't  delete it.  I can right click and press "delete" on the individual  notes, but it won't actually delete.  I tried "sudo apt-get purge  knotes; sudo apt-get install knotes" but it didn't work.  It seems that  no matter what I do I'm left with 12 copies of each note I've made (for a total of 24 notes)!

How do I clear my notes if reinstalling the application doesn't work?

[[IMG]http://www.pictureshack.us/thumbs/38086_knotessssss.png[/IMG]]("http://www.pictureshack.us/images/38086_knotessssss.png")

---

### Post by Stonecold1995 on 2013-02-16
bump

---

### Post by Stonecold1995 on 2013-02-21
Anyone?

---

### Post by csillva on 2013-02-23
When you purged the file it didn't remove any configuration files in your home directory. This is a safety feature. You probably don't need to uninstall it at all, just look for the configuration directories. I don't have knotes, but just enable looking for hidden files and look under
~/.config
~/.kde4
~/.local

So long as akonadi isn't involved deleting them should be good enough.

---

### Post by Stonecold1995 on 2013-02-24
> **csillva said:**
> When you purged the file it didn't remove any configuration files in your home directory. This is a safety feature. You probably don't need to uninstall it at all, just look for the configuration directories. I don't have knotes, but just enable looking for hidden files and look under
~/.config
~/.kde4
~/.local

So long as akonadi isn't involved deleting them should be good enough.
Thank you.  I deleted ~/.kde/share/apps/knotes and it seems to be working again.

---

