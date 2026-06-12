---
title: "zsh not tab completing 'apt' completely"
date: 2016-07-17
forum: General Help
---

### Post by minjaedavid on 2016-07-17
i got a fresh install of ubuntu 16.04 server

```

bash$ apt [tab]
autoremove edit-sources help list remove show upgrade dist-upgrade full-upgrade install purge search update

```

```

zsh$ apt [tab] 
edit-sources full-upgrade install list remove search show update upgrade

```

so the options available on zsh completion are less.  apt command itself works fine on zsh.  I presume this is something with zsh completion system. as zsh is popular, has anyone had a similar issue?

---

### Post by minjaedavid on 2016-07-20
After examining completion scripts for zsh and bash, indeed, zsh is lacking some completion keywords as shown in the original post.

I unfortunately could not source bash completion scripts into zsh due to compatibility issues.

---

