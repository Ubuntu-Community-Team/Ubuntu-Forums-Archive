---
title: "Can't edit resolv.conf"
date: 2006-10-12
forum: General Help
---

### Post by adwait on 2006-10-12
Hello!

I can't edit the resolv.conf file for some reason, it just opens as read only. Tried using sudo, tried using the root account..tried changing permissions of the file as root (it won't even let me do that...it says operation not permitted). The current permissions of the file allow the owner(root) to change the file..but I can't do it...no idea why, any ideas?

---

### Post by wieman01 on 2006-10-12
Mmm... Could you post the command you're using? I normally do this:
> sudo gedit /etc/resolv.conf
Please also post the permission settings.

---

### Post by taurus on 2006-10-12
Actually, it's better to use gksudo when you use gedit...

```
gksudo gedit /etc/resolv.conf
```

---

### Post by adwait on 2006-10-12
I am using KDE and the command is
```
sudo vi /etc/resolv.conf 
```

The permisisons are:
> -rw-r--r--   1 root   root        50 2006-06-23 12:18 resolv.conf[quote]

The error is:
[quote]chmod: changing permissions of `resolv.conf': Operation not permitted


---

### Post by wieman01 on 2006-10-12
Also try:
> sudo chmod +w+w /etc/resolv.conf
That should do.

---

### Post by wieman01 on 2006-10-12
> **taurus said:**
> Actually, it's better to use gksudo when you use gedit...

```
gksudo gedit /etc/resolv.conf
```
Is it? In what sense? Does that make a difference in terms of security or performance?

---

### Post by taurus on 2006-10-12
Are you only having problem with editing /etc/resolv.conf or does it happen for all system files?  What happens when you run this command?

```
sudo vi /etc/apt/sources.list
```
See if you can edit (by placing a # on an empty line) and save it...

---

### Post by darrenm on 2006-10-12
Sure you havent got resolvconf installed and its symlinked? What does ls -ahlt /etc/resolv.conf say?

---

### Post by thingy on 2006-10-12
One other thing you can check is whether you have [resolvconf]("http://packages.ubuntu.com/dapper/net/resolvconf") installed.
 
To check do a "dpkg -l | grep resolvconf"
 
If it is installed then this means that the nameserver information in /etc/resolv.conf is configured via the ifupdown scripts, DHCP clients, the PPP daemon, local nameservers etc.
 
So you need to make the changes to the nameservers in one of the above.

---

### Post by lkagan on 2006-10-12
Sounds like the immutable bit maybe set.

If your output looks like the following, then it's set.

```

larry@xandir:~$ lsattr /etc/resolv.conf
----i------------ /etc/resolv.conf

```

If this is the case, remove the immutable bit with:

```

larry@xandir:~$ sudo chattr -i /etc/resolv.conf

```

Hope this helps.

Larry Kagan

---

### Post by wieman01 on 2006-10-12
Deleted.

---

### Post by adwait on 2006-10-12
hey thanks...the immutable bit thing set it right!

---

