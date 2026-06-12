---
title: "[SOLVED] gnome-terminal question ??"
date: 2008-04-01
forum: General Help
---

### Post by LinuX-M@n1@k on 2008-04-01
I want gnome-terminal to autostart and show a fortune, then, when I hit enter (or not) to get back to the command line....
With "gnome-terminal -x fortune &" it starts and shows the fortune (I edited the profile not to exit the terminal after the command exits), but I can't go back to the command line and use it....
help?

---

### Post by warp99 on 2008-04-01
Use the double '&&' so that the fortune program runs then terminates and goes back to the command line. You may need to use the -w switch on fortune to display a set amount of time before the program terminates:

[http://linux.die.net/man/6/fortune](http://linux.die.net/man/6/fortune)

Edit:

That should be '&&;' not '&&'

---

### Post by LinuX-M@n1@k on 2008-04-01
not working :( if i use "gnome-terminal -x fortune &&" it waits me to type the next command on the next line because of the && ....
```
boris@linux:~$ gnome-terminal -x fortune &&
> 
```
my idea is to open a gnome-terminal with a fortune in it and continue working with it... not closing it and going to the first terminal where i executed gnome-terminal -x fortune &&
i'm not sure that i can explain it good, because my english sucks
help again ?

edit: just looked up. i'll try and edit again
edit2: not working yet:
```
boris@linux:~$ gnome-terminal -x fortune &&;
bash: syntax error near unexpected token `;'
boris@linux:~$ 
```
Off Topic - Arghh I hate these colors ! Bad designers :P

---

### Post by warp99 on 2008-04-01
That's '&&:', my bad, and it doesn't work anyway.

OT:

The colors are screwing with me that's why I'm making so many mistakes.

---

### Post by LinuX-M@n1@k on 2008-04-01
np :) so do you have any other ideas ?

---

### Post by warp99 on 2008-04-01
This works with xterm:

```
xterm -e /bin/bash -c "fortune -w && clear && /bin/bash"
```

See if you can adapt it to gnome-terminal.

Edit:

You can remove the 'clear &&' if you just want the command line and not the screen to clear.

---

### Post by warp99 on 2008-04-01
I just did some research. The following string should work:

```
gnome-terminal -x /bin/bash -c "fortune -w && clear && /bin/bash"
```

You can also turn off the feature that keeps the gnome-terminal window open.

OT:

WTF with these easter egg colors?

---

### Post by LinuX-M@n1@k on 2008-04-01
great !! thanks a lot ;)

---

