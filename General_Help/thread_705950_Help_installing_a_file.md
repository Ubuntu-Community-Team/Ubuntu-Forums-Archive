---
title: "Help installing a file"
date: 2008-02-23
forum: General Help
---

### Post by allsop207 on 2008-02-23
Hi, I saw this 2d physics simulation program on youtube called Phun. I went to the site and downloaded the 32bit linux version, but I dont know how to install it. I was wondering if there is a command I can use or something to install this. I am running ubuntu 7.10.
Please help, I am very very eager to start playing.
file:///home/allsop207/Desktop/Phun_beta_3_linux32.tar.bz2
This is the file before I unpacked it.

---

### Post by taurus on 2008-02-23
Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvjf Phun_beta_3_linux32.tar.bz2
```
That would unpack the file.  Now, you need to change into the new directory, could be Phun_beta_3_linux32, and read the INSTALL or README on how to install it.

```
cd Phun_beta_3_linux32
cat INSTALL
```

---

