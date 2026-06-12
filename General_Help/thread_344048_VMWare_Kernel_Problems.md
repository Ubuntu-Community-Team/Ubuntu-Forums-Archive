---
title: "VMWare Kernel Problems?"
date: 2007-01-22
forum: General Help
---

### Post by Josh1 on 2007-01-22
When I am installing the latest version of vmware, after I accept the terms of installing and whatever, I get this:

```
The directory of kernel headers (version 2.6.17.14-ubuntu1) does not match your
running kernel (version 2.6.17-10-386).  Even if the module were to compile 
successfully, it would not load into the running kernel.

What is the location of the directory of C header files that match your running
kernel? [/usr/src/linux/include] 
```

Typed /usr/src/linux/include but nothing happens... Anyone know a fix?

---

### Post by DerHesse on 2007-01-22
you need to: 

$sudo apt-get install linux-headers-2.6.17-10-386 g++

before proceeding.

After you finished that you can run vmware-config.pl again.

(you don't have to re-type the commands in brackets, they are default choice)

Good luck!

---

### Post by Josh1 on 2007-01-23
> **DerHesse said:**
> you need to: 

$sudo apt-get install linux-headers-2.6.17-10-386 g++

before proceeding.

After you finished that you can run vmware-config.pl again.

(you don't have to re-type the commands in brackets, they are default choice)

Good luck!

Yeah I know about the brackets, hitting enter, enter, enter is good.

```

josh@josh:~$ sudo apt-get install linux-headers-2.6.17-10-386 g++
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-10-386 is already the newest version.
g++ is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

---

### Post by lamego on 2007-01-23
On Edgy the current kernel headers path is:
/usr/src/linux-headers-2.6.17-10

---

