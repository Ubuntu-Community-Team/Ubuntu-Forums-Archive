---
title: "killing processes"
date: 2007-04-05
forum: General Help
---

### Post by bailewen on 2007-04-05
I've noticed that often when running a gui simply closing out the window doesn't always kill the program so sometimes like say I am watching a video with VLC and I close the window the sound will keep playing because the process is still active. I tried the "kill" command in the command prompt but it says"

 arguments must be process or job IDs

So how do I go about finding out what the name of a given process is or what it's ID is?

---

### Post by heimo on 2007-04-05
You could use ps to list processes, or use top (h for help), list just your processes and hit k to kill it, or you could kill all certain name processes with killall (eg. killall vlc). Or get the process id (pid) with pidof (eg. pidof vlc) or kill all vlc processes very nastily with "kill -9 $(pidof vlc)".

---

### Post by louis_nichols on 2007-04-05
You have 2 possibilities.

To kill a program by its name, you should use the command *killall*, like this:
```
killall *process-name*
``` For example:

```
killall vlc
```

If you want to use just *kill*, this takes as argument the process ID. This is not difficult either. You can find running processes and their id's with the command ```
ps ax
``` The id will be in the first column. so you will just use ```
kill 5863
``` (for example).

Still, the easiest way would be to just use the Gnome System Monitor Under System>Administration. This can also be mapped to Ctrl+Alt+Del. There, you just see the processes in a list, select the one you want and press KILL.

---

