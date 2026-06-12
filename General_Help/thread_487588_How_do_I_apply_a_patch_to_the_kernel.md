---
title: "How do I apply a patch to the kernel?"
date: 2007-06-29
forum: General Help
---

### Post by Scorpuk on 2007-06-29
I would like to add UDF 2.5 support to my box and to do that I think I need to run the following file somehow:

UDF-2.50_linux-2.6.20.patch


FYI:

Kernel Version 2.6.20-16-generic (SMP) 
Distro Name  Ubuntu 7.04 


So my question is how do I run a .patch file?


Cheers.

---

### Post by tronica on 2007-06-29
you have to recompile your kernel and add your patch, heres a great howto 

[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by Scorpuk on 2007-06-30
Cheers.

Looks complicated, but I'll give it a go when I'm next home. :o


I think I need to download kernel source 2.6.20 to apply the patch: 

([http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.20.tar.gz](http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.20.tar.gz))

and then carry on from there.


Wish me luck  [-o<

---

### Post by Scorpuk on 2007-06-30
Just been reading the instructions from the abpve link and just would like some clarification on the following matter...


The guide talks about a patch called patch.bz2 and uses a program called bzip2. I presume bzip2 is used as the extension of the patch in the guide is bz2.



Now how will this guide work with my patch since it has the extension .patch and .bz2?



If you need to see the structure of the file I have attached it, but changed the extension to .txt to allow me to upload it.


Cheers.

---

