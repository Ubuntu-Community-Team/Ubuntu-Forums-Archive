---
title: "turn back chmod to  -rw-r--r--"
date: 2022-06-01
forum: General Help
---

### Post by chat-4432 on 2022-06-01
i accidently turn permission of file to 
```
--wx--x--x 1 root root
```
how do i can get permission -rw-r--r-- back ??

---

### Post by MAFoElffen on 2022-06-01
Answer:
```

sudo chmod 644 </path/filename>

```

---

