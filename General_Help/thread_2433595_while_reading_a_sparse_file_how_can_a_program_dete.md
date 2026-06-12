---
title: "while reading a sparse file: how can a program detect if a block ..."
date: 2019-12-21
forum: General Help
---

### Post by Skaperen on 2019-12-21
while reading a sparse file: how can a program detect if a block of all binary zeros is truly sparse in the file allocation if the file is not fully sparse?

---

### Post by TheFu on 2019-12-21
IDK, but **rsync** and **gnutar** both have code to deal with sparse files.  I've seen a patch to have rdiff-backup handle sparse files as well, but it isn't in the upstream.  Anyway, you could look at their source code.

---

### Post by Skaperen on 2019-12-22
[COLOR=#0000cd][FONT=courier new]**rsync**[/FONT][/COLOR] definitely *can* write a *sparse* file.  if it reads one, it would only need to see the block of all binary zeroes to (re)create the file as a sparse file.  i use [COLOR=#0000cd][FONT=courier new]**rsync**[/FONT][/COLOR] to make my files be sparse.  i've noticed that [COLOR=#0000cd][FONT=courier new]**rsync**[/FONT][/COLOR] does a better job the [COLOR=#0000cd][FONT=courier new]**cp**[/FONT][/COLOR] frequently, producing smaller files.

---

