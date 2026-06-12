---
title: "help installing ophcrack..."
date: 2007-08-01
forum: General Help
---

### Post by Mia_tech on 2007-08-01
after downloading ophcrack and trying to compile a get this error, may be someone has come across this before...... this is during ./configure

checking openssl/ssl.h usability... no
checking openssl/ssl.h presence... no
checking for openssl/ssl.h... no
configure: error: header file <openssl/ssl.h> is required for OpenSSL

thanks in advance

---

### Post by jpeddicord on 2007-08-04
Hi there,

This error should be solved with the following line in a terminal:

```
sudo apt-get build-dep ophcrack
```
When that is finished, run ./configure again. :)

Jacob

---

### Post by Mia_tech on 2007-08-07
> **jacobmp92 said:**
> Hi there,

This error should be solved with the following line in a terminal:

```
sudo apt-get build-dep ophcrack
```
When that is finished, run ./configure again. :)

Jacob

this is what I got..........still trying

jorge@ubuntu-box:~/programs/ophcrack-2.4$ sudo apt-get build-dep ophcrack
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for ophcrack

---

### Post by sefs on 2007-08-07
out of curiosity is the advantage over the LiveCD?

---

### Post by Mia_tech on 2007-08-09
you can use on remote systems without having to boot from it

---

