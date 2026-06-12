---
title: "Hide pathnames in the terminal"
date: 2007-01-18
forum: General Help
---

### Post by earobinson on 2007-01-18
Currently I am trying to work in "earobinson@minusone:/media/data/school/csc369h1/os161/src/kern" But this takes up almost all 80 charters of my terminal. Is there any setting I can change to make it so that its don't displayed.

I'm using the xfce-terminal, but would be happy to use the gnome-terminal

Thanks

---

### Post by taurus on 2007-01-18
Actually, it's in ~/.bashrc (or even /etc/bash.bashrc).  Look at the **PS1=** line.

---

### Post by JamieC on 2007-01-18
You could try using a symlink, type the following in terminal:
```

ln -s /media/data/school/csc369h1/os161/src/kern/ /kern
cd /kern

```

---

### Post by earobinson on 2007-01-18
> **taurus said:**
> Actually, it's in ~/.bashrc (or even /etc/bash.bashrc).  Look at the **PS1=** line.
I dont want to edit for all terminals just for one terminal.

I would much rather edit PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: ${PWD/$HOME/~}\007"' manualy, but a ```
 export PROMPT_COMMAND='echo -ne "\033]0;${USER}@${HOSTNAME}: \007"' 
``` dose not solve my problem

---

