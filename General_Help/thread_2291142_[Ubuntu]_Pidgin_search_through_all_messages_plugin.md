---
title: "[Ubuntu] Pidgin search through all messages plugin"
date: 2015-08-18
forum: General Help
---

### Post by roman37 on 2015-08-18
Greetings!
From time to time I close a chat window, than attempt to remember who I was talking with. As I have about 300+ contacts it is always a problem.
Is there any plugin, which allows search through all messages (by keywords or simply by date at least)?

---

### Post by jim_deadlock on 2015-08-18
As you probably know, you can right-click on a contact and View Log. I don't know about a plugin for finding out who you were last chatting to, but I would do it in a terminal:

```
ls -lrt ~/.purple/logs/yahoo/jim_deadlock
```

Replace protocol/Your ID as necessary, this will show the latest contact at the bottom of the output list.

---

### Post by roman37 on 2015-08-18
Thank you for the answer. This is helps, but not solves - usually I have some conversations after that, so I have to look into chats to find the desired one. Sorting by time greately reduces the number of chats to look throu, but still a lot of unwanted job

---

