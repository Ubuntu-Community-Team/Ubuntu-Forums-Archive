---
title: "Services List"
date: 2013-06-21
forum: General Help
---

### Post by enienws on 2013-06-21
How can I see which user runs apache2 service on Ubuntu from command line?

---

### Post by 2F4U on 2013-06-21
What about

ps -ef

executed out of a terminal? It shows you the owner of the process in the first column.

---

### Post by newbie-user on 2013-06-21
Try using the ps command to list running processes and then pipe the output to grep to filter for apache2:
```
ps aux | grep apache2
```

---

