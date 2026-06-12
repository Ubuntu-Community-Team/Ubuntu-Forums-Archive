---
title: "user account login chronologie"
date: 2016-06-29
forum: General Help
---

### Post by kaky951357 on 2016-06-29
hello, 
 i want to know the time of login and logout of user account and especially the time of trying without succes to access my laptop, is there application that can take a webcam shut when some one tipe the wrong password?
than you to trying help me.

---

### Post by fdrake on 2016-06-30
```
sudo less /var/log/auth.log | grep -e user -e "authentication failure"
```
about the camera i don't know... but that d be a good idea...

---

### Post by kaky951357 on 2016-06-30
thanks for help,
is /var/log/auth.log the only file where i can found that kind of information ? if i want delete trace about my login in to a session what can i do ?

---

### Post by fdrake on 2016-06-30
The best way is to use a live cd . Even if you try to delete that log, the delete process will create a new session, which will be recorded. Live cd/USB is the best way to not leave trace of login.

---

