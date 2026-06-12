---
title: "how to run a terminal command that will open automatically in a new terminal"
date: 2013-06-17
forum: General Help
---

### Post by floorripper on 2013-06-17
Hello,

I am trying to log in into a device.

I have written a script which logs me in into another system,router via ssh.
When go to the router, and I make "show users" I see my new established  ssh session on the new VTY. So he makes it subtle.

```


#!/bin/bash 
 clogin $1


```


clogin is my automatic login script, which comes from a Rancid  package,it runs on echo,expect. But that's run fine. It also takes the  variable. TCP session is established but I do not see it in the new  terminal.
That's the main point. I need it to open a new window automatically and to log me in this window.

SOLVED>

the script with clogin could be replaced with the ssh or telnet command
```
nohup x-terminal-emulator  -e ssh $1 &
```

---

### Post by varunendra on 2013-06-17
> **floorripper said:**
> 
clogin is my automatic login script, which comes from a Rancid  package,it runs on echo,expect. But that's run fine. It also takes the  variable. TCP session is established but I do not see it in the new  terminal.
That's the main point. I need it to open a new window automatically and to log me in this window.

Not 100% sure, but I hope this should work -
```
#!/bin/bash
exec gnome-terminal -x clogin "$1"
```
This will execute the "clogin" script in a new terminal (gnome-terminal), accepting whatever argument you supply ($1).

If the "clogin" script further executes something that is needed to be done in a new terminal, something similar as above can be done with that too.

---

### Post by floorripper on 2013-06-18
Hello thanks it works as well! 
I have managed it also with:

> nohup x-terminal-emulator  -e clogin $1 &

---

### Post by varunendra on 2013-06-18
> **floorripper said:**
> Hello thanks it works as well! 
I have managed it also with:```
nohup x-terminal-emulator -e clogin $1 &
```
Nice! Didn't know of that 'nohup' command, looks simple but interesting. :)

Please consider marking the thread as **[Solved]** now that it is. Helps others with similar problems.
(follow the link in my signature to see how and why to mark threads [Solved].)

---

