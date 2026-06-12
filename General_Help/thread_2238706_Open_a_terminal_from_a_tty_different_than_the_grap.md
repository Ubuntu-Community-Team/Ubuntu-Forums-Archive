---
title: "Open a terminal from a tty different than the graphic tty (F7)"
date: 2014-08-09
forum: General Help
---

### Post by jaimegm on 2014-08-09
Hi there

I need to open a terminal from a tty different than my graphical tty, in my graphic mode CTRL-ALT-t does not work, and there I am not able to access the launch menu.

Any ideas?

(This is in ubuntu 14.04)

---

### Post by jaimegm on 2014-08-09
Ok after posting this I found the way, this is how I open the graphical terminal from a non graphical tty:

```

DISPLAY=:0
export DISPLAY
gnome-terminal

```

---

### Post by williamdbilly on 2014-08-18
Where do you put the above code?

---

### Post by Lars Noodén on 2014-08-18
You would enter it at the shell prompt in the tty.  Log in and you'll get the prompt.

Another way to write it would be to put it on one line:

```

DISPLAY=:0 gnome-terminal

```

The environment variable $DISPLAY tells the program where to put the graphical output.  Preceding a program with an environment variable or two applies the variable only to the program launched from the same line.

---

