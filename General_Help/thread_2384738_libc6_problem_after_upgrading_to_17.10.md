---
title: "libc6 problem after upgrading to 17.10"
date: 2018-02-11
forum: General Help
---

### Post by przemek7 on 2018-02-11
I tried to upgrade 17.04 to 17.10 and it ended with broken dependencies. Whatever I try to do it ends with these errors:

```
 libc-dev-bin : Depends: libc6 (> 2.26) but 2.24-9ubuntu2.2 is to be installed
 libc6-dbg : Depends: libc6 (= 2.26-0ubuntu2.1) but 2.24-9ubuntu2.2 is to be installed
 libc6-dev : Depends: libc6 (= 2.26-0ubuntu2.1) but 2.24-9ubuntu2.2 is to be installed
 libc6-i386 : Depends: libc6 (= 2.26-0ubuntu2.1) but 2.24-9ubuntu2.2 is to be installed
 libc6-x32 : Depends: libc6 (= 2.26-0ubuntu2.1) but 2.24-9ubuntu2.2 is to be installed
 locales : Depends: libc-bin (> 2.26) but 2.24-9ubuntu2.2 is to be installed

 Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

How to fix it? apt-get clean doesn't help, apt --fix-broken install also. I can't install anything, for example aptitude. I still have 17.04, during upgrade I got this error:

[IMG]https://preview.ibb.co/goWJFn/libc6.png[/IMG]

---

### Post by Impavidus on 2018-02-11
First of all, the quickest solution after a failed release upgrade is usually a fresh install. If you'll try a fresh install, there's no point in trying to fix this.

You have a bunch of packages depending on libc6 version 2.26, but only have libc6 version 2.24. But you can't upgrade libc6 because, according to that screenshot, your kernel is older than 3.2. And that error shouldn't be shown, as the package manager should have cought the problem already if the kernel was installed the normal way. Kernel 3.2 is ancient. Ubuntu 14.04, the oldest release still supported, came with kernel 3.13. So where did you get that ancient kernel?

If you want to solve this, show the output of```
dpkg --list | egrep 'linux-image|libc6'
```But I actually recommend to make this a fresh install.

---

### Post by przemek7 on 2018-02-11
This is VPS server, so I assume I can't update the kernel, right? Fresh install it's the last resort.

Output:
> ri  libc6:amd64                                     2.24-9ubuntu2.2                               amd64        GNU C Library: Shared libraries
iU  libc6-dbg:amd64                                 2.26-0ubuntu2.1                               amd64        GNU C Library: detached debugging symbols
iU  libc6-dev:amd64                                 2.26-0ubuntu2.1                               amd64        GNU C Library: Development Libraries and Header Files
iU  libc6-dev-i386                                  2.26-0ubuntu2.1                               amd64        GNU C Library: 32-bit development libraries for AMD64
iU  libc6-dev-x32                                   2.26-0ubuntu2.1                               amd64        GNU C Library: X32 ABI Development Libraries for AMD64
iU  libc6-i386                                      2.26-0ubuntu2.1                               amd64        GNU C Library: 32-bit shared libraries for AMD64
iU  libc6-x32                                       2.26-0ubuntu2.1                               amd64        GNU C Library: X32 ABI Shared libraries for AMD64

---

### Post by przemek7 on 2018-02-12
Does anyone know how to fix it? :(

---

