---
title: "trying to install Wine, but i get an error"
date: 2019-03-12
forum: General Help
---

### Post by drtechtek on 2019-03-12
trying to install Wine, but i get an error this error. 

E: Malformed entry 57 in list file /etc/apt/sources.list (Component)
E: The list of sources could not be read.

after i putted -sudo apt-add-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) cosmic main' 

how can i resolve this issue? 

Thank you all

---

### Post by jeremy31 on 2019-03-12
In terminal do ```
cat /etc/apt/sources.list | nc termbin.com 9999
```
Post URL

---

