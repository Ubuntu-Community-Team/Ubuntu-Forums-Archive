---
title: "Octave Control Package error"
date: 2015-10-24
forum: General Help
---

### Post by lucas51 on 2015-10-24
Hi everyone, im trying to use the octave control package in ubuntu 15.10 (32-bits) but it doesnt seem to work cause this error shows up every time i try to use a fuction of this package

error: issample: /usr/lib/i386-linux-gnu/octave/packages/control-2.8.3/i686-pc-linux-gnu-api-v50+/is_real_scalar.oct: failed to load: /usr/lib/i386-linux-gnu/octave/packages/control-2.8.3/i686-pc-linux-gnu-api-v50+/is_real_scalar.oct: undefined symbol: _ZNK5ArrayISsE17resize_fill_valueEv
error: called from
    issample at line 65 column 12
    lqr at line 92 column 3
    observador at line 154 column 2

''observador'' is the name of my m-file.

Can anyone help me please?!

Thanks a lot

---

### Post by Eric_Fraga on 2015-10-30
Just to add that I have also run into this problem, albeit from a different Octave function:

```
error: parcellfun: /usr/lib/i386-linux-gnu/octave/packages/parallel-3.0.0/i686-pc-linux-gnu-api-v50+/fload.oct: failed to load: /usr/lib/i386-linux-gnu/octave/packages/parallel-3.0.0/i686-pc-linux-gnu-api-v50+/fload.oct: undefined symbol: _ZNK5ArrayISsE17resize_fill_valueEv

```

This is on a recently upgraded system (wily release).

---

### Post by lucas51 on 2015-10-30
I've installed the packages via ubuntu terminal (sudo apt-get install octave-package), that was the mistake.
After reinstalling the packages via octave terminal it worked fine (pkg install -forge package)

try this, maybe it works for u too.

---

### Post by Bucky Ball on 2015-10-30
Welcome. Good news. Please mark the thread as solved by following the first link in my signature. 

@ Eric_Fraga: If lucas51's solution doesn't work for you, please post a new thread with a descriptive title and give as much detail as you can about your problem. This will greatly improve your chances of support as yours is a different function, different error, different issue and this thread is now solved. Good luck. :)

---

### Post by Eric_Fraga on 2015-10-30
Thanks.  Installing packages from Octave directly seems to do the job.  I appreciate your advice to start a new thread but the issue is in fact the same one: there is an incompatibility with the compilation of the individual octave-* packages in the standard repositories with what octave itself expects.  Why, I don't know, but I know it has been mentioned in one or other of the octave forums.

Anyway, installing from octave directly works fine (once I installed libgnutls-dev; why Octave needs this is unclear but there you are).

Thanks again,
eric

---

