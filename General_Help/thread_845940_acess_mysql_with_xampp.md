---
title: "acess mysql with xampp"
date: 2008-07-01
forum: General Help
---

### Post by dapim on 2008-07-01
hi,

i would like to acess only to mysql shell with xampp?
how can i do it?

./lampp startmysql
but now how i can acess the shell for mysql???

---

### Post by justleen on 2008-07-01
> **dapim said:**
> hi,

i would like to acess only to mysql shell with xampp?
how can i do it?

./lampp startmysql
but now how i can acess the shell for mysql???

once the mysql server is up and running, you should be able to connect with the mysql-client (if installed)
```
 mysql -h localhost -u user -p 
```

---

### Post by dapim on 2008-07-01
it isn't working in this way

---

### Post by justleen on 2008-07-01
is the client available? If you type "mysq" <TAB><TAB> does it show mysql?

---

