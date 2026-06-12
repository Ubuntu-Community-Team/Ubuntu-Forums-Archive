---
title: "Linux Pseudo Random Number generator"
date: 2016-05-03
forum: General Help
---

### Post by ronan4 on 2016-05-03
Hey all,

I am running Ubuntu 14.04.4 LTS (trusty, linux kernel 3.19) and I would like to know where I can find the code describing the pseudo random number generator. In an older version of ubunto (kernel 2.6) the information was in /drivers/char/random.c, but this file doesn't seem to be on my system.

Cheers,
Ronan

---

### Post by HermanAB on 2016-05-03
Grep for csprng?

[https://fossies.org/linux/libgcrypt/random/random-csprng.c](https://fossies.org/linux/libgcrypt/random/random-csprng.c)

---

### Post by ronan4 on 2016-05-03
Thanks for the reply Herman. I did a grep and a find but I don't seem to have random-csprng.c either.

I tried:

find / -name *libgcrypt*

and got

/usr/share/doc/libgcrypt11
/usr/lib/vmware/lib/libgcrypt.so.11
/usr/lib/vmware/lib/libgcrypt.so.11/libgcrypt.so.11
/var/cache/apt/archives/libgcrypt11_1.5.3-2ubuntu4.3_amd64.deb
/var/cache/apt/archives/libgcrypt11_1.5.3-2ubuntu4.3_i386.deb
/var/lib/dpkg/info/libgcrypt11:i386.symbols
/var/lib/dpkg/info/libgcrypt11:amd64.postrm
/var/lib/dpkg/info/libgcrypt11:amd64.md5sums
/var/lib/dpkg/info/libgcrypt11:i386.list
/var/lib/dpkg/info/libgcrypt11:amd64.shlibs
/var/lib/dpkg/info/libgcrypt11:amd64.symbols
/var/lib/dpkg/info/libgcrypt11:i386.postrm
/var/lib/dpkg/info/libgcrypt11:i386.postinst
/var/lib/dpkg/info/libgcrypt11:amd64.postinst
/var/lib/dpkg/info/libgcrypt11:amd64.list
/var/lib/dpkg/info/libgcrypt11:i386.md5sums
/var/lib/dpkg/info/libgcrypt11:i386.shlibs
/lib/x86_64-linux-gnu/libgcrypt.so.11
/lib/x86_64-linux-gnu/libgcrypt.so.11.8.2
/lib/i386-linux-gnu/libgcrypt.so.11
/lib/i386-linux-gnu/libgcrypt.so.11.8.2

Is it possible that the source code has been removed from my system?

Thanks,
Ronan

---

### Post by ubu_dynamite on 2016-05-03
If you want source code you should get it first with "apt-get source packagename"

---

