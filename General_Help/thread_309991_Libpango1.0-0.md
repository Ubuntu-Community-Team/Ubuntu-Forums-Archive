---
title: "Libpango1.0-0"
date: 2006-11-30
forum: General Help
---

### Post by subiet on 2006-11-30
While installing/compiling a lot of packages, i get an error which says "Dependency is not satisfiable: libpango1.0-0", i am running dapper draker 6.06 LTS 32bit on a 64bit amd athlon 3000+.

I have installed "libpango1.0-0,libpango1.0-0-dbg,libpango1.0-0-common,libpango1.0-0-dev, libpango1.0-0-doc,libpango1 ruby" via synaptics, and it also shows in synaptics that it is installed, but yet the packages give me the error mentioned above.

any help would be greatly appreciated.

---

### Post by LLRNR on 2006-11-30
I don't know what exactly you're trying to compile... Usually it's better to use already compiled packages, since the ones you have to compile yourself from different sources are often betas / buggy / unreliable.

Regardless, if you still need to compile something, maybe taking a look at the following articles might give you a clue on what you need to do:

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

and

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

LLRNR

---

### Post by subiet on 2006-11-30
Oh no, even if i use per built package, the error is still there, and i generally don't have much problems with compiling softwares, have done it number of times for various softwares.
It is this libpango1.0-0 which even after being there, shows that it isn't there to the software when he demands it. how do i correct this?

---

### Post by Adramelech on 2006-11-30
maybe you have to mess with the configure file, and look what package is looking for.

I guess your pkg-config is looking for a file that doesnt exist. If i were at your position i will check the .pc file and compare it with the one requested on configure.

---

