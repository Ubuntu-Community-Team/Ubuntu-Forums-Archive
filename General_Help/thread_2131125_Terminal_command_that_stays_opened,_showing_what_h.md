---
title: "Terminal command that stays opened, showing what happens in the computer?"
date: 2013-03-31
forum: General Help
---

### Post by vezolmi on 2013-03-31
Hi.  There is a console command that, after you execute, keeps running, giving information about events that take place in the computer.  I cannot remember its name, neither find it, though I think is quite known. Any ideas?  Thanks

---

### Post by Bashing-om on 2013-03-31
top ?

---

### Post by vezolmi on 2013-03-31
Thanks, but no, it's another one. It's not about processes. I think it outputs text lines with information for example when you insert a USB flash drive.

---

### Post by steeldriver on 2013-03-31
then maybe what you're thinking of is

```
tail -f /var/log/syslog
```

---

### Post by vezolmi on 2013-03-31
Thank you! With that I get what I want. But I have 2 questions now:

a) Is there any one-word command that does something similar to **tail -f /var/log/syslog**?

b) Are there more useful **tail -f ...........log**-like commands? (for example to know which applications are opened ...)

---

### Post by Bashing-om on 2013-03-31
vezolmi; 

Your questions indicate you are ready to learn about the linux command line users manual.
```
man man
```where man = manual thus "man man" = the manual on the manual.
To find an unknown command for for a given "task":
```
 man -k <key_word(s}>
```
as an example:
```
man -k running task
man -k task
```
and in particular:
```
man tail
```[INDENT=3]just try'n to help

[/INDENT]

---

### Post by mexicanseaf00d on 2013-03-31
try

```
watch "dmesg | tail -20"
```

this calls "dmesg" every 2 seconds and displays the last 20 lines of dmesg's output.
abort with ctrl+c

---

### Post by vezolmi on 2013-03-31
Thanks for the answers.


Does anybody know any log or command that gives information about the programs we open or close?

---

### Post by efflandt on 2013-03-31
Applications typically output messages to stdout and/or stderr.  Unless you redirect output somewhere, an app specifically logs somewhere, or something logs if it crashes, I don't think there is a way to see the results of something not launched from a terminal or launched from a terminal that is no longer open or accessible.

Nothing normally logs all output from all processes.

**ps aux** would show current processes. Maybe **ps aux | less** in a wide terminal (132 col) if you want to scan through them and more of the command that launched the apps (which may reveal zombies).

**top** or **htop** (which shows multiple processors) may reveal if some process is in a race condition (endless loop), consuming cpu time and possibly memory.

Up cursor key would show recent commands in a particular terminal, but not the result.  Likewise the contents of ~/.bash_history for terminals that were closed.

If you have a drive problem, such that a drive remounts readonly (so no logs can be written), **dmesg** before shutting down may reveal something about the drive problem.

---

### Post by bab1 on 2013-03-31
Could you be looking for system calls when using a command.  That would be **strace**.  It would be used like this```
strace <whatever_command_you_choose>
```

You can find a list of system monitoring tools [**_[COLOR="#0000FF"]here[/COLOR]_**]("http://www.cyberciti.biz/tips/top-linux-monitoring-tools.html").

---

### Post by vezolmi on 2013-04-02
Thanks.

I was wondering if there is any log file, command or application that says for example:
20:03:56 gedit opened
20:04:05 gcalctool opened
20:04:27 firefox opened
20:04:45 gcalctool close
20:32:31 gedit closed
20:37:25 firefox closed

---

