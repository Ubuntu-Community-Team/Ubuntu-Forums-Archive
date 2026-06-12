---
title: "Really simple question, why is there a sshd user on my server?"
date: 2014-05-24
forum: General Help
---

### Post by vRanger on 2014-05-24
Yes, I did install OpenSSH.  Yes, I did do search on Google.  But it doesn't answer why there is a user called "sshd".
> :~$ cat /etc/passwd | grep sshd
sshd: x:112:65534::/var/run/sshd:/usr/sbin/nologin


---

### Post by 3rdalbum on 2014-05-24
In order to listen on the SSH port it needs privileges that an ordinary user account doesn't have.

However, running as root would be insanely dangerous. Any successful attacker would have root.

Therefore, sshd runs as its own super-restrictive user account to limit what an attacker can do.

Most other servers do the same thing.

---

### Post by sudodus on 2014-05-24
sshd is the computer service or daemon that implements the Secure Shell protocol. It belongs to OpenSSH. And a user with the same name also belongs to the infrastucture of OpenSSH. There are many user IDs behind the curtain. See the file **/etc/group**

```
less /etc/group
```

Quit from the viewer less with q

---

### Post by vRanger on 2014-05-24
You both rock!  Thanks.

---

