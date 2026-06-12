---
title: "[SOLVED] gimp at startup"
date: 2008-04-12
forum: General Help
---

### Post by gishaust on 2008-04-12
hi everyone,

Very time i start xubuntu it automatically starts gimp. It is not an auto start program. How do get it to stop?

any help  would be great!!!!

gishaust

---

### Post by Koybe on 2008-04-12
Look in System -> Preferences -> Session

You should have started it and save your session.

---

### Post by sisco311 on 2008-04-12
delete the session files:
```
rm ~/.cache/sessions/*
```
and don't save your session when you logout/shut down

---

### Post by gishaust on 2008-04-12
thankyou your advice worked.

---

