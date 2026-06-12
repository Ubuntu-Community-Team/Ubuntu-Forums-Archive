---
title: "ls command pages"
date: 2007-07-16
forum: General Help
---

### Post by mouseboyx on 2007-07-16
Is it possible to make it so that the ls command will pause at at the beginning of a new screen so that it is possible to view all information.

---

### Post by dpar on 2007-07-16
You can just scroll up to the beginning.

Type > man ls
In terminal for help.

---

### Post by mouseboyx on 2007-07-16
yes, but i need it when you cant scroll at the virtual terminals when you press crl+alt f1-f6

---

### Post by dpar on 2007-07-16
Did you try > ls | less

---

### Post by mouseboyx on 2007-07-16
thanks
!

---

### Post by jocko on 2007-07-16
You could always use "less":
```
ls | less
```Then you can scroll the output with the up/down arrow keys.
Press "q" to quit less and get back to the command line.

Edit: I'm typing too slowly...

---

### Post by RedSquirrel on 2007-07-16
You can also use 'more':

```
ls | more
```
```
ls -l | more
```

then you don't have to press "q". ;)

They say less is more, but I've always preferred more.

And do have a look at that man page too.

---

