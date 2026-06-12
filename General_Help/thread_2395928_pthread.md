---
title: "pthread"
date: 2018-07-08
forum: General Help
---

### Post by sundaresh on 2018-07-08
How do I link with the pthread library ?

---

### Post by QIII on 2018-07-08
Hello!

It would be helpful if you could give us a bit of detail about your intent.

---

### Post by steeldriver on 2018-07-08
At least for gcc, the recommended way AFAIK is to add the -pthread option to both the compile and link phases

```

       -pthread
           Adds support for multithreading with the pthreads library.  This
           option sets flags for both the preprocessor and linker.

```

---

