---
title: "Bash script: disown &amp; exit"
date: 2014-03-05
forum: General Help
---

### Post by schema2 on 2014-03-05
I am writing a bash script and I would really like to be able to detach the process and close the terminal when launched from prompt.  Here are examples of formats I've tried. I am able to detach the process, but I can't close the terminal. 

nohup firefox localhost & 
exit


firefox localhost & disown;
exit

What am I missing?

---

### Post by Lars Noodén on 2014-03-05
The script has the pid of $$, since it is the 'current' process.  You can find its parent in /proc

```

[s]ppid=$(/usr/bin/awk '{ print $4 }' /proc/$$/stat)[/s]
echo Parent is $ppid

```

If the script was launched from the terminal, then $ppid will be the pid of the terminal.  If the script was launched in a different context, then the pid of something else will get returned.  You probably need some safeguard to ensure that nothing important gets killed, such as your desktop environment.


Edit: never mind, that gets too high a parent to be useful.  It will kill all terminals.

---

