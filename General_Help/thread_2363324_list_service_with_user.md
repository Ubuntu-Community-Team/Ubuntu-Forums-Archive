---
title: "list service with user"
date: 2017-06-08
forum: General Help
---

### Post by aminbaik on 2017-06-08
Hello,
what the command that i have to use to list all services with the account that is running by.
thanks.

---

### Post by cariboo on 2017-06-09
top works well for that, it is installed by default, just open a terminal and type:

```
top
```

---

### Post by SeijiSensei on 2017-06-09
Or add the "u" switch to ps, e.g., "ps aux" produces entries like
```
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         1  0.0  0.0  34316  4792 ?        Ss   Jun08   0:00 /sbin/init

```

---

### Post by Habitual on 2017-06-09
```
top -u <user>
lsof -u <user>
```

---

