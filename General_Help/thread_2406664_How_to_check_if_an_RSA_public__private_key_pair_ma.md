---
title: "How to check if an RSA public / private key pair match"
date: 2018-11-23
forum: General Help
---

### Post by dilbert_one on 2018-11-23
How to check if an RSA public / private key pair match

I have two files, id_rsa and id_rsa.pub. What command can be used to validate if they are a valid pair?

 i have tested this way: 

 ssh-keygen -y -e -f <private key>



[martin@martin-pc ~]$ ssh-keygen -y -e -f <private key>
bash: Syntaxfehler beim unerwarteten Wort `newline'
[martin@martin-pc ~]$ 

why do i get this error ?!

---

### Post by wildmanne39 on 2018-11-23
*Thread moved to **General Help for a more appropriate fit**.*

---

