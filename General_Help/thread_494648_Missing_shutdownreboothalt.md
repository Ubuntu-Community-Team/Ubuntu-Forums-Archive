---
title: "Missing shutdown/reboot/halt"
date: 2007-07-07
forum: General Help
---

### Post by shugo_socks on 2007-07-07
I can't seem to find the shutdown, reboot, or halt commands.  From what I have read, they are supposed to be in /sbin.  However, they are not there.

I have run "find / -name shutdown", but nothing is found.

Using Ubuntu Feisty.

Any help would be amazing.

---

### Post by DagMan on 2007-07-07
type 
```
which shutdown
```
at a terminal

When you don't know where a command resides, use which and it will give you the path and if there is more than one it will give you the location of all of them.

All three of those commands are located in /sbin on my system.
make sure to read the manuals for them before using them if you aren't sure what all the options are and how specifically they work.
```
man shutdown
```

locate is a good command line tool to find things as is slocate.

---

### Post by shugo_socks on 2007-07-07
"which shutdown" gives nothing, nor does "which reboot" and "which halt".

The problem isn't that I don't know how to use them, it's just that they aren't there.  Since find didn't find it, I am concerned that it isn't on my computer.

---

