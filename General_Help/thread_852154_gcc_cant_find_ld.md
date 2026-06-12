---
title: "gcc cant find ld"
date: 2008-07-07
forum: General Help
---

### Post by sam159 on 2008-07-07
It seems the gcc cannot find ld when compiling anything.
ie "int main(void) { return 0; }"
```
$ gcc -o test test.c 
collect2: cannot find 'ld'
```
ld is installed and working
```
$ whereis ld
ld: /usr/bin/ld /usr/share/man/man1/ld.1.gz
$ ld
ld: no input files
```

??

---

