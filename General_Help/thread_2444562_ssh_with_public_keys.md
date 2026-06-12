---
title: "ssh with public keys"
date: 2020-06-01
forum: General Help
---

### Post by Hotchilli on 2020-06-01
i set up a ssh login and created a set of keys then installed them on the server with ssh-copy-id command they were installed on server 
the keys are in my home directory .ssh
then disabled password login on the server
but when i try to login with ssh ssh root@myremoteserver -p5422

i get
Permission denied (publickey).

or if i try
ssh -i ~/.ssh/id_rsa.pub root@myremoteserver -p5422

i get the same

---

### Post by TheFu on 2020-06-01
Ubuntu doesn't allow remote root access. We use sudo.   Keys are per account.
Try, from the client with the private key (using the specific account used to create the ed25519 key:
```
$ ssh -p5422  hotchilli@myremoteserver
```

RSA keys are being deprecated. Really shouldn't be used anymore.  usernames and servernames should be lowercase, not mixed, not upper.  There are reasons.

~/.ssh/id_rsa.pub is the public key. That won't work.

If you post the EXACT commands used to create and push the keys, we may see the flaw.

---

### Post by Hotchilli on 2020-06-01
here is what i did i am in ubuntu as client remote host is debian 9

ssh-keygen -t rsa -b 4096 -C "xstation@yahoo,con

Enter file in which to save the key (/home/yourusername/.ssh/id_rsa):

in my case home/xstation

Enter passphrase (empty for no passphrase): i entered a passphrase

keys are in
/home/yourusername/.ssh/id_rsa /home/yourusername/.ssh/id_rsa.pub


ssh-copy-id remote_username@server_ip_address -p5422

i log in again to make sure key was added
Number of key(s) added: 1


but still had to type root password

then in config ssh dispabled password

here is my .ssh file
drwx------  2 xstation xstatio 4096 &#4103;&#4157;&#4116;&#4154;    1 17:11 .
drwxr-xr-x 24 xstation xstation  4096 &#4103;&#4157;&#4116;&#4154;    1 20:53 ..
-rw-------  1 xstation xstation 3434 &#4103;&#4157;&#4116;&#4154;    1 16:47 id_rsa
-rw-r--r--  1 xstation xstation  741 &#4103;&#4157;&#4116;&#4154;    1 16:47 id_rsa.pub
-rw-r--r--  1 xstation xstation 1330 &#4103;&#4157;&#4116;&#4154;    1 17:11 known_hosts

---

### Post by TheFu on 2020-06-01
Please fix the typos above.  Attempts to connect to "yahoo,com? That makes no sense. The quote isn't closed either.  Details must be accurate and complete.  Please.

Please clearly label what is on the client and what is on the server.

Would be helpful if anything typed or viewed in a terminal were wrapped in "code" tags.

RSA is being deprecated. [https://www.openssh.com/releasenotes.html](https://www.openssh.com/releasenotes.html)

Forget root.  That shouldn't be used. Accessing a root account using a password is outside the Ubuntu methods.  We don't enabled root and would only elevate to use it with sudo.  Remote ssh logins via root aren't normally possible. su - isn't normally possible on Ubuntu systems.  Only use a non-root account.

---

