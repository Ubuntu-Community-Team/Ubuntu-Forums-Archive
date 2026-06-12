---
title: "How to allow a program to create a SOCK_RAW socket ?"
date: 2008-06-09
forum: General Help
---

### Post by lordcoder on 2008-06-09
Hello,

how can I allow a program ( wine in my case ) to create a SOCK_RAW socket without being root ?

Thanks .

---

### Post by lordcoder on 2008-06-09
Is this the appropriate forum for this question ?

---

### Post by lordcoder on 2008-06-09
No one ? :confused:

---

### Post by lordcoder on 2008-06-09
Well, I've found fscaps ( [http://www.olafdietsche.de/linux/capability/](http://www.olafdietsche.de/linux/capability/) ) but there's no package for my kernel version ( 2.6.24-18 ) .

Is there a .deb package or something like that for the Kernel 2.6.24-18 ?

Thanks :-)

---

### Post by /etc/init.d/ on 2008-06-09
There is no legitimate reason to use raw sockets without being the root user.  They are restricted for a reason, we don't want you breaking the Internet now.

---

### Post by lordcoder on 2008-06-09
Well, many Windoze apps use raw sockets, and to make them work properly, I need to give wine the permission to create a raw socket, I've used "sudo setcap cap_net_raw=ep /usr/bin/wine" but it doesn't work ( even if there's no error messages ) because the kernel needs to have CONFIG_SECURITY_FILE_CAPABILITIES=y .

Using " grep '\(XATtr\|CAPA\)' /boot/config-`uname -r`" gives me :
```

CONFIG_SECURITY_CAPABILITIES=y
# CONFIG_SECURITY_FILE_CAPABILITIES is not set

```

---

### Post by lordcoder on 2008-06-09
No one has tried fscaps ?

---

### Post by lordcoder on 2008-06-09
Okay I need commoncap, but how to install/activate that module ?

---

### Post by lordcoder on 2008-06-09
Is there any kernel patch or something like that to get the commoncap module ? Or even better, something Ubuntu specific ?

Thanks .

---

### Post by captinkid on 2008-12-26
> **/etc/init.d/ said:**
> There is no legitimate reason to use raw sockets without being the root user.  They are restricted for a reason, we don't want you breaking the Internet now.

Well I would like to flash my router with a new firmware, the Asus utility to do this needs raw sockets to run. I would call this a legitimate reason. 

:)

I guess i need to reinstall XP on an old box just to flash the router, so close and yet so far. 

Tomato we love thee, just not with wine.

---

