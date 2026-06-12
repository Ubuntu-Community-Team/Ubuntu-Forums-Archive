---
title: "Piping a command to 'at' leads to command being executed immediately"
date: 2015-01-19
forum: General Help
---

### Post by matt174 on 2015-01-19
```
echo "happy days" |at now + 1 minute
```

This results in echo running immediately, not a minute later. How can I pipe commands into 'at'?

---

### Post by Holger_Gehrke on 2015-01-19
you have to pipe the command into it. Example:
```

echo 'ls -1lAR /usr/'|at now + 1 minute

or to fix your example

echo 'echo "Happy Days"' | at now + 1 minute

```
Output and errors will be mailed to your local account. You should have gotten a mail giving you an error along the lines of 'happy : command not found'. You can check your local mail by entering 'mail' on the command line.

---

### Post by tgalati4 on 2015-01-19
*at* is a strange command.  I find it works better with a script using the -f switch.  I know that *at* does not work the way you expect it to.

---

### Post by matt174 on 2015-01-19
The correction still does not work - nothing echoes out at the specified time.

Let's say I want to use gedit instead:

echo "happy days" > happy.txt
gedit happy.txt | at now + 1 minute

This also executes immediately. I'm not sure what your fix does. Please explain.

Thanks very much for the help!

---

### Post by matt174 on 2015-01-19
```
at -f mplayer /home/matias/Documents/projects/fitness/down.mp3 now + 1 minute
```

I get this error:

```

syntax error. Last token seen: /
Garbled time


```

---

### Post by Lars Noodén on 2015-01-19
> **matt174 said:**
> Let's say I want to use gedit instead:


Can you spot the difference between these two?

```

 gedit happy.txt
 echo "gedit happy.txt"

```

The first one runs gedit, the second one outputs some text.  The second one is what you want since at is expecting some text input.

```

 echo "gedit happy.txt" | at now + 1 minute

```

Also, +1 minute is more like now +1 to +60 seconds, since at will run at the top of the minute.

---

### Post by Holger_Gehrke on 2015-01-19
The 'at' command is old and strange. Its meant for big, non-interactive jobs (let's say compiling a complete DE from sources) you want to run at a time when their load on the system won't get in the way of people doing their job. It's not meant for starting interactive stuff at a given time. Search synaptic for 'timer' if that's what you need. 

The '-f' option expects a text file full of commands you want to execute at the given time, what you told it was to read a file called mplayer in the current directory and execute the commands in it at '/home/matias/Documents/projects/fitness/down.mp3' o clock :)

---

