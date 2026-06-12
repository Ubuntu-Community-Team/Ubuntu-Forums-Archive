---
title: "hello friends"
date: 2008-03-06
forum: General Help
---

### Post by prof.bond007 on 2008-03-06
hello,
i want to run my c program automatically when i logoff my ubuntu.
what is the procedure....
pplz help me..

---

### Post by elspiko on 2008-03-06
Providing you've complied the program already...

Edit your $HOME/.bash_logout file so you add the file execution.

e.g. if you compiled the program thus

```
gcc test.c -o /path/to/file/myprog
```

you would add

```
/path/to/file/myprog
```

to the end of your $HOME/.bash_logout file :)

---

