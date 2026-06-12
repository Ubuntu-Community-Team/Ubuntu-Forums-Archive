---
title: "How can i download/install TOFRODOS package for ubuntu 7.04"
date: 2007-10-09
forum: General Help
---

### Post by Stylized on 2007-10-09
Hi everybody!

i'm trying to use one of the **tofrodos** functions
and when i using it it writes
that i must install the tofrodos program

and when i type:
```
sudo apt-get install tofrodos
```
it writes:
> E: Couldn't find package tofrodos

so.. why it is not found and how can i get it and install it?

---

### Post by por100pre1 on 2007-10-09
It should be there.

```
gksudo software-properties-gtk
```

Check that **main** repository is enabled, check universe, restricted and multiverse too. :-k

```
cat /etc/apt/sources.list
```

post the results.

---

### Post by Stylized on 2007-10-09
i can't find it 
maybe its because i started using linux only todat.. =\
any other ways?

---

### Post by por100pre1 on 2007-10-09
Ok, let's try it again. Open **System> Administration> Software Properties**, after typing your password [this]("http://img156.imageshack.us/img156/1118/repos03am2.png") window should appear. Check everything but "Source Code".

---

