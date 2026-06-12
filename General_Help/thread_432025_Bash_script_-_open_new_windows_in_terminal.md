---
title: "Bash script - open new windows in terminal"
date: 2007-05-03
forum: General Help
---

### Post by ltk5 on 2007-05-03
I'm very new to writing scripts in bash. I'm trying to make it run two executables in two different terminals.
The only code I have (and haven't tested is below. However I don't know how to tell it to open a new windows and run another executable in it. Thanks for your help.

```
#!/bin/bash
cd bin/fah/1
./fah1.exe

# what here?
cd ../2
./fah2.exe
```

---

### Post by rich.bradshaw on 2007-05-03
you know that you can just type

/bin/fah/1/fah1.exe to run things, you don't have to cd into their directory don't you.

try

/bin/fah/2/fah2.exe &

That will probably work.

What exactly are you trying to do, if you are more specific we might be able to offer better assistance...

---

### Post by WW on 2007-05-03
If you really want a separate terminal to start up, you will need to give the command that runs a terminal.  For example, in Ubuntu (not Kubuntu or Xubuntu), the standard terminal is **gnome-terminal**.  This command will start up a new terminal with **top** running:
```

$ gnome-terminal -e top &

```

---

### Post by ltk5 on 2007-05-08
i did this
```
#!/bin/bash
/home/lotko/bin/fah/1/fah1.exe &

# what here?
gnome-terminal -e /home/lotko/bin/fah/2/fah2.exe &
```

fah.exe is folding at home, and everytime i tried opening it, it always started working in the current directory. It should start folding in *bin/fah/* directory and not *Desktop* (where my scripts are)
Another problem (not that close related) is that when I try to run my scripts by double-clicking on them, they don't execute. I did set the script to be executable in Properties.

---

