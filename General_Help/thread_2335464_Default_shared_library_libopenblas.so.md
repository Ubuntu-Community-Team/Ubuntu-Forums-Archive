---
title: "Default shared library libopenblas.so"
date: 2016-08-29
forum: General Help
---

### Post by nestarneal on 2016-08-29
Hello everyone, 

My question is what is the difference between Ubuntu default shared library
and the one provided by [http://www.openblas.net/](http://www.openblas.net/) ?

I find that there is a shared library file libopenblas.so in /usr/lib.
And I can use such as cblas_dgemm function to perform matrix-matrix multiply operation.

I try to modify the details inside it, so I download the source code from [http://www.openblas.net/](http://www.openblas.net/)
and build libopenblas.so in /opt/OpenBLAS/lib.

But I'll get the error message "Illegal instruction (core dumped)" when I make my program link
with /opt/OpenBLAS/lib/libopenblas.so (built by myself from source code).
And I'll get correct output when I make my program link with /usr/lib/libopenblas.so (Ubuntu default).

What is the difference between them?

Many thanks.

---

