---
title: "URL's in openoffice docs open in konqueror instead of firefox"
date: 2007-03-29
forum: General Help
---

### Post by bkj1 on 2007-03-29
how do i get openoffice to open url's in my default browser firefox instead of konqueror?

thanks in advance

---

### Post by bkj1 on 2007-03-29
bump

---

### Post by gila_monster on 2007-03-29
Hi.

Not sure if this will work (because I don't know if OOO has its own settings, or is using x-www-browser), but try the following at a terminal:

update-alternatives --config x-www-browser


If x-www-browser is set to konqueror, that's what the system will tend to use. Set it to firefox (should be one of the options shown) and try it.

Hope that works for you.

---

