---
title: "I installed LIMEWIREbut it's NO PLACE TO BE FOUND?"
date: 2008-01-26
forum: General Help
---

### Post by adn258 on 2008-01-26
I installed it from the computer packages meaning I didn't download it from their site and anyway I can't find it it isn't under accessories or internet applications or anything what should I do?

---

### Post by pytheas22 on 2008-01-26
open a terminal and type "limewire"

If that doesn't work, then it's probably not installed (how/from where did you try to install it?), and you're best off just downloading the .deb from limewire's homepage.  Or even better, use frostwire, a truly open-source version of Limewire, which I think is available in the standard repositories.

---

### Post by gvartser on 2008-01-26
```
dpkg-query -L limewire
```

Will display installed files inc path to the files owned by the limewire package.

/g

---

