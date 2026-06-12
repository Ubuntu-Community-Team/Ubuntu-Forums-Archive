---
title: "Possible to hide updates in Update Manager?"
date: 2008-06-11
forum: General Help
---

### Post by earther on 2008-06-11
I'm wondering if it's possible to 'hide' updates so they don't appear in the Update Manager selections. There was an option to do this with Winblows updates and it was sometimes very useful.

I'm asking in preparation for the release of FF 3 which I am not liking very much in my Virtual Box testing of Hardy.  Don't like the 'Awesome' (should be 'Awful') Bar, download manager, the new way bookmarks are handled and I am greatly annoyed that it is now difficult or impossible to associate custom favicons with bookmarks.

Since I won't be updating until there are 'improvements' or addons to remedy the 'deficiencies', I don't want to see it in the Update Manager or have it installed by accident.

BTW, still on Gutsy but if I upgraded to Hardy, I'd roll back to FF 2 first thing.

Thanks . . . earther

---

### Post by sdennie on 2008-06-11
You should be able to lock package versions in synaptic.  Select the packages you want to never upgrade (in this case, things like firefox 3 and xulrunner 1.9) and then go to Packages->Lock Version.  It's also useful to then run:

```

sudo ln -s /var/lib/synaptic/preferences /etc/apt/preferences

```

---

### Post by earther on 2008-06-13
Thanks for the tip.  I'll give it a try.

---

