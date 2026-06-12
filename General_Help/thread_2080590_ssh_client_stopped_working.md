---
title: "ssh client stopped working"
date: 2012-11-04
forum: General Help
---

### Post by TheHimself on 2012-11-04
I have Xubuntu 10.10 on a Lenovo laptop and ssh command does not work anymore (it used to work). I've tested it over a variety of (wireless) networks and each time I get the "Connection timed out" error. I've also tried sshing different servers as well but no chance.

---

### Post by apollothethird on 2012-11-04
> **TheHimself said:**
> I have Xubuntu 10.10 on a Lenovo laptop and ssh command does not work anymore (it used to work). I've tested it over a variety of (wireless) networks and each time I get the "Connection timed out" error. I've also tried sshing different servers as well but no chance.

If you think it's the ssh client itself, try uninstalling and reinstalling the client:

```

$ sudo apt-get remove openssh-client
$ sudo apt-get install openssh-client

```

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by TheHimself on 2012-11-04
Didn't help.

---

### Post by apollothethird on 2012-11-04
> **TheHimself said:**
> Didn't help.

You may have to verify that the firewalls on both the client and server isn't blocking the connection, and the client's IP address isn't being blocked by /etc/hosts.deny .

Most host machines restrict which IP's have access.  If you had access at one time and suddenly don't, you might also want to check if your IP has changed.  Unless you have a static public IP it's possible you might have a different IP from what you was previously in effect when it was working.

-- L. James

-- 
L. D. James
[email]ljames@apollo3.com[/email]
[www.apollo3.com/~ljames](www.apollo3.com/~ljames)

---

### Post by TheHimself on 2012-11-04
It seems that the server has moved to a new address. Thanks.

---

### Post by Cheesemill on 2012-11-04
Does using the full verbose switch give you any more details?
```
ssh -vvv user@host
```

---

