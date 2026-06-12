---
title: "Locating Program File"
date: 2007-02-28
forum: General Help
---

### Post by Tekovro on 2007-02-28
when i go to download a file of the internet and download a file, it asks me if i want to open or save, i pick open and then choose i want to open with a other program. in this case azureus. where the heck do i locate it in the filesystem?

---

### Post by highneko on 2007-02-28
Try this maybe:
```
locate azureus
```
Did you install from the repositories?

---

### Post by Tekovro on 2007-02-28
i installed from add/remove whatever you call it

i located "azureus.desktop" but it still doesn't open with it.

---

### Post by xenmax on 2007-02-28
If azureus is already in your PATH, then ```
which azureus
``` will show where executable is.
Else, try ```
find / -name azureus
```. Add -mount option after / if you dont want it to descend to other file systems (other than / that is)

---

### Post by Tekovro on 2007-02-28
oh cool that helped. thank you very much.

is there a place where i can learn all these codes, a guide to the terminal so to speak

---

### Post by Ramses de Norre on 2007-02-28
These forums :)

---

### Post by mcduck on 2007-02-28
> **Tekovro said:**
> oh cool that helped. thank you very much.

is there a place where i can learn all these codes, a guide to the terminal so to speak
Try these:
[http://www.ss64.com/bash/]("http://www.ss64.com/bash/")
[http://www.linuxcommand.org/index.php]("http://www.linuxcommand.org/index.php")

---

