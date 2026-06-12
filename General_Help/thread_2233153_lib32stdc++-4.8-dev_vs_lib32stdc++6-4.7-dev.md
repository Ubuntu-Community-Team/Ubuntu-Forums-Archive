---
title: "lib32stdc++-4.8-dev vs lib32stdc++6-4.7-dev"
date: 2014-07-06
forum: General Help
---

### Post by elindarie on 2014-07-06
What is the difference between lib32stdc++-4.8-dev and lib32stdc++6-4.7-dev ?

I had to install lib32stdc++ because I have 64-bit Ubuntu 14.04, but the Brother printer driver I want to install for the DCP-8155DN was originally written for a 32-bit OS.  The Ubuntu Software Center showed lib32stdc++-4.8-dev and lib32stdc++6-4.7-dev, so I installed both because I have no clue what the difference is.  I hope this does not cause a conflict.

I didn't see any clues in these descriptions:

[http://packages.ubuntu.com/trusty/libdevel/lib32stdc++-4.8-dev](http://packages.ubuntu.com/trusty/libdevel/lib32stdc++-4.8-dev)

[http://packages.ubuntu.com/trusty/libdevel/lib32stdc++6-4.7-dev](http://packages.ubuntu.com/trusty/libdevel/lib32stdc++6-4.7-dev)

Does anybody know?  Is anybody familiar with the naming convention, who could describe it, and perhaps post a link to documentation?

Thank you.

---

### Post by slooksterpsv on 2014-07-10
Don't take my word for this, but here's what I believe are the differences.
stdc++ 4.8 vs 4.7

They're updates for compilation support for certain C++11 conventions (as well as C++0x etc.) - [https://gcc.gnu.org/projects/cxx0x.html](https://gcc.gnu.org/projects/cxx0x.html)

The EXACT changes, I'm not sure of. But it has something to do with supporting newer version of C++, libraries, and such.

---

