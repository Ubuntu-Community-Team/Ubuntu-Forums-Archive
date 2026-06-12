---
title: "Running wineconsole from cron"
date: 2005-10-08
forum: General Help
---

### Post by bsoric on 2005-10-08
Hey Everyone,
I'm having a problem running wineconsole from cron, because apparently wineconsole needs X to work. I've tried:

* * * * * export DISPLAY=:0.0; wineconsole xxxxx

but that doesn't seem to work. However, if I do the same thing in a terminal (Ctrl-Alt-F1) and then switch to X it works. So I'm very confused.

If anyone can help I'd appreciate it.

Brett

---

### Post by adwait on 2005-10-08
Add the following line to your crontab file, /etc/crontab if you are using the global crontab. Add it right at the top.......
```
DISPLAY=:0
```

---

### Post by bsoric on 2005-10-08
Thanks very much, worked perfectly.

---

