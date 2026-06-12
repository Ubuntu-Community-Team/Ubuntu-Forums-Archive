---
title: "bash: syntax error near unexpected token `['"
date: 2008-04-01
forum: General Help
---

### Post by yanyan on 2008-04-01
I am practicing using bash on ubuntu system. I typed in following command on command line and got following error message. Could anyone tell me why?

> for $index ( a b c) ; do echo '$index'; done
bash: syntax error near unexpected token `('

here, I really could not understand why it could not work. thanks a lot.

---

### Post by dabang on 2008-04-01
I think it should be (but can't test right now...):
```

for index in (...); do echo $index; done
```

---

### Post by prshah on 2008-04-01
> **yanyan said:**
> 
> for $index ( a b c) ; do echo '$index'; done
bash: syntax error near unexpected token `('



Use braces " { } " not parenthesis " ( ) " 

>  for index in {1..10}; do echo $index; done
1
2
3
4
5
6
7
8
9
10

> 
for index in {f..a}; do echo $index; done
f
e
d
c
b
a


---

### Post by yanyan on 2008-04-02
Thanks so much.

---

