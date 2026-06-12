---
title: "How to make mouse-wheel work in emacs in ubuntu?"
date: 2007-05-12
forum: General Help
---

### Post by yinglcs2 on 2007-05-12
How to make mouse-wheel work in emacs in ubuntu? 

I am coming from Fedora. I think mouse wheel works in emacs there, how can I make it work in ubuntu?

Thank you.

---

### Post by jbro on 2007-05-13
Hmm, I'm using Feisty and emacs-snapshot-gtk, and the mouse wheel just works. If it is not working for you, perhaps try "M-x mouse-wheel-mode" while in emacs and if your mouse wheel starts to work then add the line ```
(mouse-wheel-mode t)
``` to your .emacs file.

Good luck,
jbro

---

### Post by felixnine on 2008-01-01
for the longest time

```
(mouse-wheel-mode)
```

was working fine, then it wasn't. i could do M-x mouse-wheel-mode in emacs, but not at startup. why does the trailing 't' make it work?

(sorry, i'm way too lazy to look into elisp to figure it out)

---

### Post by vambo on 2008-01-01
The 't' sets ot true

---

### Post by felixnine on 2008-01-01
ha! that was easy.

---

