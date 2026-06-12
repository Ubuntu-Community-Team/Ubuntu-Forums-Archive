---
title: "cdemu problems"
date: 2005-07-13
forum: General Help
---

### Post by user on 2005-07-13
ok i already did apt-get update and got the newest gcc too.
first i extracted what's in the compressed file and, as the manual says, did 
```
/lib/modules/2.6.10-5-386/build/include
```
but i get 
```
No such file or directory
```
so i did
```
/lib/modules/2.6.10-5-386 /build/include
```
then i got 
```
bash: /lib/modules/2.6.10-5-386: is a directory
```

well, after that i did "make" and i got this messege;
```
make: *** No rule to make target `cdemu.ko', needed by `modules'.  Stop.
```, both cases.
so... what should i do?

---

