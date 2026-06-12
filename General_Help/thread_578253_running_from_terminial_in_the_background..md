---
title: "running from terminial in the background."
date: 2007-10-17
forum: General Help
---

### Post by kroiz on 2007-10-17
I though that if I open a terminal and type
```
checkgmail &
```
then close the terminal, checkgmail will still be running because of the &.
But it doesn't.
Why is that?

BTW When I do alt-F2 and type checkgmail then it runs and does not close.

---

### Post by luisromangz on 2007-10-17
The & symbol tells the terminal not no wait until the command has exited so it can give you another prompt, but the command's process is still a terminal's child process. So, closing the terminal makes all its child processes to exit.

It doesn't happen when you use alt+F2, because then the process (usually) become a child of the desktop main process, so it won't exit until you exit you session.

---

### Post by oegi on 2007-10-17
Try

$ nohup checkgmail &

from the terminal.

---

### Post by kroiz on 2007-10-17
Thank you both.
Now I understand.

---

