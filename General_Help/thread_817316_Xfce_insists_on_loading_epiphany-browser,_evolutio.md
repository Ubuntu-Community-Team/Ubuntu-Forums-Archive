---
title: "Xfce insists on loading epiphany-browser, evolution, xterm whenever I log in."
date: 2008-06-03
forum: General Help
---

### Post by goldust on 2008-06-03
I don't want this. I've exhausted every effort.

---

### Post by Dr.Ninethousand on 2008-06-03
maybe an obvious question, but did you try closing everything and then logging out and checking the 'save this session for future log-ins' box?

---

### Post by goldust on 2008-06-03
Thank you for responding.
Yes, I closed everything and I never have save session checked.

---

### Post by Dr.Ninethousand on 2008-06-04
possibly the first time you logged out it was checked, since it is by default..  so try closing everything for a clean desktop, then checking 'save  for future' when you log out, so that a clean desk will be saved..  then uncheck it again after that..

---

### Post by sisco311 on 2008-06-04
or delete the config files from a terminal:
```
rm -r ~/.cache/sessions/*
```

---

### Post by Sef on 2008-06-04
> rm -r ~/.cache/sessions/*

Be real careful, if you use that.  If you do it wrong, you run the risk of needing to reinstall Ubuntu.  It would be best to avoid using it.

---

