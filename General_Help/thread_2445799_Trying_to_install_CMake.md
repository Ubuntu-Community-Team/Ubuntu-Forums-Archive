---
title: "Trying to install CMake"
date: 2020-06-19
forum: General Help
---

### Post by paulgureghian on 2020-06-19
my system is Ubuntu 20 on WSL and up to date.

[https://imgur.com/a/Pi5t9OL](https://imgur.com/a/Pi5t9OL)

---

### Post by CelticWarrior on 2020-06-19
The error is about missing openSSL, not CMake.

---

### Post by Yellow Pasque on 2020-06-19
Is there a reason you can't just use the version in the repo and have to build your own?

---

### Post by monkeybrain20122 on 2020-06-20
> **Yellow Pasque said:**
> Is there a reason you can't just use the version in the repo and have to build your own?

+1. Ubuntu 20.04 has cmake 3.16.3 which is recent enough. I have compiled cmake on Ubuntu 16.04 though, the repo version is too old for compiling newer software. cmake-3.14 is adequate for my purpose.

---

### Post by Yellow Pasque on 2020-06-20
And if, for some reason, you need to build latest cmake, this should fix the error:
```
sudo apt-get install libssl-dev
```

---

