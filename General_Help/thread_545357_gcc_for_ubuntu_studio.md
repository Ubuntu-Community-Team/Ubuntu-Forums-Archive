---
title: "gcc for ubuntu studio"
date: 2007-09-07
forum: General Help
---

### Post by Mango_21 on 2007-09-07
[RESOLVED]hello..
i just recently installed ubuntu studio.....wrote a small c program....tried to compile it ...gives me an error..
1.c:1:18: error: stdio.h: No such file or directory


i tried installing the gcc package from synaptic manager....it still doesnt work..:(
i later tried apt-get install build-essentials....again gives me a error..
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essentials

i tried installing the   libgcc1_4.2.1-5ubuntu1_i386.deb    package.....says i'm missing some dependencies....

i also tried libc6-udeb_2.3.2.ds1-22sarge6_i386.udeb .....it says im missing the libnss-dns-udeb dependency 

what is easiest way to make this work?

please if some one could help ...i wud be really greatful...

If anyone could tell me how i could tell me how to  install python imaging library as well..i wud really appreciate it....thank you

---

### Post by RedSquirrel on 2007-09-07
The package is called **build-essential**. (no "s" at the end)

```
sudo apt-get install build-essential
```

---

### Post by raul_ on 2007-09-07
you can always do a search in synaptic for "gcc" or "build" and then scan the results there. The problem with using terminal package management programs is that you don't have the same notion of the available packages. and what their correct names are.

---

### Post by RedSquirrel on 2007-09-08
> **raul_ said:**
> you can always do a search in synaptic for "gcc" or "build" and then scan the results there. The problem with using terminal package management programs is that you don't have the same notion of the available packages. and what their correct names are.
This guide is helpful for learning how to search the repositories and check package details on the command line:

[https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)

---

### Post by Mango_21 on 2007-09-10
hey....thanks a ton guys.....loaded libc6 from the synaptic manger....solved everything.....thanks once again//

---

### Post by Maestro23 on 2007-09-10
> **Mango_21 said:**
> hey....thanks a ton guys.....loaded libc6 from the synaptic manger....solved everything.....thanks once again//

Good deal man.  Can you go back to your 1st post, and edit it to RESOLVED.

Glad you got everything figured out.

---

