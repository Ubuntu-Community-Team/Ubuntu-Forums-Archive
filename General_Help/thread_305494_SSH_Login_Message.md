---
title: "SSH Login Message"
date: 2006-11-23
forum: General Help
---

### Post by phillips321 on 2006-11-23
Hi Guys

I have this message presented to me each time i log into to my remote ubuntu box via ssh.

```
Using username "phillips321".
phillips321@192.168.0.4's password:
Linux LinuxServer 2.6.15-26-386 #1 PREEMPT Fri Sep 8 19:55:17 UTC 2006 i686 GNU/Linux
[B]
The programs included with the Ubuntu system are free software; the exact distribution
terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by applicable law.[/B]
Last login: Thu Nov 23 17:33:54 2006 from 192.168.0.2
phillips321@LinuxServer:~$
```

I would like to change the bit in bold to my own custom message, does anyone know where this is stored?

cheers in advance

---

### Post by taurus on 2006-11-23
```
cat /etc/motd
```

---

### Post by earobinson on 2006-11-23
a simple man of sshd tell us they are stored in /etc/motd

Note: this will also change the login message from a ctrl + alt + f1 log in

---

### Post by phillips321 on 2006-11-23
mint, cheers guys.

Custom message is much better, thx :)

---

### Post by earobinson on 2006-11-23
no problem, now do us a favor, edit the original post, click advanced and mark the thread as resolved

---

