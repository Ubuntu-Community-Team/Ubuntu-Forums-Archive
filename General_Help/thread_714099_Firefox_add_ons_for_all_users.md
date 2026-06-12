---
title: "Firefox add ons for all users"
date: 2008-03-03
forum: General Help
---

### Post by artti on 2008-03-03
Is it possible to install firefox add-ons for all users?

---

### Post by Nepherte on 2008-03-03
I think Firefox add ons are stored in the profile you use. If you create a profile that everyone can access and use, you'll have the same add ons. But then again, everything would be shared like history, bookmarks, ...

To access the profilemanage, close all firefox windows and type in the consoler:
```
firefox -ProfileManager
```

---

### Post by aysiu on 2008-03-03
I would imagine something like this could work: ```
sudo mv /usr/lib/firefox/extensions /usr/lib/firefox/extensions.old
sudo ln -s ~/.mozilla/firefox/*profilename*/extensions /usr/lib/firefox/extensions
sudo chmod -R 755 /usr/lib/firefox/extensions
``` *profilename* usually looks like gobbledygook, something like *6z7u82ub.default*

---

