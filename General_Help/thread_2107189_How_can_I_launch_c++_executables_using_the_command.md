---
title: "How can I launch c++ executables using the command line?"
date: 2013-01-21
forum: General Help
---

### Post by X D face me on 2013-01-21
Hey everyone

I've got a small c++ executable: multimc4(forkk.net/MultiMC4/). I want to add a desktop launcher for it with arronax but for that, i have to be able to launch it with a command. does anyone know how to launch c++ executables with the command line?

thx to any answers

X D face me

---

### Post by btindie on 2013-01-21
It doesn't matter what type of program it is, they all work in the same way.

If you haven't got a bin directory in your home directory then create one and place your executable in there.

Then create a link to it specifying the full path - e.g. /home/XDfaceme/bin/myprog

When you place executable files in your ~/bin directory you can run them from the shell without having to specify the path as the bash startup scripts automatically detect the presence of your ~/bin directory and add it to the PATH variable which is used by bash to search for programs - echo $PATH. When you create the ~/bin directory for the first time you'll have to close the shell and open it again for the bash init script to be re-run.

---

### Post by steeldriver on 2013-01-21
The same as any other executable

- make sure the executable bit is set

```
chmod +x /path/to/your/executable
```- if it is not located somewhere on your execute PATH then you must give the full path on the command line

```
/path/to/your/executable
```

---

### Post by X D face me on 2013-01-21
thx, works now. thread can be closed

---

