---
title: "distinguishing interactive bash from script bash in ps"
date: 2019-09-30
forum: General Help
---

### Post by Skaperen on 2019-09-30
i still use bash for many scripts as well as many interactive shell sessions.  i want to be able to terminate all the interactive shells or all the script shells for a particular user, but not both.  "killall /bin/bash" would do both.  i'd like to know the best way to list bash processes in ps that can be filtered to one type or the other.

---

### Post by TheFu on 2019-09-30
Use a PID file for a each "program". Be certain to trap signals so the PID file gets cleaned up regardless of how the process ends.  [https://www.tldp.org/LDP/Bash-Beginners-Guide/html/chap_12.html](https://www.tldp.org/LDP/Bash-Beginners-Guide/html/chap_12.html)
Professional programs should always clean up their temp files regardless of how they finish, even if killed.

You can use the PID file to know the process and kill them using the PID.

---

### Post by Skaperen on 2019-09-30
yes, in the case of killing a script that has temporary file, it should clean them up on the appropriate signals.  but my issue is determining which processes to kill and which processes to not kill, depending on which set i want killed.  the scripts might be called [COLOR=#0000cd][FONT=courier new]**killallbashscripts**[/FONT][/COLOR] and [COLOR=#0000cd][FONT=courier new]**killallbashsessions**[/FONT][/COLOR].  the latter one will also check to see if it is running under one and kill it last, or try to ignore [COLOR=#0000cd][FONT=courier new]**SIGHUP**[/FONT][/COLOR].

---

### Post by Holger_Gehrke on 2019-10-01
```
ps -a -C bash -o pid,args --no-headers
```
will output all process with 'bash' somewhere in the command. A bash executing a script has the name of the script file as one of its arguments.

Holger

---

### Post by HermanAB on 2019-10-01
You could use a different Group ID using the program 'sg' to launch the script.  Then you can manage the programs based on their group IDs

---

### Post by Skaperen on 2019-10-01
> **Holger_Gehrke said:**
> ```
ps -a -C bash -o pid,args --no-headers
```
will output all process with 'bash' somewhere in the command. A bash executing a script has the name of the script file as one of its arguments.

Holger

so, i just need to see if a script name is there, or not.

---

