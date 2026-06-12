---
title: "zombie processes"
date: 2018-05-15
forum: General Help
---

### Post by sniper8752 on 2018-05-15
I received a warning of ~160 zombie processes on my server, and it has been slowly growing.  Doing a ps aux, it looks like there are lots of [sh] <defunct> processes by root.  How do I kill them, and how do I figure out what the parent is, and how they are being spawned?

---

### Post by QIII on 2018-05-15
Hello!

On cell phone right now so I can't confirm, but I think the following should help you find the PPIDs of the zombie processes

```
ps -l | grep Z 
```

Maybe use -axl

---

### Post by Bashing-om on 2018-05-15
sniper8752; Hello - 

Amend QIII's memory to:
```

ps aux | grep 'Z'

```

then ya want the child processes:
```

pstree -p -s <child-process-PID>

```

Kill these processes:
```

sudo kill <PID_grandchild>

```
[http://askubuntu.com/questions/111422/how-to-find-zombie-process](http://askubuntu.com/questions/111422/how-to-find-zombie-process)

[INDENT]my bit to try and help
[/INDENT]

---

### Post by QIII on 2018-05-15
Muscle memory with two thumbs is not the same as with all 10 fingers...

---

