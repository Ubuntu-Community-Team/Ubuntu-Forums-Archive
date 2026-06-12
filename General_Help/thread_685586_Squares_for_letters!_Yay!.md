---
title: "Squares for letters! Yay!"
date: 2008-02-02
forum: General Help
---

### Post by Pandab34R on 2008-02-02
Okay, I was in the process of trying to fix my sound problem in ubuntu 6.06 LTS and guess what happend - nice little squares replaced every letter and number in the english alphabet! Does anyone know how to fix this? Or what may have happend? Help, it sucks!

---

### Post by neurostu on 2008-02-08
That is a fount issue. You need to reinstall your fonts. Try something like ```
$sudo apt-get install wincorefonts
``` (or something like that)

If you try
```
$aptitude search fonts
``` it will show you what packages exist. Try reinstalling your fonts and that might fix the issue.

---

