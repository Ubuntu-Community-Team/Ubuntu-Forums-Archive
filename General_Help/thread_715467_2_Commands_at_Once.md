---
title: "2 Commands at Once"
date: 2008-03-04
forum: General Help
---

### Post by psychofish25 on 2008-03-04
I don't care about how practical it is, I was just wondering how I could run two terminal commands in one line. 

Thanks,
Jordan

---

### Post by taurus on 2008-03-04
```
first_command; second_command
```
or
```
first_command && second_ command
```

---

### Post by bodhi.zazen on 2008-03-04
There are other options as well, pipes and ||

command 1 | command 2

command 1 || command 2

And you can background commands 

command 1&
command 2 &

=======

&& = run command 2 if command 1 runs w/o error (logical and)

|| = run command 2 if command 1 fails (logical or)

& = run in background

| = send output of command 1 to command 2


HTH with your understanding of your options, I am probably forgetting some :twisted:

---

