---
title: "Save terminal commands"
date: 2007-04-05
forum: General Help
---

### Post by kryos on 2007-04-05
>How would one copy previous terminal commands and output to a file?

History command.  Go figure!
Thanks to all.

---

### Post by 23meg on 2007-04-05
Check out the *history* command.

---

### Post by irwa82 on 2007-04-05
Hi,

look in the ~/.bash_history file 

e.g.

less ~/.bash_history

---

### Post by Sencer on 2007-04-05
> **kryos said:**
> How would one copy previous terminal commands and output to a file?  I can up/dn arrow through them but only copy 1 line at a time.  There must be a better way.  I would like to know where I've been/what I've done.

Is the output of the commands important?

Well, if you know in advance, you can always use "script" to save at terminal session to a text file.

Or you can maximize the terminal window, use "ctrl -" to reduce the font size (so more lines fit on a screen-full), mark all the lines with the mouse, and then use "ctrl+shift+c" to copy it, and then switch to gedit and paste it.

---

