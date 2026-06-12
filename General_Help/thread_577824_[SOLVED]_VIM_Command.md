---
title: "[SOLVED] VIM Command"
date: 2007-10-16
forum: General Help
---

### Post by btaylor101 on 2007-10-16
Does anyone know the command to make VIM open a file from the latest entry. Whenever I open a log I have to page down through to the end.

---

### Post by wayneschutz on 2007-10-16
ESC then Capital G

---

### Post by kellemes on 2007-10-16
Or *:$* enter.

---

### Post by stylishpants on 2007-10-16
To open vim to the last line in the file, use this command:

```

vim +$ filename

# Also handy: open to a certain line
vim +122 filename

# Also handy: open to the first result of a search:
vim +/searchstring filename

```

---

