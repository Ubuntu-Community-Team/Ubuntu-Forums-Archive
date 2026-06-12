---
title: "open program as another user - aka what do I set the DISPLAY variable?"
date: 2008-04-20
forum: General Help
---

### Post by go_dragons on 2008-04-20
I have two accounts on my computer and sometimes I when I am logged into Gnome as one user I would like to open programs as another user. Specifically, I would like to open evolution email client as my other account without completely logging into another Gnome session.

This is what I have done:
I open gnome-terminal and su to my other account.
when I type 'evolution' I get the 'cannot open display' error.

I type export DISPLAY=":0.0"
and retry opening evolution but I still get the same error.

Does anyone know what I need do/what I need to set my export variable to in order to do what I want?

---

### Post by ibutho on 2008-04-20
Try using xhost e.g.
```
xhost +localhost
```

---

### Post by go_dragons on 2008-04-20
thanks for a quick response. I ran that program while logged into both accounts and could not get anything to work. The manpage of xhost says running xhost with no command line arguments given that it gives a message indicating whether or not access control is currently enabled. When I run xhost with no parameters it gives the error 

unable to open display ""

---

### Post by ibutho on 2008-04-20
What you need to do is start a terminal e.g. gnome-terminal, run "xhost +localhost", su to the new user and run the commands you wish.

---

### Post by sdennie on 2008-04-20
If I open up a terminal and do the following, it works fine for me:

```

xhost +local:
sudo -H -u someuser bash
xterm

```

That will give me an xterm owned by the user from the sudo command.

---

### Post by go_dragons on 2008-04-20
Thanks to everyone! This does exactly what I want it to do.


> **vor said:**
> If I open up a terminal and do the following, it works fine for me:

```

xhost +local:
sudo -H -u someuser bash
xterm

```

That will give me an xterm owned by the user from the sudo command.

---

