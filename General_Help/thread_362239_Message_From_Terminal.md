---
title: "Message From Terminal?"
date: 2007-02-15
forum: General Help
---

### Post by kvonb on 2007-02-15
-

---

### Post by Ramses de Norre on 2007-02-15
To a plain console like the one you get with alt-ctrl-F2?
Do **finger** to see who's on which console, and if for example someone is on tty2 you can print "test" on his terminal with: ```
echo "test"|tee -a /dev/tty2
```
I'm not sure who to do this with terminal emulators like a gnome-terminal session, these sessions aren't device nodes you can write to like the tty's.

---

### Post by kvonb on 2007-02-16
-

---

### Post by kvonb on 2007-02-16
-

---

### Post by stylishpants on 2007-02-16
If you just want to print a single message on another user's terminal, you should learn the 'write' command.  (see the man page.)  The 'wall' command may be useful too.

If you want a fully interactive conversation, then you want the "talk" package or one of it's descendents such as "utalk" or "ytalk".  You will have to install these to use them.

---

### Post by kvonb on 2007-02-17
-

---

### Post by Ramses de Norre on 2007-02-17
> **kvonb said:**
> IT works between the same user, but to another user I get this:

fred@kev:~$ echo "test"|tee -a /dev/tty1
tee: /dev/tty1: Permission denied

....and you can't use "sudo" with "echo" unfortunately :(

You need to use sudo to gain access to the tty then, but the other mentioned methods are probably better anyway ;)

---

