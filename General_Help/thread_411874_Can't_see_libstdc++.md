---
title: "Can't see libstdc++"
date: 2007-04-17
forum: General Help
---

### Post by copepod on 2007-04-17
I'm using Edgy and I can't reference libstdc++ methods during a compile.  My gcc is 6.4.1-dev and libstdc++5 and 5.3.3-dev.  I'm getting tons of 

undefined reference to `std::basic ...

Has anyone seen this or know how my compiler can find these libstdc++ references?


David (copepod):guitar:

---

### Post by copepod on 2007-04-17
I fixed this.  I needed to install libtool.  That was it.



David (copepod)

---

