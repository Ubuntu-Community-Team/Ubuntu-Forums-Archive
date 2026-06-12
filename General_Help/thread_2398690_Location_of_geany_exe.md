---
title: "Location of geany exe"
date: 2018-08-15
forum: General Help
---

### Post by raleigh3 on 2018-08-15
I am trying to find where the geany exe is located.

Tried which and whereis with no luck.

---

### Post by oldfred on 2018-08-15
the .exe is a Windows file, Linux does not use .exe.

fred@bionic-z97:~$ whereis geany
geany: /usr/bin/geany /usr/lib/x86_64-linux-gnu/geany /usr/include/geany /usr/share/geany /usr/share/man/man1/geany.1.gz

---

### Post by raleigh3 on 2018-08-16
I know that. 

Linux use the elf format for many programs.

geany.1.gz is not the Geany program that runs.

---

### Post by sudodus on 2018-08-16
```

$ which geany
/usr/bin/geany
$ ls -l /usr/bin/geany
-rwxr-xr-x 1 root root 6136 jan  8  2018 /usr/bin/geany

```

---

### Post by The Cog on 2018-08-16
A huge majority of the executables you use will be found in /bin, /usr/bin or /usr/sbin. 
Shared Objects (like windows DLLs) are often in /lib or /usr/lib.
geany.1.gz is the manual text.

---

