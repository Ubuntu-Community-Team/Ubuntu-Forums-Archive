---
title: "BASH - hide output but continue"
date: 2007-07-27
forum: General Help
---

### Post by zwanzig on 2007-07-27
Is it possible to under the processing of a command press a shortkey to hide the output and give me the pid and the prompt back?

Example:
I run
```
BASH$ sudo slocate -u
```
And then realize it will take some time and i should have run ```
BASH$ sudo slocate -u &
```
Now i want to press i.e. ctrl-H to:
[LIST]
[*]hide the output
[*]tell me the pid
[*]give me a BASH$
[/LIST]

---

### Post by noof on 2007-07-27
That depends on what you want to do, why you need the pid. You can press ctrl-z and write bg. But that won't hide the output but you'll get a new prompt while the last command is running in the background.

---

### Post by zwanzig on 2007-07-27
Thats seems to stop the previous command for me... I don't really need the pid.

---

### Post by mpeters on 2007-07-27
> **zwanzig said:**
> Thats seems to stop the previous command for me... I don't really need the pid.

```
Ctrl-z
```

Suspends the command.

```
bg
```

resumes the command in the background. If you run 

```
jobs
```

You should see the status of the command. You can bring the command to the foreground again, if you wish, by running:

```
fg *<job number>*
```

where *<job number>* is the number shown when running jobs, note that this is not the pid.

---

### Post by stylishpants on 2007-07-27
The PID is available in this variable: $!

I wonder if you could alter the stdout and stderr of a running process by messing with the symlinks in /proc/$PID/fd/?  Symlink 1 should be stdout, symlink 2 should be stderr.

---

