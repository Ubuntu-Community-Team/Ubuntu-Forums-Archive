---
title: "HowTo: Get rid of the huge arrow icons on bookmark toolbarfolders in Firefox 3.0"
date: 2008-06-11
forum: General Help
---

### Post by quonsar on 2008-06-11
The css to do this has apparently changed since the beta version. Putting the following code in [your profile]/chrome/userChrome.css will banish the ugly things!

```
/* remove arrow from bookmark toolbar folders */
toolbarbutton.bookmark-item > .toolbarbutton-menu-dropmarker { display: none !important; }
```

---

