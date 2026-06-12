---
title: "Question re shells &amp; background processes"
date: 2007-05-15
forum: General Help
---

### Post by Cheese Sandwich on 2007-05-15
When I start a background process from a shell terminal window, such as:

gedit myfile &

it starts up in the background as intended, but if I subsequently close the shell window, the background process dies with it. However, this doesn't seem to happen in Solaris or in Red Hat (both of which I've used at work).

Is there any way to have background processes live beyond the lifespan of the shell from which they were run?

-Thx

---

### Post by Cheese Sandwich on 2007-05-15
The shell is bash, btw.

---

### Post by stylishpants on 2007-05-15
You can use the "disown" command.  It's a shell builtin command, so it has no man page.  Type "help disown" for more information.

However, this only works on individual commands.  I don't know how to configure the shell so that all backgrounded processes end up like this.  Knowing how bash is, I'm sure there's a way though.

---

### Post by sisco311 on 2007-05-15
```
nohup gedit file_name&
```

---

### Post by sisco311 on 2007-05-15
```
gedit /etc/skel/.bash_logout
```
add this line:
> disown %*

---

### Post by Cheese Sandwich on 2007-05-15
Ah, thanks.

---

