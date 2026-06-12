---
title: "commande line to find subdirectories only until level 3"
date: 2016-04-26
forum: General Help
---

### Post by jm-loussert on 2016-04-26
Hello

I don't know how to find (with command line or script) the sub-directories of a folder but only sub-directories level 0 to 3.
I know the "find . -type d" command but this command list all sub-directories...

Thanks in advance for your help.

---

### Post by steeldriver on 2016-04-26
You can use the -maxdepth option: from `man find`

```

       -maxdepth levels
              Descend at most levels (a non-negative integer) levels of direc&#8208;
              tories below the command line arguments.

```

---

### Post by jm-loussert on 2016-04-26
Hi,

thanks, sorry for my stupid question.

---

### Post by steeldriver on 2016-04-26
No problem - often these things are simple once you know the answer ;)

Welcome to the forums btw

---

