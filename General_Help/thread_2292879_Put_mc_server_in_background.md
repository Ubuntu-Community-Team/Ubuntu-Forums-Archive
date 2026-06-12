---
title: "Put mc server in background"
date: 2015-08-31
forum: General Help
---

### Post by komekjr on 2015-08-31
I want to make a script that would automate starting multiple mc servers. 
I am using the latest spigot (new craftbukkit).
When I start the server with & on the end it stops and doesn't do anything.
When I start it in foreground, press ctrl+z and then bg %1 it stops as well.

How to prevent this? I don't want to use screen because it doesn't always work and I have issues with it.

Thanks in advance!

---

### Post by sandyd on 2015-08-31
try using
```

nohup *command* &
```

---

