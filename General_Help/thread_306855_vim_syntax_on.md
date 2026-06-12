---
title: "vim syntax on"
date: 2006-11-25
forum: General Help
---

### Post by jordilin on 2006-11-25
I'm using Edgy with vim 7.0. If I enable syntax on in the /etc/vim/vimrc file (just uncommenting the "syntax on line) then I get the following error when trying to open a file with vim:
> Error detected while processing /usr/share/vim/vimrc:
line   20:
E319: Sorry, the command is not available in this version:  syntax on
Press ENTER or type command to continue

any ideas?

---

### Post by taurus on 2006-11-25
Maybe you need to install the full version of vim!!!

```
sudo aptitude update
sudo aptitude install vim-full
```

---

### Post by jordilin on 2006-11-25
Thank you very much taurus, that did the trick :mrgreen:

---

### Post by taurus on 2006-11-25
> **jordilin said:**
> Thank you very much taurus, that did the trick :mrgreen:
=D>

---

