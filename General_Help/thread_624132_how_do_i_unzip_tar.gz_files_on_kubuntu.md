---
title: "how do i unzip tar.gz files on kubuntu?"
date: 2007-11-26
forum: General Help
---

### Post by zivxx on 2007-11-26
hey guys..ive got few tar.gz files i can't extract...anyone know whats the problem or maybe if i can install them without extracting?

---

### Post by skyjacker on 2007-11-26
> **zivxx said:**
> hey guys..ive got few tar.gz files i can't extract...anyone know whats the problem or maybe if i can install them without extracting?

```
tar -zxvf <tarfile>
```
Go in to the new directory:
```
cd <newdirname>
```
Read the README or INSTALL file

To compile and install, just execute:

```
./configure
```
```
make
```
```
make test
```
```
make install
```

---

