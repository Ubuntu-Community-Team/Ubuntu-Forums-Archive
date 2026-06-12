---
title: "Using openssh public key with Putty"
date: 2014-09-10
forum: General Help
---

### Post by ras123 on 2014-09-10
Hi,
I generated a ssh key pair as provided in [https://help.ubuntu.com/community/SSH/OpenSSH/Keys](https://help.ubuntu.com/community/SSH/OpenSSH/Keys)

Now I need to access this computer from a windows computer using Putty, how to load the public key generated in Linux machine in Putty? I couldn't find any option.

Thanking You,
Ras

---

### Post by ThatBum on 2014-09-11
You use the private key on the client and the public key on the server.

Also, putty uses its own format for keys, so you need to import the private key into puttygen and convert it into a .ppk

---

### Post by Frogs Hair on 2014-09-11
Looks like a support question, moved to ***General Help.***

---

### Post by ras123 on 2014-09-12
Thank you

---

