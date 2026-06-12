---
title: "Bug in Dynamic Linker ld.so"
date: 2008-02-29
forum: General Help
---

### Post by adolfobruno on 2008-02-29
Hello, 

 When I tryed install:  glibc-2.1.3-16.i386.rpm  this happened:

[B] Preparing...                ########################################### [100%]
   1:glibc                  warning: /etc/localtime created as /etc/localtime.rp mnew
warning: /etc/nsswitch.conf created as /etc/nsswitch.conf.rpmnew
warning: /etc/rpc saved as /etc/rpc.rpmorig
########################################### [100%]
error: unpacking of archive failed on file /usr/share/locale/pt_BR/LC_TIME: cpio : rename failed - Is a directory[/B]

 Then when I execute some command this message appears:

[B] BUG IN DYNAMIC LINKER ld.so: dynamic-link.h: 57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed!
[/B]
 Somebody knows what I must make this message not to appear more and my system comes back to function normally?

Thank you.

---

### Post by PeterJS on 2008-02-29
Why did you install a non-standard glib from a Red Hat package? The glib you installed is incompatable with your system, it's a wonder it runs at all.

Did you install it with alien? Hopefully you should be able to open synaptic and search for an ubuntu glib package and install a proper package, and hope the damage isn't too great.

---

### Post by adolfobruno on 2008-02-29
I saw in a tutorial one that I would have to install this package, then I tried to install. It would like to know if it has as my system to come back to the normal one, therefore I only obtain to execute "cd" and more nothing.

Thank you!

---

### Post by adolfobruno on 2008-02-29
I am working in the machine remotely and for that I perceived if I to detach the session ssh I will not obtain more to connect myself.

---

### Post by taurus on 2008-02-29
Is the tutorial for Ubuntu or RedHat/Fedora?  Ubuntu uses .deb while RedHat/Fedora uses .rpm extension.

---

### Post by adolfobruno on 2008-02-29
I am working in Ubuntu.

---

### Post by taurus on 2008-02-29
> **adolfobruno said:**
> I am working in Ubuntu.

I know you are running Ubuntu but the tutorial that told you to install glibc-2.1.3-16.i386.rpm on your machine is for RedHat/Fedora or Ubuntu?

---

### Post by PeterJS on 2008-02-29
The ubuntu glibc package is named libc6, try:
```

sudo apt-get install --reinstall libc6

```
What were you trying to install, after your system gets back to stable we'll see what we can do about finding instructions that aren't Red Hat specific.

---

### Post by adolfobruno on 2008-02-29
> **taurus said:**
> I know you are running Ubuntu but the tutorial that told you to install glibc-2.1.3-16.i386.rpm on your machine is for RedHat/Fedora or Ubuntu?

Ubuntu

---

### Post by adolfobruno on 2008-02-29
> **PeterJS said:**
> The ubuntu glibc package is named libc6, try:
```

sudo apt-get install --reinstall libc6

```
What were you trying to install, after your system gets back to stable we'll see what we can do about finding instructions that aren't Red Hat specific.

I tryed this command but appears this:

**BUG IN DYNAMIC LINKER ld.so: dynamic-link.h: 57: elf_get_dynamic_info: Assertion `! "bad dynamic tag"' failed!**

---

### Post by PeterJS on 2008-02-29
Hopefully Tarus will have a better solution but this is looking like the sort of thing you don't recover from. You can't install the correct linker because you can't run apt-get to install it because apt-get uses linked libraries that can't be linked because you've got a bad linker.

---

