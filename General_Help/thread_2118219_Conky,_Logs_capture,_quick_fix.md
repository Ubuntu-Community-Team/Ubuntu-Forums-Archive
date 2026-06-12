---
title: "Conky, Logs capture, quick fix"
date: 2013-02-20
forum: General Help
---

### Post by Warprunner on 2013-02-20
Hi everyone,
Novice to the programming of Conky. 
I am using the following to capture the Syslog in conky:

${execi 2 tail -n5 /var/log/syslog | fold -w50}

This works great except I would like to have it read by the most recent down instead of the most recent on the bottom.

Can anyone help?
Thanks ahead of time!!!

---

### Post by Habitual on 2013-02-20
```
tail -n5 /var/log/syslog | sort -r | fold -w50
```

---

### Post by Warprunner on 2013-02-20
> **Habitual said:**
> ```
tail -n5 /var/log/syslog | sort -r | fold -w50
```


MANY many thanks!!!!   :D

---

### Post by Habitual on 2013-02-20
I don't code conky anymore, but that was too simple a fix to pass up.

You are very welcome!

[Conky PitStop]("http://conky.pitstop.free.fr/")

---

