---
title: "Startup a process in Screen on system boot (Server/Terminal)"
date: 2014-01-26
forum: General Help
---

### Post by jomar3 on 2014-01-26
Hi people.
I have a problem with finding out how (if possible) to start up a [screen]("https://help.ubuntu.com/community/Screen") running a process when the system boots.
I already have the process start on a separate user by editing "/etc/rc.local", but I would like to start this inside a screen as well.

Thanks in advance :)

---

### Post by ian-weisser on 2014-01-27
See man screen:
```
       -d -m   Start screen in "detached" mode. This creates a new session but
               doesn't  attach  to  it.  This  is  useful  for  system startup
               scripts.
```

---

### Post by jomar3 on 2014-01-28
How do i then use that do start for example 'su tuyi -c "serverstart.sh start"' in a screen?

---

