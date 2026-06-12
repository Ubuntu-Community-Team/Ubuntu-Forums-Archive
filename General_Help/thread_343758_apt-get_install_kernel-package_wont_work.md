---
title: "apt-get install kernel-package wont work"
date: 2007-01-21
forum: General Help
---

### Post by s2svetko on 2007-01-21
im tring to upgrade my kernel so i need to run 
apt-get update
followed by
apt-get install kernel-package

but im getting an error that says the package doesnt exist.
what am i doing wrong
thanks

---

### Post by pay on 2007-01-21
```
sudo apt-get dist-upgrade
```would upgrade you to the latest kernel in the repositories. Also theres no point in posting the same question twice on the forums. Just be patient.

---

### Post by s2svetko on 2007-01-21
still not working heres a copy of my terminal:
"steve@ubuntu:/usr/src/linux-2.6.19.2$ su
Password:
root@ubuntu:/usr/src/linux-2.6.19.2# apt-get update
Reading package lists... Done
root@ubuntu:/usr/src/linux-2.6.19.2# apt-get install kernel-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kernel-package
root@ubuntu:/usr/src/linux-2.6.19.2# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/usr/src/linux-2.6.19.2# apt-get install kernel-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kernel-package
"

---

### Post by HGXiphias on 2007-01-21
I'm also trying to upgrade to the latest Kernel, but I get this message returned and I'm sure that I definitely don't have the most recent version of the Kernel.

```
root@test1:~# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@test1:~#

```

Any ideas?

---

### Post by pay on 2007-01-22
> **s2svetko said:**
> still not working heres a copy of my terminal:
"steve@ubuntu:/usr/src/linux-2.6.19.2$ su
Password:
root@ubuntu:/usr/src/linux-2.6.19.2# apt-get update
Reading package lists... Done
root@ubuntu:/usr/src/linux-2.6.19.2# apt-get install kernel-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kernel-package
root@ubuntu:/usr/src/linux-2.6.19.2# apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@ubuntu:/usr/src/linux-2.6.19.2# apt-get install kernel-package
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kernel-package
"
you're using the 2.6.19.2 kernel. That's the latest stable kernel, but it isn't available in edgy so you must of compiled it yourself. I forget what the kernel packages is called but it is something like ```
sudo aptitude install linux-images-<kernel>
```Try pressing tab twice to see what kernels are available.

@HGXiphias
You might already have the latest kernel if it's not updating. Run```
 uname -r
```to see what kernel you're using.

---

