---
title: "Compiling fortran using g++"
date: 2008-04-21
forum: General Help
---

### Post by davidY on 2008-04-21
Hello, I am trying to compile some fortran libraries to use with c++ code. Somebody told me that g++ works just fine: g++ -c *.f 

However, this command says in error messages: cannot exec f951. There is no package called f951, what should i do?

---

### Post by Vermind on 2008-04-21
Hello,
I never combined Fortran and C++,
but I compiled Fortran code with:
[G95]("http://www.g95.org/").
It might help.

---

### Post by amingv on 2008-04-21
Or you could use g77 if you want to use one from the GNU Compiler Collection. I think g77 uses gcc behind the scenes to compile, but I wouldn't know that much about it anyway

---

### Post by Xayma on 2008-04-23
g++ won't work as far as I know. gfortran is the relevant compilier from the gcc series. So if you have g++ you should have gfortran.

---

