---
title: "gcc problem"
date: 2008-05-06
forum: General Help
---

### Post by htpvitas on 2008-05-06
when my using gcc to build my grogram, the problem has been occur:

htpvitas@root:~/Desktop/program/example$ ls
m.c  m.c~
htpvitas@root:~/Desktop/program/example$ gcc -o m m.c
m.c:1:18: error: stdio.h: No such file or directory
m.c: In function ‘main’:
m.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

who can tell me? thank you!

---

### Post by Dougie187 on 2008-05-06
Whats your code look like? i dont think its an issue with GCC. it looks like a programming issue instead. Just give the first few lines.

---

### Post by jw5801 on 2008-05-06
> **htpvitas said:**
> when my using gcc to build my grogram, the problem has been occur:

htpvitas@root:~/Desktop/program/example$ ls
m.c  m.c~
htpvitas@root:~/Desktop/program/example$ gcc -o m m.c
m.c:1:18: error: stdio.h: No such file or directory
m.c: In function ‘main’:
m.c:5: warning: incompatible implicit declaration of built-in function ‘printf’

who can tell me? thank you!

```
sudo apt-get install build-essential
```

Will fix your problem. You don't have any of the headers you need to be able to call 'inbuilt' functions.

---

