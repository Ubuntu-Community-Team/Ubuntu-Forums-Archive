---
title: "Can I use wildcards and *.local in /etc/ssh/sshd_config?"
date: 2017-05-25
forum: General Help
---

### Post by desconocido on 2017-05-25
I am building a local network of machines which, I hope, will all be using Zeroconf/Avahi/Bonjour.

I want only users on local machines to be able to ssh to these machines. (All users except root). I want to exclude users from the wider Internet from being able to ssh to my machines. Ideally I would make the sshd_config files identical on all the machines.

Can I just put the lines

```
PermitRootLogin no
AllowUsers  *@*.local
```

in /etc/ssh/sshd_config in each of these machines? I'm not sure of wildcard possibilities.

Alternatively, but not so ideal, can I put

```
PermitRootLogin no
ListenAddress thiscomputername.local
```

I'm not clear on the semantics of the structure of this file and the [Man page]("https://www.freebsd.org/cgi/man.cgi?sshd_config%285%29") doesn't seem to help. Do earlier directives override later ones or viceversa? What happens if directives contradict each other? Does it matter in which order deny.. and allow.. are placed?

(To start off with, all the machines will have Ubuntu 16.04 with default /etc/ssh/sshd_config)

---

### Post by apmcd47 on 2017-05-25
The ListenAddress directive is used when a computer has multiple IP addresses, forcing the SSH Daemon to listen only on one of those addresses. The AllowUsers directive is the better one to use. Check the [ssh_config]("http://www.unix.com/man-page/linux/5/ssh_config/") man page section on PATTERNS to see what is possible. In your case I would probably have something like
```
AllowUsers  *@192.168.1.*
``` where the 192... is the IP address range of your local network.

Andrew

---

### Post by Habitual on 2017-05-25
[https://help.ubuntu.com/community/StricterDefaults](https://help.ubuntu.com/community/StricterDefaults) may be of help.

---

### Post by desconocido on 2017-05-25
> **apmcd47 said:**
> Check the [ssh_config]("http://www.unix.com/man-page/linux/5/ssh_config/") man page section on PATTERNS to see what is possible.  It doesn't really say much more than your example, although it implies you can use wildcards anywhere.


> 
In your case I would probably have something like
```
AllowUsers  *@192.168.1.*
```

Andrew

In that case, 
```
AllowUsers  *@*.local
``` should be possible. I think I will try this (although I won't be able to test it - I have no idea how to hack access to a machine behind a router from the Internet).

---

### Post by desconocido on 2017-05-25
> **desconocido said:**
> I think I will try this
No, that doesn't work.
```
$ ssh faustino.local
bob@faustino.local's password: 
Permission denied, please try again.
```
That fails from the same machine, from another machine and if I try ssh localhost. All those worked before I put those directives in.

---

### Post by desconocido on 2017-05-26
So, *.local didn't work

This one did
```

AllowUsers  *@192.168.0.???

```

---

