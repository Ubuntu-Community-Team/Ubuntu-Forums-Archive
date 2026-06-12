---
title: "sudo broke by hostname change on remote server"
date: 2006-11-22
forum: General Help
---

### Post by aagmon on 2006-11-22
Hi , 

using ubuntu server 6.06
on IBM 336
------------------------

we have changed the hostname by using the linux hostname command. 
which didn't changed the /etc/hostname or added the entry 
in the /etc/hosts.

anyway this caused sudo to break like:
"sudo: unable to lookup test1 via gethostbyname()"
which means that we can't change it again using sudo .. :(

now i know that its possible to get root shell during boot , 
but the problem is that this server is in another country!!!
we only SSH to it

so if there is any but any way to resolve this issue ..
i'll be far more then greatfull ... 

thank you very much

---

### Post by etienne.navarro on 2006-11-25
Have you setup a root account? If you have you can just do
```
su -
``` and get into the root account and fix things.

Possibly depending on the privileges you've given yourself, you could chroot into some small distro (like DSL) and then mount the hard drive where /etc exists and change it.

---

