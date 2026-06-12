---
title: "Firefox 3.0 bookmark information stored where?"
date: 2008-07-01
forum: General Help
---

### Post by sdkramer on 2008-07-01
I checked 
~/.mozilla/firefox/l6ioccav.default/bookmarks.html, 
~/.mozilla/swiftweasel/l6ioccav.default/bookmarks.html,
/etc/firefox/profile/bookmarks.html,
/etc/firefox-3.0/profile/bookmarks.html

I need to know, where the information is saved when I add a bookmark. I'm running firefox 3.0 and I would assume it would be stored in my home folder somewhere, but I'm not finding any recent versions.

Thanks

---

### Post by sdennie on 2008-07-01
I think Firefox 3 has moved to sqlite to store this information (which is not human readable).  Specifically, places.sqlite seems to hold both bookmark information and history information.  You may have to export your bookmarks for a human readable format.

---

