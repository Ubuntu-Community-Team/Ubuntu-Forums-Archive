---
title: "ls options persistence"
date: 2007-07-08
forum: General Help
---

### Post by _MaDD_RuSSkiY_ on 2007-07-08
Hello,

  I'm trying to figure out if there is any way to have ls always execute with -ltr as the default options. Is there some sort of environment variable that can be set from .profile or something like that?

Thanks in advance!
Sasha

---

### Post by jyba on 2007-07-08
In your .bashrc file put this line...
```

alias ls="ls -ltr"
```

---

