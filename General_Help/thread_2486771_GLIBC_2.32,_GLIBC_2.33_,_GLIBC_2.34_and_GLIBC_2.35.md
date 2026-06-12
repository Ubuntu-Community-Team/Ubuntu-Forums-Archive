---
title: "GLIBC_2.32, GLIBC_2.33 , GLIBC_2.34 and GLIBC_2.35 not found ...not is possible start"
date: 2023-05-10
forum: General Help
---

### Post by aug7744 on 2023-05-10
Hello.
Thanks for using your time reading my topic.

When trying start bforartists is showed the message below

Bforartists-3.5.0-linux
./bforartists: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.34' not found (required by ./bforartists)
./bforartists: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.32' not found (required by ./bforartists)
./bforartists: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.33' not found (required by ./bforartists)
./bforartists: /lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.30' not found (required by ./bforartists)
./bforartists: /lib/x86_64-linux-gnu/libm.so.6: version `GLIBC_2.35' not found (required by ./bforartists)
./bforartists: /lib/x86_64-linux-gnu/libc.so.6: version `GLIBC_2.32' not found (required by /opt/Bforartist/lib/libcycles_kernel_oneapi_aot.so)

The software not start.
OS is Lubuntu 20.04.6.
That is related with libc6 ?
How fix it ? Anyone known an PPA for download any dependencies ?

Have an nice day.

---

### Post by MAFoElffen on 2023-05-10
> **aug7744 said:**
> 
That is related with libc6 ?

Yes...

Please post the output of  this command, posted within CODE Tags...
```

apt policy libc6

```

---

### Post by aug7744 on 2023-05-10
Thanks for replying.


apt policy libc6
libc6:
  Instalado: 2.31-0ubuntu9.9
  Candidato: 2.31-0ubuntu9.9
  Tabela de versão:
 *** 2.31-0ubuntu9.9 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     2.31-0ubuntu9.7 500
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
     2.31-0ubuntu9 500
        500 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) focal/main amd64 Packages

---

### Post by MAFoElffen on 2023-05-10
And the version of b4artist?

If for the errors are cpomaing back as libc6 versions 2.32 through 2.35 and yours is 2.31... Then you are running Ubuntu release 20.04, and trying to run b4artists v3.5.1.

Unfortunately, if you upgraded to or downloaded the latest version of b4artists version 3.5.1, it will not run on Ubuntu 20.04. The current version was built for Ubuntu 22.04.

Their release notes:
> 
Note: the *.deb and *.tar are built with Ubuntu 22.04 LTS. This may cause problems with glibc on some distributions. This unfortunately also affects the Appimage version since using Ubuntu 22 will raise the minimum requirements for the Appimage. It will not run on older linux versions like Ubuntu 20 or the current Debian. Just equal or newer ones.

Note: The Appimage for 3.5.1 is still a work in progress. Latest version is 3.5.0

So you would either have to Upgrade your release of Ubuntu to 22.04 or run an older version of b4artists. (One that was built for 20.04).

---

### Post by aug7744 on 2023-05-10
Thanks for your good reply =)

The better solution is an OS upgrade.
Seeing in internet have an another solution too ...

mkdir $HOME/glibc/ && cd $HOME/glibc
wget [http://ftp.gnu.org/gnu/libc/glibc-2.32.tar.gz](http://ftp.gnu.org/gnu/libc/glibc-2.32.tar.gz)
tar -xvzf glibc-2.32.tar.gz
mkdir build 
mkdir glibc-2.32-install
cd build
~/glibc/glibc-2.32/configure --prefix=$HOME/glibc/glibc-2.32-install
make
make install

Need add the path of compiled glibc in environment ? If yes is an temporary fix and can run the software =)

Have an nice week.

---

### Post by MAFoElffen on 2023-05-10
You also!

I just got two new drives delivered today, to play with and continue some ZFS pool cache tests...

---

