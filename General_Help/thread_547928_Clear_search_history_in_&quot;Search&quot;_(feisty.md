---
title: "Clear search history in &quot;Search&quot; (feisty)"
date: 2007-09-10
forum: General Help
---

### Post by mikeize on 2007-09-10
So I figured out how to clear the desktop search history (right click>clear), but when I do a file search from Places>Search for files...  all my old searches are there in the dropdown searchbar.  Is there anyway to clear this out?  Would be great to be able to turn it off completely, but at the very least I'd like to find the "clear search history" option.  Anyone?  Thanks.

-mike

---

### Post by jamvegan on 2007-09-10
You can get rid of the history like this:
```
rm ~/.gconf/apps/gnome-settings/gnome-search-tool/%gconf.xml
```
You then need to log out and log back in to no longer see the history in Places->Search for Files...

I don't know if this is the preferred way, but it will do it (I just tested it).  Don't know how to turn it off, though.

---

### Post by mikeize on 2007-09-11
thanks jamvegan!

i was hoping for a "gui solution", but I'll give this a shot tomorrow.  ubuntu vegan warrior!

-mike

---

