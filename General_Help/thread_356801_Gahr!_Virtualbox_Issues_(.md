---
title: "Gahr! Virtualbox Issues :("
date: 2007-02-08
forum: General Help
---

### Post by zombiepkx on 2007-02-08
> 
VirtualBox kernel driver not accessible, permission problem.
At '/home/vbox/vbox/src/VBox/VMM/VM.cpp' (303) in int VMR3Create(void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, char*), void*, int (*)(VM*, void*), void*, VM**).
VBox status code: -1909 VERR_VM_DRIVER_NOT_ACCESSIBLE
.


Result Code: 
0x80004005
Component: 
Console
Interface: 
IConsole {1dea5c4b-0753-4193-b909-22330f64ec45}

 

Mind telling me an easy way/quick way to fix this? I need XP on this machine for College yo. :P

---

### Post by zombiepkx on 2007-02-08
BUMP!!!

Sorry guys, this is urgent, need it before tomorrow :(

---

### Post by zombiepkx on 2007-02-08
> **zombiepkx said:**
> BUMP!!!

Sorry guys, this is urgent, need it before tomorrow :(

:(

---

### Post by lbyrd33 on 2007-02-10
I had the same problem when I updated to the new kernel. Just download the headers for the kernel as the update manager does not do that for you.

sudo apt-get install linux-headers-"uname -r"

Also, in order to let the installer setup the kernel in virtualbox have the newest version of GCC installed

---

### Post by dimeotane on 2007-02-10
I have the same problem after updating the kernel....
"VirtualBox kernel driver not installed."

this didnt' work for me however: 
```

sudo apt-get install linux-headers-"uname -r"
```



I get this error: 
E: Couldn't find package linux-headers-uname -r

:confused:

However, doing a reinstall from the Virtualbox v1.32 deb file did the trick for me =)

---

### Post by mrWoot on 2007-02-10
It's ```
sudo apt-get install linux-headers-`uname -r`
```

---

