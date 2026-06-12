---
title: "Lost colours in Gnome Terminal"
date: 2007-05-19
forum: General Help
---

### Post by samjh on 2007-05-19
I have somehow lost the colours in gnome-terminal.  Before, files used to displayed in different colours depending on their permissions and file types, but now everything is the same colour.

How do I get the colours back?  I've tried setting the colours in the profile dialog, but it didn't do anything.

---

### Post by Zootropo on 2007-05-19
> **samjh said:**
> I have somehow lost the colours in gnome-terminal.  Before, files used to displayed in different colours depending on their permissions and file types, but now everything is the same colour.

How do I get the colours back?  I've tried setting the colours in the profile dialog, but it didn't do anything.

Try and input this command:
ls --color=auto

Does it show any colours?

---

### Post by samjh on 2007-05-19
Yes, it does, but only for that instance of the command.  All subsequent commands still show plain black colour, and no others.

---

### Post by samjh on 2007-05-19
Problem solved!

I created a .bashrc file in my home directory, and added to it this command:
```
alias ls='ls --color=auto'
```

Now, my terminal shows colours! :)

Thanks for the hint, Zootropo.

---

### Post by sumanc on 2008-05-02
But that is an option for the 'ls' command. Is there any way to set it from the terminal/konsole settings?

---

### Post by Bubba64 on 2008-05-02
> **sumanc said:**
> But that is an option for the 'ls' command. Is there any way to set it from the terminal/konsole settings?

In the terminal hit edit then current profile and you can change colors and set a transparency and other stuff.

---

