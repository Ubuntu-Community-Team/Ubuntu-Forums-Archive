---
title: "How to Update kernel?"
date: 2006-10-16
forum: General Help
---

### Post by wolf202 on 2006-10-16
Ok I'm running a AMD Athlon64 3000+ I'm currently running a 386 kernel

Is there a kernel for the amd 64? and how do I update to it.

-wolf

---

### Post by wolf202 on 2006-10-16
this has got to be an easy question!  -wolf

---

### Post by moore.bryan on 2006-10-16
[I]easy question, complicated answers.  if you want to stick with what is, almost, guaranteed to work... check the repos.  doing a simple search on [ubuntu's package site]("http://packages.ubuntu.com") lists many different amd64 "flavors;" you just have to pick the right one.  

option two is to compile one yourself from the [kernel.org]("http://www.kernel.org") folks.  there are plenty of wiki's and threads on that.

if you need more specifics on how to do it, post exactly what you're looking for...
[/I]

---

### Post by az on 2006-10-16
> **wolf202 said:**
> 
Is there a kernel for the amd 64? and how do I update to it.

-wolf

To go from 32 bit to 64 bit is more complicated than just updating your kernel.  You will need the k8 kernel, but you would have to recompile all your binaries to 64 bit.  You should reinstall using the 64-bit version of Ubuntu.

---

