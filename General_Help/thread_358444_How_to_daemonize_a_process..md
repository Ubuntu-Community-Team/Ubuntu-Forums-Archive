---
title: "How to daemonize a process."
date: 2007-02-10
forum: General Help
---

### Post by kd7swh on 2007-02-10
Could some one share the proper syntax for this with me?

I want to execute one shell script (in the foreground), than execute another script and daemonize it. (run it in the background)

would it be something like :

root@computer:~# command1|command2 -d

:confused:

---

### Post by rai4shu2 on 2007-02-10
More like:

command1|command2 &

---

### Post by kd7swh on 2007-02-10
ok that seems to daemonize the process but the terminal window is still open in X after it launches and daemonizes. How can I tell that gnome-terminal to close after daemonizing?

```
 command1 | command2 &;
exit 
```

doesn't work.


:(

---

### Post by koenn on 2007-02-11
try 
```
....    |  (command2 &) && exit;
```
Also note that the | you use between command1 and command2 means "send output of command1 to command2" or "let command2 take output from copmmand1 as input".

Depending on what you want the relation between the 2 commands is, you'd want to separate them with
 |  
||  
&& 
;

and depending on which of those you chose, you may need () here and there

---

