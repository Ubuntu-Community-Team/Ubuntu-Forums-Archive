---
title: "Adept database locked"
date: 2007-05-15
forum: General Help
---

### Post by subnet_rx on 2007-05-15
I get a message on starting up Adept that says my database is locked because another process is using the database.  How can I find out what process is using it, and unlock the database?  I really think that it's locked from Adept crashing the last time I had it open, but still don't know how I can unlock the db to test my theory.

---

### Post by taurus on 2007-05-15
Applications -> Accessories -> Terminal
```
ps -A
```

---

