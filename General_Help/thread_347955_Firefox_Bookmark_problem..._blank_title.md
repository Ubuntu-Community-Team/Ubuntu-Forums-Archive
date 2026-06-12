---
title: "Firefox Bookmark problem... blank title?"
date: 2007-01-28
forum: General Help
---

### Post by gsc3c on 2007-01-28
When I attempt to bookmark a site in Firefox 2.0.0.1, the "add" button has no response.  In the "Create In..." drop-down box, there is "Bookmarks", "Bookmarks Toolbar", a spacer, another "Bookmarks Toolbar" and another "Bookmarks", followed by my folders that were imported from windows Firefox 2.0.

If I try to bookmark in the second "Bookmarks" or "Bookmarks Toolbar", the bookmark is created, but without a title.

I know this behavior must be rather unique, as I cannot find a previous posting discussing it.  Any clues/hints/tips?  Thanks in advance... it's frustrating being foiled by Firefox, browsing without bookmarks.

---

### Post by Koybe on 2007-01-28
I had not exactly the same issue, but it was blanking title too. If you changed the gtk theme, try moving back. Try also changing the firefox theme. Maybe this could help.

---

### Post by gsc3c on 2007-01-28
I've also noticed that when I "customize" my firefox navigation toolbar, and move things around / remove things, it always comes back to the defaults upon restarting.

Maybe a permissions problem / problem writing to a file somewhere?  Thanks peeps.

---

### Post by gsc3c on 2007-01-28
I fixed the problem...

When I checked Tools>Error Console in Firefox, it was giving me an error in line 1 of my localstore.rdf file.  I just renamed it to localstore.rdf.2 and restarted Firefox and all is well.  Can't imagine how it became corrupt, though.

---

