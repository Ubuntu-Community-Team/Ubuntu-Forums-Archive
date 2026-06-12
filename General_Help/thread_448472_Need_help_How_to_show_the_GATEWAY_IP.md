---
title: "Need help How to show the GATEWAY IP"
date: 2007-05-19
forum: General Help
---

### Post by Klitzie on 2007-05-19
Is there a equivalent command in ipconfig/all in Windows in Ubuntu? because i don't know what command can render my gateway address using the terminal in ubuntu...thx

---

### Post by The Pinny Parlour on 2007-05-19
```
ip neigh
```

or

```
ifconfig
```

---

### Post by hartz on 2007-05-19
Enter this command:

```
netstat -r
```

The line starting with the word "default" shows your gateway (Default router)

---

