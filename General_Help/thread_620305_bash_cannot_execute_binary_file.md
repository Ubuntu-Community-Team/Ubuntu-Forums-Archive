---
title: "bash: cannot execute binary file"
date: 2007-11-22
forum: General Help
---

### Post by espressopigeon on 2007-11-22
I've installed Portable .Net on Xubuntu 7.10 to write C# programs. I used apt-get to install pnet and treecc, but I had to compile pnetlib because it was not in the repositories. I wrote a test program which compiled fine. I verified that I was in the correct directory, then ran:

**./a.out**

but got:

**bash: ./a.out: cannot execute binary file**

I verified I had execute permission. I tried compiling with the -o flag, I ran it with sudo and it turned everything I typed into crazy gibberish. Running file on a.out gave me this:

**a.out: MS-DOS executable PE  for MS Windows (console) Intel 80386 32-bit Mono/.Net assembly**

Is there a #! directive I need at the start of the file? Or is it something else entirely?

---

### Post by jaspreet on 2007-11-22
it is definatly not #! as you are compiling a C# program. Try using 

sh a.out

---

### Post by geirha on 2007-11-22
A search on google suggests that you should run it using ilrun. ```
ilrun a.out
```

[http://pwet.fr/man/linux/commandes/ilrun](http://pwet.fr/man/linux/commandes/ilrun)

---

### Post by espressopigeon on 2007-11-23
Ilrun worked! Thanks!

---

