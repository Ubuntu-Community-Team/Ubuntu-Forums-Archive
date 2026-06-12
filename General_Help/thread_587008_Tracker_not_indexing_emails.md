---
title: "Tracker not indexing emails"
date: 2007-10-22
forum: General Help
---

### Post by buttari on 2007-10-22
Hi all,
I upgraded to Gutsy last Friday so I got Tracker installed on my box. The problem is that tracker has indexed only some emails. For the same search (i.e. the name of one of my coworkers), Tracker returns 6 emails, beagle 187.
Email indexing is turned on in tracker-preferences.
I can't find any log files in ~/.local/share/tracker/

Any help on this?

Thanks a bunch

---

### Post by martin_prince on 2007-10-25
Bump.

Does anybody have any ideas or suggestions on this, I too have the same problem.  I searched the forums and this was the only thread I found.  I guess I could install Beagle, but I noticed a performance hit with it.  I'd really like to see why tracker doesn't seem to index my Evolution emails.  Any help would be greatly appreciated!

---

### Post by buttari on 2007-10-25
> **martin_prince said:**
> Bump.

Does anybody have any ideas or suggestions on this, I too have the same problem.  I searched the forums and this was the only thread I found.  I guess I could install Beagle, but I noticed a performance hit with it.  I'd really like to see why tracker doesn't seem to index my Evolution emails.  Any help would be greatly appreciated!

Martin,
I managed to solve this problem by deleting the tracker database and letting it reindex everything from scratch. 
there's still something really strange in this story (see [HERE]("http://mail.gnome.org/archives/tracker-list/2007-October/msg00102.html")) but at this moment tracker is working for me and so I don't care much. As a side note, I still prefer beagle because it searches my contacts also and because tracker returns the search results apparently in random order which makes the email search pretty unuseful.

Alfredo

---

