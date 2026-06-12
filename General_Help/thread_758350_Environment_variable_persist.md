---
title: "Environment variable persist?"
date: 2008-04-17
forum: General Help
---

### Post by puelly on 2008-04-17
Do environment variables persist include when I run a command with 'sudo'?

For example, I am trying to run Tomcat, I am certain that $JAVA_HOME is set to the correct path and I can see the value when I run 'echo $JAVA_HOME'.  However, Tomcat's startup script still tells me that JAVA_HOME is not set.  What is causing this and how can it be rectified?

Any help would be appreciated, Thanks.

---

### Post by Glaxed on 2008-04-17
to explain, open a terminal and type
$ echo $USER

now type
$ sudo echo $USER
...
So try setting $JAVA_HOME under sudo..

---

### Post by puelly on 2008-04-17
> **Glaxed said:**
> to explain, open a terminal and type
$ echo $USER

now type
$ sudo echo $USER
...
So try setting $JAVA_HOME under sudo..
I get the same output for both commands

richard@linbox:~$ echo $USER
richard
richard@linbox:~$ sudo echo $USER
[sudo] password for richard: 
richard
richard@linbox:~$ 

also sudo export $JAVA_HOME="/here/" gives me an error that export is not a valid command

---

### Post by imtheguru on 2008-04-18
> **puelly said:**
> sudo export $JAVA_HOME="/here/" gives me an error that export is not a valid commandThat's right

in bash shell the $ is used only to dereference the variable, not for export.

```
export JAVA_HOME=/path/goes/here
./path/to/tomcat/start.sh
```

Cheers.

---

