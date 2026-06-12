---
title: "How do you link to old libraries?"
date: 2006-08-31
forum: General Help
---

### Post by jsmidt on 2006-08-31
I am trying to install maple on my Ubuntu system.  It is a few years old so looks for and old kernal and libraries.  To solve the kernal problem I just do:

```
export LD_ASSUME_KERNEL=2.4.1
```

Now it wants old libraries.  It gives this error:

```

/usr/local/maple/bin.IBM_INTEL_LINUX/maplew: error while loading shared libraries: libstdc++-libc6.1-1.so.2: cannot open shared object file: No such file or directory


```

What library is that?  What is the modern day equivilent and how do I link to it?

---

### Post by kerry_s on 2006-08-31
just open synaptic and do a search for libc6 and libstdc , i think you need the dev, but there are several to choose from for both, so you'll have to look for yourself and see what you need.

---

