---
title: "Script run on xterm terminal, how?"
date: 2007-08-14
forum: General Help
---

### Post by hraposo on 2007-08-14
I want create a script  that it was executed in consoles of gnome, runs in a terminal xterm.
That is, the command for script could be ./script, in consoles of gnome, but later opens a  xterm termina as root where script runs.
How I make this?
Which the commands to open xterm as root and to execute script?

---

### Post by ThinkBuntu on 2007-08-14
Well, to open the Xterm window, I'd use:

```
su xterm
```

And to run the script? Let me think...I'd use:

```
su -c 'xterm -e /this/is/the/path/to/the/executable'
```

But I may be wrong. You could substitute 'gksu' for 'su' and then leave out the -c and quotes.

Just a try! I'll let you know if I test this and it works.

---

### Post by BoltCutter on 2008-01-19
Ok so what I have done is

sudo startx -e 'sotware -flags'

it works great as long as I type it in the terminal, but when I try to compile it as a
script-app with platypus It doen's work.. any idea???

---

