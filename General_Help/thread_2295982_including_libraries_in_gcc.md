---
title: "including libraries in gcc"
date: 2015-09-22
forum: General Help
---

### Post by Zombir on 2015-09-22
Dear all,

I'm trying to compile an OpenCL program by following a tutorial. The compile line is as follows:

```
gcc -ocl-demo cl-demo.c cl-helper.c -lrt -lOpenCL
```

But then I get the error message:

```
/usr/bin/ld: cannot find -lOpenCL
collect2: error: ld returned 1 exit status
```

I searched for the term OpenCL in my computer and came up with the following results:

libOpenCL.so.1 : in /usr/lib/i386-linux-gnu
libOpenCL.so.1 : in /usr/lib/x86_64-linux-gnu
libOpenCL.so.1.0 : in /usr/lib/i386-linux-gnu
libOpenCL.so.1.0 : in /usr/lib/x86_64-linux-gnu

So I edited my compilation line as follows:

```
gcc -L/usr/lib/x86_64-linux-gnu -ocl-demo cl-demo.c cl-helper.c -lrt -lOpenCL
```

But I still get the same problem. 

Am I missing an so file or do I have to do something else to get these so file to work?

Thank you

---

### Post by TheFu on 2015-09-23
Try

```

gcc -o cl-demo cl-demo.c cl-helper.c -lrt -L/usr/lib/x86_64-linux-gnu  -lOpenCL
```
or

```

gcc -o cl-demo cl-demo.c cl-helper.c -lrt -l/usr/lib/x86_64-linux-gnu/libOpenCL.so.1
```

Actually ... I'd use a makefile to do compiles first, then linking in a 2nd step.  
```
gcc -c cl-demo.c 
gcc -c cl-helper.c
gcc -o cl-demo cl-demo.o cl-helper.o -lrt -L/usr/lib/x86_64-linux-gnu  -lOpenCL
```

---

