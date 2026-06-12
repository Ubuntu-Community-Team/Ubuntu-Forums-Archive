---
title: "Why does this work? Grep/Pipes query..."
date: 2007-07-21
forum: General Help
---

### Post by Contrarian on 2007-07-21
Suppose the (truncated) output of 'ps -ef' looks like this ...

     UID     PID    PPID TTY     STIME COMMAND
sshd_ser   28936   29860   ?    Jul 20 /usr/sbin/sshd
Administ   29416       1   1  00:10:51 /usr/bin/bash

Why does this work?

 $ if ps -ef | grep -v grep | grep -q ssh ; then echo "Service Running"; fi
 Service Running

I know ps -ef gives the process list, and piping it trough 'grep -q ssh' would give an empty output but return a 0 since it found matches for 'ssh'.  But why does do the middle two greps fit in to provide the positive result that gets the echo statement to run?

---

### Post by bernied on 2007-07-21
If you just do
ps -ef | grep ssh
then you will always get a match, because the process started by the command 'grep ssh' (which you have just started) has 'ssh' in it (just try it). Reading 'man grep' tells me that the -v option inverts what you are looking for, so any line that does not have 'grep' in it gets through the first grep, then all that can get a result from the second grep is an actual occurence of ssh.

---

