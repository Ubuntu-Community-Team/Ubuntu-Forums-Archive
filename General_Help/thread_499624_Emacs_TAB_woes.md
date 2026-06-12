---
title: "Emacs TAB woes"
date: 2007-07-12
forum: General Help
---

### Post by kinghajj on 2007-07-12
I want Emacs to use TABs (and *only* TABs) for indenting text. (Please, no "TABs vs Spaces" debate.) So I added these lines to my .emacs file:
```

(setq indent-tabs-mode t)
(setq-default indent-tabs-mode t)
(global-set-key (kbd "TAB") 'self-insert-command)
(setq default-tab-width 4)
(setq tab-width 4)
(setq c-basic-indent 4)

```
However, when I go to edit a C file, and type a '(' for a function call, it reverts the tab of the current line to two spaces! Further, the Ruby mode uses spaces anyway.

Is there a way to force *ALL* modes to use TABs, and to make sure that they don't automatically remove them?

---

