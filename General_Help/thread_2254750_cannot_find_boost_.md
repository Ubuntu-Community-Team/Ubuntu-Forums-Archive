---
title: "cannot find boost_*"
date: 2014-11-29
forum: General Help
---

### Post by ELMIT on 2014-11-29
How can I fix this error:

> /usr/bin/ld: cannot find -lboost_system-mgw48-mt-s-1_55
/usr/bin/ld: cannot find -lboost_filesystem-mgw48-mt-s-1_55
/usr/bin/ld: cannot find -lboost_program_options-mgw48-mt-s-1_55
/usr/bin/ld: cannot find -lboost_thread-mgw48-mt-s-1_55
collect2: error: ld returned 1 exit status


---

### Post by steeldriver on 2014-11-29
Can you give us some context here? are you trying to cross-compile something using a mingw toolchain?

---

### Post by ELMIT on 2014-11-29
I cannot tell you much more than what I try to do. I downloaded the source of the coin quatloocoin from [https://github.com/quatloos/quatloo](https://github.com/quatloos/quatloo) and want to compile the wallet:

git clone [https://github.com/quatloos/quatloo](https://github.com/quatloos/quatloo)
cd quatloo
qmake-qt4
make

---

