---
title: "Running Scripts in Terminal"
date: 2007-01-06
forum: General Help
---

### Post by JPMaximilian on 2007-01-06
So I've got a script, i made it executable, the way I run it is I put it in the .gnome2/nautilusscripts folder in my home folder, then I can right click and run it.  And it works fine that way, my question is how I would run this script from terminal?  Thanks.

---

### Post by finer recliner on 2007-01-06
./filename

---

### Post by JPMaximilian on 2007-01-06
Right, but that only works if i'm in the directory that the script is saved in, how do I run scripts from any directory.

---

### Post by aysiu on 2007-01-06
> **JPMaximilian said:**
> Right, but that only works if i'm in the directory that the script is saved in, how do I run scripts from any directory.
Put them in /usr/local/bin

That's what I do.

For example, I have a script called /usr/local/bin/backupfiles that runs an *rsync* command to back up my files to an external hard drive. If I just type ```
backupfiles
``` from any directory, the script runs.

---

### Post by ansi on 2007-01-06
> **JPMaximilian said:**
> Right, but that only works if i'm in the directory that the script is saved in, how do I run scripts from any directory.

You can write a full path to this script, e.g.:
```
$ pwd
/tmp
$ /home/username/myscripts/script.sh
```

Or make a persistent short-name alias in your shell. In bash it seems like this:
```
alias myscript="/home/username/myscripts/script.sh"
```
and now, anywhere you can call *myscript* command, which executes your script.

---

