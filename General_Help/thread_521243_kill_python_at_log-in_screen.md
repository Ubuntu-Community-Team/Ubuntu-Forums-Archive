---
title: "kill python at log-in screen"
date: 2007-08-09
forum: General Help
---

### Post by muddymind on 2007-08-09
Hi!

I would like to kill every python process every time I enter in the log in screen (after a log out or a switch user)... How can I do it?

[]

---

### Post by muddymind on 2007-08-09
anyone?

---

### Post by muddymind on 2007-08-09
I made a script that look like this:

```
#!/bin/bash
PID=$(ps aux |grep ntlmaps|grep -v grep |awk '{print $2}')
for i in $PID ; do kill -9 $i; done
```

now i need to run it every time a user ends his session or if he make switch user... how can I do it?

---

### Post by muddymind on 2007-08-09
~~up~~

---

