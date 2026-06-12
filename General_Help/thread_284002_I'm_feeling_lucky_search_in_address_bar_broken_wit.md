---
title: "I'm feeling lucky search in address bar broken with 2.0? (Solved)"
date: 2006-10-25
forum: General Help
---

### Post by aysiu on 2006-10-25
I just "upgraded" to Firefox 2.0, and it definitely feels snappier.

One thing that's bothering me, though, is that I can't get the URL search to work. When I try to do an "I'm feeling lucky" search from the address bar, I get ```
The URL is not valid and cannot be loaded
``` I've tried searching for the correct string to put in keyword.URL in the about:config, but nothing I try works.

Has anyone else had this problem? Or is it just me?

Anyone found a solution?

---

### Post by aysiu on 2006-10-25
Never mind.

It was an extension I installed. After I removed it, everything was fine.

In case anyone wants to change the search bar back to I'm Feeling Lucky (instead of a general Google search), the string you're looking for is this: ```
http://www.google.com/search?btnI=I%27m+Feeling+Lucky&ie=UTF-8&oe=UTF-8&q=
```

---

### Post by aperomsik on 2006-10-26
Which extension was it? I have the same problem...

---

### Post by aysiu on 2006-10-26
> **aperomsik said:**
> Which extension was it? I have the same problem...
It was Tabbrowser Preferences, which I installed because TabMixPlus hadn't updated to Firefox 2.0 compatibility yet.

---

