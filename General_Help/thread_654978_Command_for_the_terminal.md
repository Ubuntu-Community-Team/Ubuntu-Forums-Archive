---
title: "Command for the terminal"
date: 2007-12-31
forum: General Help
---

### Post by geovino on 2007-12-31
I'm trying to create a launcher in Xubuntu for the terminal. Somebody mentioned gnome-terminal , but that doesn't work. 

What is the command for the terminal (konsole)?

---

### Post by taurus on 2007-12-31
Try xterm (or even Terminal).  Konsole will work if you have KDE installed.

---

### Post by geovino on 2007-12-31
Thanks, that works, but it brings up a black background with white letters which is the opposite of my other terminal of the menu list. Maybe this is another terminal?

---

### Post by taurus on 2007-12-31
Are you talking about xterm or Terminal?

```
xterm -bg white -fg black
```

---

### Post by |Porsche on 2007-12-31
The command you are looking for is ```
xfce4-terminal
``` to creat the launcher.

---

### Post by geovino on 2007-12-31
> **|Porsche said:**
> The command you are looking for is ```
xfce4-terminal
``` to creat the launcher.

That's the one! :)

Thanks

---

