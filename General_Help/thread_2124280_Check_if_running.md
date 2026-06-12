---
title: "Check if running"
date: 2013-03-10
forum: General Help
---

### Post by hwttdz on 2013-03-10
I'm trying to use start stop daemon to check if a python script is running.  The catch is if I execute
./myscript.py
what's actually running is /usr/bin/python, and I might want multiple instances of python running.  So I'm interested in getting start-stop-daemon to specifically check for a python which is running a certain script.  Is there a way to do this, or another clever way?  Sadly pid/lock files don't work well here because the daemon tends to terminate unexpectedly/filesystem issues (not my server).

---

### Post by cybergalvez on 2013-03-10
you could process the output of ps -e -F through grep looking for your program

---

### Post by prshah on 2013-03-10
You can use the "-c" option of top to display the actual commandline used for the process.

Eg, ```

top -c -b -n 1|grep python
``` should give you a list of running python processes, INCLUDING the command line used to initiate the process. -c = show command line, -b = batch mode (non-interactive) -n 1 (run only once).

From that point, I guess it's a simple matter to extract the PID, though I failed miserably when using the "cut" command (apparently, "top" uses multiple spaces to align fields).

Please post back if you need more information.

---

### Post by steeldriver on 2013-03-10
... or just get the pid with

```
pgrep -f 'myscript.py'
```

maybe? (the '-f' searches the whole command not just the process name - similar to the -c in top)

For top, awk seems to work if cut is tricky:

```
top -cbn1 | awk '$NF ~ /myscript/ {print $1}'
```

---

### Post by hwttdz on 2013-03-12
Thanks, I switched to a mini-script with top & grep, but it seems like it should be unnecessary.  

I'll try pgrep as that's one I haven't looked at.

Unrelated, but did mark as solved disappear again in the remodel?  If not where is it hiding?

---

### Post by steeldriver on 2013-03-12
I guess one caveat with pgrep is that afaik it won't distinguish between running and defunct processes - so if you really need to find *running* instances of your script you may need to do something more sophisticated - see here for example [http://unix.stackexchange.com/questions/13622/how-to-list-only-non-defunct-processes](http://unix.stackexchange.com/questions/13622/how-to-list-only-non-defunct-processes)

---

