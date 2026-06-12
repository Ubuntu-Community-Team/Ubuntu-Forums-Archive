---
title: "Making internal variables"
date: 2008-04-15
forum: General Help
---

### Post by psychofish25 on 2008-04-15
I know how Ubuntu has some built in variables like $HOME and others. I was wondering how I could make my own or a file that has all off them listed.

---

### Post by pointone on 2008-04-16
```
env
```

You can assign a variable in BASH as easy as any other language.

```
TEST=Hello
echo $TEST
```

If you want variables to be permanently set, you can *export* them in your .bashrc:

```
export TEST=Hello
```

---

