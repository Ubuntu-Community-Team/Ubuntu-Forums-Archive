---
title: "Mouse Problem"
date: 2008-05-21
forum: General Help
---

### Post by MosMusy on 2008-05-21
I edited the file which configures the mouse (xorg.conf) and I got my tablet pen working with the system, however my mouse got messed up. Now I want to restore my mouse settings to the default way, I don't need the tablet pen. How should I do that?

---

### Post by Helgiks on 2008-05-21
The easiest way would be to auto reconfigure xorg.conf, with ```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```

But this will also delete you're custom settings (if any). You're current file will get backed up.

---

### Post by MosMusy on 2008-05-21
Ignore

---

### Post by MosMusy on 2008-05-21
> **Helgiks said:**
> The easiest way would be to auto reconfigure xorg.conf, with ```
$ sudo dpkg-reconfigure -phigh xserver-xorg
```

But this will also delete you're custom settings (if any). You're current file will get backed up.

I think it fixed the problem, thank you very much.

---

