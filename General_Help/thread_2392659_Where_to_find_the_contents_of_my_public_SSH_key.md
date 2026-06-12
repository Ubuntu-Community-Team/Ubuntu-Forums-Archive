---
title: "Where to find the contents of my public SSH key"
date: 2018-05-23
forum: General Help
---

### Post by jl2414 on 2018-05-23
I have a SSH key located at "Passwords and Keys" -> "OpenSSH keys".

I'm able to see "Properties" -> "Key" and "Details" of my "Personal SSH key".

But where do I find the information: **contents of my public SSH key**?

---

### Post by deadflowr on 2018-05-23
look in ~/.ssh

---

### Post by jl2414 on 2018-05-23
I opened: Terminal and wrote: ~/.ssh

and the result:
 xyz@xyz-HP-Pavilion-Sleekbook-15:~$ ~/.ssh 
bash: /home/xyz/.ssh: Is a directory

Is this it?
If not pleas specify, because I'm a newbie in Ubuntu.

---

### Post by deadflowr on 2018-05-23
try
```
ls ~/.ssh
```
should output something like
id_rsa id_rsa.pub known_hosts 
id_rsa.pub is the public key
(Or anything that ends in .pub should be the public key)

---

