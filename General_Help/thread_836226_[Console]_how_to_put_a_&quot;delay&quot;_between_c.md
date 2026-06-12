---
title: "[Console] how to put a &quot;delay&quot; between commands execution"
date: 2008-06-21
forum: General Help
---

### Post by randomAccess on 2008-06-21
As title says, I have a shell script (.sh extension) that executes 10 commands in a row. As these services all connect to internet, I do not want then to connect simultaneously. 

How can I put a delay between them so when the 1st commands executes, there's a delay of 30 seconds, then the 2nd one executes, and so on. 

Is this possible after all? :confused:

---

### Post by drs305 on 2008-06-21
> **randomAccess said:**
> As title says, I have a shell script (.sh extension) that executes 10 commands in a row. As these services all connect to internet, I do not want then to connect simultaneously. 

How can I put a delay between them so when the 1st commands executes, there's a delay of 30 seconds, then the 2nd one executes, and so on. 

Is this possible after all? :confused:

Add a line: 
```
sleep 30

```

---

### Post by MattiJ on 2008-06-21
try
```
sleep --help
```

---

### Post by randomAccess on 2008-06-21
thanks guys ;)

---

