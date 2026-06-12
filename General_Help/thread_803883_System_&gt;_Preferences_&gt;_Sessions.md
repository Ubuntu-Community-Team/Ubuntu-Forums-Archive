---
title: "System &gt; Preferences &gt; Sessions?"
date: 2008-05-22
forum: General Help
---

### Post by agorex on 2008-05-22
Hello! I'm wondering... which files does gnome-session modify?

Thanks.

---

### Post by shifty_powers on 2008-05-22
xorg.conf off the top of me head.

probably wrong though knowing me ;)

---

### Post by agorex on 2008-05-22
The answer is in the man page, sorry.

```
gnome-session uses the contents of the ~/.gnome/session file for starting up as specified by the "Current Sesssion" key in the ~/.gnome/session-options file. Various default values are provided in case the file entry does not exist.

If the session file does not exist, gnome-session will use the contents of the /usr/share/gnome/default.session file.
```

---

