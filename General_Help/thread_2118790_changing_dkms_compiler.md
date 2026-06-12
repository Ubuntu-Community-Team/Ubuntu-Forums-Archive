---
title: "changing dkms compiler"
date: 2013-02-22
forum: General Help
---

### Post by birty on 2013-02-22
I have changed my gcc/g++ symlinks to point at clang. This works fine for most things but clang isn't yet able to build the kernel. This means that every time I install a kernel update my dkms modules (specifically virtual box guest additions) fail to compile and I have to manually reinstall them. Is it possible to make dkms use gcc-4.7 instead of gcc so that it isn't trying to use clang?

---

### Post by dino99 on 2013-02-22
about new kernel & virtualbox:

[http://www.tuxtrix.com/2013/02/how-to-install-virtualbox-guest.html](http://www.tuxtrix.com/2013/02/how-to-install-virtualbox-guest.html)

[http://www.google.fr/#q=gcc+4.7+using+clang&hl=fr&source=lnt&tbs=qdr:y&sa=X&ei=21MnUfTMJaKj0QWrtYH4DQ&ved=0CB8QpwUoBQ&bav=on.2,or.r_gc.r_pw.r_qf.&fp=f4865e32faa9e3f4&biw=1674&bih=893](http://www.google.fr/#q=gcc+4.7+using+clang&hl=fr&source=lnt&tbs=qdr:y&sa=X&ei=21MnUfTMJaKj0QWrtYH4DQ&ved=0CB8QpwUoBQ&bav=on.2,or.r_gc.r_pw.r_qf.&fp=f4865e32faa9e3f4&biw=1674&bih=893)

---

### Post by birty on 2013-02-22
I'm not having any problems compiling the virtual box additions with gcc, the automated installer works perfectly if I have the gcc symlink pointing to gcc. I was asking whether it's possible to specify the compiler that dkms uses (e.g. gcc-4.7 rather than just gcc)

---

