---
title: "Cannot get canonical-livepatch to work"
date: 2016-10-22
forum: General Help
---

### Post by vasya1122 on 2016-10-22
Hello Gurus!

I am trying to install canonical-livepatch on my Ubuntu 16.04 server. I managed to install it via snap but after the command sudo canonical-livepatch enable [MY_TOKEN_HERE] I get the following error: sudo: canonical-livepatch: command not found.

Can you please point out what is wrong here?

Thanks

---

### Post by howefield on 2016-10-22
Would be good to see the actual terminal output (with the token obfuscated) ?

---

### Post by vasya1122 on 2016-10-22
[IMG]http://savepic.ru/11875157.jpg[/IMG]
The weird writing in cyrillic stands for 'command not found'.

---

### Post by vasya1122 on 2016-10-28
Anyone?

---

### Post by bearlake on 2016-10-28
Hi,

Have you seen this [thread]("https://ubuntuforums.org/showthread.php?t=2341379") yet?

---

### Post by vasya1122 on 2016-10-29
> **bearlake said:**
> Hi,

Have you seen this [thread]("https://ubuntuforums.org/showthread.php?t=2341379") yet?

Thank you very very much! After the following command it worked - sudo /snap/bin/canonical-livepatch enable <token>  :D

---

### Post by sandeep.sudheer on 2017-01-31
Include '***:/snap/bin/***' at the end to variable ***PATH=***"..." under '***/etc/environment***' file.

---

