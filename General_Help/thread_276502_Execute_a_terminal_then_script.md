---
title: "Execute a terminal then script"
date: 2006-10-13
forum: General Help
---

### Post by kent41 on 2006-10-13
What I would like to do is execute a script within a terminal sesion that was started from a desktop icon.

In other words I would like to click on a desktop icon that starts a terminal session that runs a script.

Is this possible ?

---

### Post by JonahRowley on 2006-10-13
**gnome-terminal -e <command here>**

I'd supply the full path to a script not in your path.  Other than that, should be really simple.  The other possibility (I think, anyway) is to specify a shortcut to the script itself and check "Run in terminal".

---

### Post by kent41 on 2006-10-13
> **JonahRowley said:**
> **gnome-terminal -e <command here>**

I'd supply the full path to a script not in your path.  Other than that, should be really simple.  The other possibility (I think, anyway) is to specify a shortcut to the script itself and check "Run in terminal".
See next post

---

### Post by kent41 on 2006-10-13
Thanks

That works but the terminal session exit after the script runs.

can we have the terminal session stay open after it runs now it closes?

---

### Post by Rui Pais on 2006-10-13
> **kent41 said:**
> Thanks

That works but the terminal session exit after the script runs.

can we have the terminal session stay open after it runs now it closes?

With gnome-terminal thats hard...
At least that i know, you got only 2 non trivial options:
Either you set as default to all gnome-terminals to not close on exit or **(better)** you make a 2nd profile named something like keepopen (call it what you want) and set for keep open on exit and call it with:
```
gnome-terminal --window-with-profile=keepopen -e <command>
```

To set the gnome-terminal to keep open on exit go to the menu:
Edit -> Profiles
and edit default or make the new one.

If you just want a terminal, not necessarily gnome-terminal, you can use xterm directly:
```
xterm -hold -e <command>
```

Don't know if there are simpler ways...
hope that helps.

---

### Post by kent41 on 2006-10-13
> **Rui Pais said:**
> With gnome-terminal thats hard...
At least that i know, you got only 2 non trivial options:
Either you set as default to all gnome-terminals to not close on exit or **(better)** you make a 2nd profile named something like keepopen (call it what you want) and set for keep open on exit and call it with:
```
gnome-terminal --window-with-profile=keepopen -e <command>
```

To set the gnome-terminal to keep open on exit go to the menu:
Edit -> Profiles
and edit default or make the new one.

If you just want a terminal, not necessarily gnome-terminal, you can use xterm directly:
```
xterm -hold -e <command>
```

Don't know if there are simpler ways...
hope that helps.


Problem Solved::-D 

Both options work great and the xterm option must have a larger buffer because I see more data.

Thank you so much for the easy to follow help.

---

### Post by Rui Pais on 2006-10-13
> **kent41 said:**
> Problem Solved::-D 

Both options work great and the xterm option must have a larger buffer because I see more data.

yes and is lighter and can run costumized in every way and adapt to any situation (man page is huge and full of options). 

> Thank you so much for the easy to follow help.

you welcome :)

---

