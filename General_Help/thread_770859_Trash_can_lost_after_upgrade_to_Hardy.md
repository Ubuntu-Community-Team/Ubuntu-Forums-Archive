---
title: "Trash can lost after upgrade to Hardy"
date: 2008-04-27
forum: General Help
---

### Post by lenx on 2008-04-27
I upgraded from 7.10 to 8.04 today, and my recycle bin is lost! I tried to add it by right clicking on the panel, but when i add it nothing happens.

My deleted files still appear in home/user/.local/share/Trash
but where is that bin?? is there any other way to 'force' it back on my panel?

---

### Post by rturner on 2008-04-27
try typing in a terminal:
gconf-editor /apps/nautilus/desktop

See if ticking the trash icon visible box brings it back.

---

### Post by spike_naples on 2009-04-27
So simple the solution to my same problem. Thanks!

---

### Post by cfurlin on 2009-04-28
> **lenx said:**
> I upgraded from 7.10 to 8.04 today, and my recycle bin is lost! I tried to add it by right clicking on the panel, but when i add it nothing happens.

My deleted files still appear in home/user/.local/share/Trash
but where is that bin?? is there any other way to 'force' it back on my panel?

I highly doubt your trash can is lost. It probably knows exactly where it is. You however, don't. Try using conf manager and pointing to apps > nautilus > desktop and checking 'trash_can_visible'

---

