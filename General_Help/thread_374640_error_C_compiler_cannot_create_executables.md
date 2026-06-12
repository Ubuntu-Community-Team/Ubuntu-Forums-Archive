---
title: "error: C compiler cannot create executables"
date: 2007-03-02
forum: General Help
---

### Post by Astral Abraxas on 2007-03-02
how do I fix this problem? I am trying to install "recordmydesktop" and I get that error.

---

### Post by taurus on 2007-03-02
```
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by Astral Abraxas on 2007-03-02
ah thank you. now im getting a 'make' error: 

> 
../include/rmdfunc.h:465: error: expected declaration specifiers or ‘...’ before ‘gzFile’
../include/rmdfunc.h:481: error: expected declaration specifiers or ‘...’ before ‘gzFile’
make[2]: *** [recordmydesktop-recordmydesktop.o] Error 1
make[2]: Leaving directory `/home/kos-mos/Desktop/recordmydesktop-0.3.3.1/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kos-mos/Desktop/recordmydesktop-0.3.3.1'
make: *** [all] Error 2


---

### Post by mavx on 2007-03-03
Thank you, Taurus. I also had the same problem and that solved it wonderfully. :)

---

### Post by keerikkadan on 2007-03-12
very good sudo aptitude works

---

