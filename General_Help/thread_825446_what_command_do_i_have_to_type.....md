---
title: "what command do i have to type...."
date: 2008-06-11
forum: General Help
---

### Post by eival on 2008-06-11
[IMG]http://i29.tinypic.com/qxrmlc.png[/IMG]

i want to change the setting for the line i have marked in black.

what command would let me do that?

---

### Post by spiderbatdad on 2008-06-11
I believe what you are looking for is controlled in /etc/security/limits.conf
with the nofile (item) You can look at the file editing guidelines for more information, or the Ubuntu Handbook perhaps.

---

### Post by HalPomeranz on 2008-06-11
"ulimit -n <number>" will let you change the value.  Notice that the output of "ulimit -a" is trying to give you a hint that the "-n" option is the one you want.

As the previous poster points out, you can also set default values for these parameters in limits.conf.  Note that the values in limits.conf only apply to normal interactive user logins (and not processes started at boot time, by cron, etc).  Also, limits set in limits.conf never apply to the superuser.

---

### Post by iaculallad on 2008-06-11
> **eival said:**
> [IMG]http://i29.tinypic.com/qxrmlc.png[/IMG]

i want to change the setting for the line i have marked in black.

what command would let me do that?

```
ulimit -n size
```

size=integer

---

### Post by eival on 2008-06-11
i tried "ulimit -n <size>" but it said Command Not Found

i tried it again using Sudo and still got the same message

do i have to be logged in as Root user?

---

### Post by HalPomeranz on 2008-06-11
> **eival said:**
> i tried "ulimit -n <size>" but it said Command Not Found

Huh?  You posted the output of "ulimit -a" earlier.  How is it that that command works for you, but "ulimit -n ..." doesn't?  Has something changed in your environment since your original posting?

Anyway, the ulimit command is a bash built-in command-- there typically is no separate ulimit executable.  Have you changed your default shell recently?  "echo $SHELL" will usually tell you what shell you're currently running.

---

### Post by eival on 2008-06-11
alright my tech guy at work just tried this out for me an we found out you have to be logged in as root to change the number.

if you try it with a user or sudo the commands wont work.

:popcorn:

---

