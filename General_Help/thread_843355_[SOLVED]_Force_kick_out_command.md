---
title: "[SOLVED] Force kick out command"
date: 2008-06-28
forum: General Help
---

### Post by jspolen on 2008-06-28
I'm logging into my webserver computer by using ssh, and find that my friend is logged in to. 

For fun I would like to kick him out, since I'm the administrator I have the rights.

But what commands  do I use, lets say my friends username is rooney.

Is there something like *kickout rooney*

---

### Post by sisco311 on 2008-06-28
```
skill -KILL -u rooney
```

---

### Post by jspolen on 2008-06-28
Thanks

---

### Post by mcduck on 2008-06-28
If you just eant to have fun, why not decrease you'r friends nice level instead.. I've always thought that as a fun trick (and somehting to make people remember not to mess with their system admins :D)

```
sudo renice +10 -u username
```

(The command decreases the priority of all processes owned by that user..)

---

