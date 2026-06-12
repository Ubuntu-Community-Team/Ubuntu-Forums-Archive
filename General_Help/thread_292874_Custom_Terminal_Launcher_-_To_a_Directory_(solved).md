---
title: "Custom Terminal Launcher - To a Directory (solved)"
date: 2006-11-04
forum: General Help
---

### Post by Burgresso on 2006-11-04
I'm trying to make an (application?) launcher that will open terminal in a specific directory or open terminal and supply the arguments (ie, "cd directory/") to do so. Any advice?

gracias

burgresso

---

### Post by chalex on 2006-11-04
I typed "man gnome-terminal" and saw that there's a --working-directory=DIRNAME option.

Right-click on Desktop, Create New Launcher..., type "gnome-terminal --working-directory=/tmp" into the command field, and give a name to this launcher by typing something into the first field (name).

---

### Post by 23meg on 2006-11-04
```
(cd /your/desired/path ; gnome-terminal)&

```works with gnome-terminal.

---

### Post by Burgresso on 2006-11-04
Thanks for both responses. I really appreciate it.

Unfortunately, neither worked for me. I copied verbatim and tried both absolute and relative paths. Is there something obvious I may be doing?

thanks again

burgresso

---

### Post by andiii on 2006-11-04
> **Burgresso said:**
>  Is there something obvious I may be doing?

Yes:

Tell us what exactly you typed in and what exactly came out of it. :)

---

### Post by 23meg on 2006-11-05
```
(cd /your/desired/path ; gnome-terminal)&
```only works from another terminal. I just created a launcher with the command ```
gnome-terminal --working-directory=/usr
``` and it does start at /usr .

---

### Post by Burgresso on 2006-11-05
23meg:
I got your second example working. THanks, and thanks to everyone who responded to this thread.

burgresso

---

### Post by 23meg on 2006-11-05
> **Burgresso said:**
> 23meg:
I got your second example working. THanks, and thanks to everyone who responded to this thread.

burgresso
You're welcome. It's a good habit to scan through manual pages for such options, or search them with grep.

---

