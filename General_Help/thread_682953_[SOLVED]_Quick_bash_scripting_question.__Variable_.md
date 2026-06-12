---
title: "[SOLVED] Quick bash scripting question.  Variable use."
date: 2008-01-30
forum: General Help
---

### Post by zyberwoof on 2008-01-30
I am writing a script and am stuck on a small problem.

When I run it like this it works:
```
sed -n ';1p' 01name.tmp2 > temp.tmp 
```

However, when I am running this, I need to use a variable.  Thus I am replacing ';1p' with $foo.
```
foo="';1p'"
sed -n $foo 01name.tmp2 > temp.tmp
```

But this keeps throwing an error: 
```
sed: -e expression #1, char 1: unknown command: `''
```

The only difference between the two pieces of code is the fact that I am trying to put in some text as a variable.  How can I run this command by using this variable?

---

### Post by heindsight on 2008-01-30
When you run it like this:
```
sed -n ';1p' 01name.tmp2 > temp.tmp
``` the shell strips off the quotes around ;1p before passing it to sed, whereas when you do:
```
foo="';1p'"
sed -n $foo 01name.tmp2 > temp.tmp
```
the string ';1p' gets passed to sed (without the quotes being stripped off first).

Try doing it like this instead:
```
foo=";1p"
sed -n $foo 01name.tmp2 > temp.tmp
```

---

### Post by zyberwoof on 2008-01-30
Thanks a lot.  That was just what I needed!

---

### Post by bilge.tutak on 2008-01-30
I think since there is no type in Shell scripts, you can safely ignore the single quotes and just do:
foo="abc"

---

