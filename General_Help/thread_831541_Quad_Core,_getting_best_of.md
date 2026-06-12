---
title: "Quad Core, getting best of"
date: 2008-06-16
forum: General Help
---

### Post by malfist on 2008-06-16
I just purchased an AMD Phenom 9850 and was wondering how I can get the best performance from it on Ubuntu?

Thanks,
Malfist

---

### Post by sdennie on 2008-06-16
You shouldn't have to do anything to take advantage of the CPU.  Most apps are still essentially single threaded but, one common thing I can think of that will greatly benefit from multiple cores is compiling software.  If you are compiling things with make, you should be able to build things with -j4 (or probably higher).  Or, if you are building a kernel with make-kpkg, you can prefix it with CONCURRENCY_LEVEL=4 (or higher) to take advantage of your CPU.  Of course, if you don't build software, none of that is useful.  :)

---

### Post by malfist on 2008-06-17
I do a lot of compiling but it's mostly my pet projects and they are (almost) all in Java. If I recompile the kernel with the concurrency level will it improve performance?

---

### Post by FuturePilot on 2008-06-17
You may see some performance improvement, but for the trouble you have to go through to compile your own kernel I don't think it's worth it. On a binary distribution like Ubuntu, compiling your own kernel is messy business especially when it comes to updates.

---

### Post by sdennie on 2008-06-17
Depending on how you compile your Java code, there may be options for building it in parallel.  It's something to look into.

As FuturePilot said, it's probably not worth the hassle to compile your own kernel.  I was just pointing out that if it's something you do, you can greatly speedup the compilation with a quadcore.

---

### Post by bingoUV on 2008-06-17
> **malfist said:**
> I do a lot of compiling but it's mostly my pet projects and they are (almost) all in Java. If I recompile the kernel with the concurrency level will it improve performance?

No, kernel already has what it needs to have to support 4 (even more actually) cores. The applications need to do be multi-threaded or multiple process'ed to take advantage of it. But it is not necessary as even if you have only single threaded applications, you can run 4 of them together and still have a responsive system. e.g. all these in parallel : 
1. Listening to music
2. Encoding a video
3. Browsing the web with javascript heavy webpages
4. Compiling java programs.

Since some of the above applications do not need a whole CPU core, you can do more than this and still have a responsive system.

---

### Post by malfist on 2008-06-18
> **bingoUV said:**
> 
3. Browsing the web with javascript heavy webpages


Yey! Now I can browse my own webpage! Jesus, my boss is crazy with what she want's javascript to do. (really, it's not that bad, just a lot of javascript but my lappy can handle it).

---

