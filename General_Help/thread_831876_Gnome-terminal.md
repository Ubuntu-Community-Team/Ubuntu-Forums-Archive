---
title: "Gnome-terminal"
date: 2008-06-17
forum: General Help
---

### Post by Joe Momma on 2008-06-17
Does anyone know if it is possible to run 2 separate Gnome-terminal windows with 2 separate PIDs?  I can open multiple windows but they all seem to be the same process.

---

### Post by skymera on 2008-06-17
Why would you want to?

Just curious i open several terminals fine.

---

### Post by rraj.be on 2008-06-17
You cant do that one.

```
Each shell is isolate blocks of environment.
```

Each shell will be holding its own attributes and environment facts.

But i had a hope at the corner that you can make some IPC to work like that.
But not sure.

---

### Post by Joe Momma on 2008-06-17
I want to do it because I need to make gnome terminal a child process of another application so that its environment inherits certain encryption properties.  But when I attempt to open gnome terminal within the other application, it ignores my wrapper and simply opens a window as part of the default process with default properties.

In 7.10 it worked fine, but after the "upgrade" it does not.  I can open xterm and konsole as child processes but not gnome-terminal, which is my terminal of choice.

Edit:

ok, so I found that the flag --disable-factory will open a new process (with a new PID) instead of just extending a previous one, but the terminal still is not inheriting the environment from the application that is calling 'gnome-terminal'

---

