---
title: "What is LSB module ?"
date: 2021-06-21
forum: General Help
---

### Post by anneranch on 2021-06-21
qs@qs-desktop:~$  lsb_release -a  
No LSB modules are available. 
Distributor ID:    Ubuntu 
Description:    Ubuntu 21.04 
Release:    21.04 
Codename:    hirsute 
qs@qs-desktop:~$ apt-get install lsb-core 

After checking $  lsb_release -a  I got 
No LSB modules are available.

Then I run   apt-get install lsb-core
and more software  ( packages) got installed 
I guess 
sudo apt updated missed them 

BUT 
I cannot find **what is "LSB"  module?**

---

### Post by grahammechanical on 2021-06-21
LSB = Linux Standard Base.

---

### Post by ActionParsnip on 2021-06-21
Good starting place
[https://en.wikipedia.org/wiki/Linux_Standard_Base](https://en.wikipedia.org/wiki/Linux_Standard_Base)

---

