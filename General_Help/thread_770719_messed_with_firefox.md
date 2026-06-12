---
title: "messed with firefox"
date: 2008-04-27
forum: General Help
---

### Post by ELD on 2008-04-27
I just noticed i don't get the "this page requires a plugin blah" bar come up anymore? Have i accidently deleted something in firefox 3 that it needs?

Like i view a page that needs flash and i don't get anything?

---

### Post by sizzam on 2008-05-29
Check this setting:

In the address bar in Firefox type: 
```
about:config
```

Click the "I'll be careful, I promise!" button.

In  "Filter", enter:
```
plugins.hide_infobar_for_missing_plugin
```

This should be set to False so that the infobar displays when you are missing a plugin.

---

