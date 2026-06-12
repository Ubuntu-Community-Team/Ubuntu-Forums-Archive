---
title: "Remotely running applications"
date: 2007-03-22
forum: General Help
---

### Post by plueken on 2007-03-22
Scenario:  I have my computer running, and I want to connect to it from another location, start a program on my computer, and then disconnect while the program continues to run (say, downloading or updating or some such).  Is there any easy way to do that?

I have tried everything I can think of with ssh and nx, and I can't think of any way to start a program that will not end as soon as I disconnect and end the temporary session.  Really, is there any way to start a program in an already active session, so that it doesn't quit when I disconnect?

Thanks in advance.

plueken

---

### Post by thelinuxguy on 2007-03-23
> **plueken said:**
> Scenario:  I have my computer running, and I want to connect to it from another location, start a program on my computer, and then disconnect while the program continues to run (say, downloading or updating or some such).  Is there any easy way to do that?

I have tried everything I can think of with ssh and nx, and I can't think of any way to start a program that will not end as soon as I disconnect and end the temporary session.  Really, is there any way to start a program in an already active session, so that it doesn't quit when I disconnect?

Thanks in advance.

plueken

You are looking for VNC. A forum search for VNC will get you what you are looking for. One of them is here: [http://www.ubuntuforums.org/showthread.php?t=191564&highlight=vnc](http://www.ubuntuforums.org/showthread.php?t=191564&highlight=vnc)

---

### Post by nikhilk on 2007-03-23
I do this routinely for non-interactive programs.
```
nohup <application> &
```
e.g. nohup wget -i urls.txt &

---

