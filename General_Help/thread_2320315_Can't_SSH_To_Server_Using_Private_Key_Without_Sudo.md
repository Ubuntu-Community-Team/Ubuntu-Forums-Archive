---
title: "Can't SSH To Server Using Private Key Without Sudo"
date: 2016-04-12
forum: General Help
---

### Post by barrycarey on 2016-04-12
Hey All,

For some reason I'm unable to SSH from my Ubuntu 15.10 machine to a remote server using a private key if I run ssh without sudo.

Server side config is fine.  I have tested the private key from my Windows machine and from a CentOS box and both can use it.

If I put the private key in ~/.ssh authentication fails and I'm prompted for a password. However, if I put the same private key in /root/.ssh and use sudo ssh I can connect as normal. 

I did notice this in the verbose SSH output. 

Without Sudo: Offering RSA public key: /home/matt/.ssh/id_rsaWith Sudo: Trying private key: /root/.ssh/id_rsa

Prior to that line output is the same. 

Using the root .ssh directory isn't the end of the world but this doesn't seem correct. 

Does anyone know why it's not working with the ssh key in my user's home directory?

---

### Post by HermanAB on 2016-04-12
SHH is very particular about ownership and permissions.

chown username: keyfilename
chmod 600 keyfilename

---

### Post by TheFu on 2016-04-13
And the ~/.ssh/ directory needs to be 700 permissions.

Improper use of sudo can cause all sorts of issues.

---

