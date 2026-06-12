---
title: "How to kill a specific java process?"
date: 2006-07-13
forum: General Help
---

### Post by AlliumPorrum on 2006-07-13
Hi!

I'm trying to make a batch that would kill & restart my own java application. 

How can I kill a specific java process?? I have being trying different combinations of ps, grep & kill, but I just can't make it working...

---

### Post by taurus on 2006-07-13
```

sudo kill -9 <process ID>

```
You can get the process ID (first column) with 

```

ps -A

```

---

### Post by AlliumPorrum on 2006-07-13
Yeah, I know, but how can I do that on a batch file?? I have somehow to parse the correct java process' ID from 'ps', and then pass it to the 'kill'.

---

### Post by mbeierl on 2006-07-13
Something like this ought to help you out:

```
ps -Ao pid,command
```

This tells ps to display only the pid and the command.  

Now you look for java processes like so:

```
ps -Ao pid,command | grep java
```

You can then pipe that through sed (the Stream EDitor) to remove leading whitespace like so:

```
ps -Ao pid,command | grep java | sed "s/^[ ]*//"
```

Then send that through cut to strip off only the first element in a space-delimited list (please note there are two spaces after the -d\)

```
ps -Ao pid,command | grep java | sed "s/^[ ]*//" | cut -d\  -f1
```

You can then make a one-liner to repeatedly perform an action (in this case kill) on each pid:

```
 for pid in `ps -Ao pid,command | grep java | sed "s/^[ ]*//" | cut -d\  -f1` ; do echo kill $pid ; done
```

This command just "echo"s the kill command for you to view instead of actually killing.  Remove the echo and it will kill.

Effectively, this now is the same as "killall java", which I presume is not exactly what you wanted.

If you want to kill only certain java processes, add more to the grep line.  For example, this will give the pids for java running Eclipse only:

```
ps -Ao pid,command | grep java | grep eclipse
```

Hope this helps!

---

### Post by ayoli on 2006-07-13
```
kill -9 `pidof process_name`
``` 
replacing process_name by the name of process ou want to kill
regards

---

