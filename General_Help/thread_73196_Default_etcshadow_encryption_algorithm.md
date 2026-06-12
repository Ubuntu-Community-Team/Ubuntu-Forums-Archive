---
title: "Default /etc/shadow encryption algorithm"
date: 2005-10-08
forum: General Help
---

### Post by mlopes on 2005-10-08
Hi. I need to know which is Ubuntu's Hoary default encryption algorithm. I need to generate passwords for /etc/shadow outside the system so I need to know the algorithm. And by the way, is there an online encrypter for it? It would spare me some work!

Thansk in advance :-)

---

### Post by joerite on 2006-12-05
yeah I would like to know this to. You could encrypt your password with different functions and compare it to the hash in the shadow file. But if someone knows that be easier.

---

### Post by komputes on 2008-05-05
JLd6cq2dYyKR6 is apparently equal to an empty password. To answer your inquiry, there are two types of passwords: DES and MD5. 

md5 being stronger, and you can tell distinctly tell them apart. If the string starts with $1$, it's an MD5. The makepasswd command allow you to set a password from another computer. If you would like to create a DES password simply run perl -e 'print crypt "mypassword"'

---

