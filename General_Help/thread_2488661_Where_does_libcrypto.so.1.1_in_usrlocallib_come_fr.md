---
title: "Where does libcrypto.so.1.1 in /usr/local/lib come from?"
date: 2023-07-11
forum: General Help
---

### Post by tnafele on 2023-07-11
Hi there,

cmake on my 22.04 Laptop (actually it's PopOS but this isn't PopOS specific) started to complain about missing libcrypto.so.1.1:

```
cmake: error while loading shared libraries: libcrypto.so.1.1: cannot open shared object file: No such file or directory

```
I removed  libcrypto.so.1.1 from /usr/local/lib because I thought I put it there myself when I was compiling some libssh stuff a few years ago.

Now I'm a bit surprised that some binaries from official Ubuntu packages depend on it. But I can't find the package which installed this library:

dpkg -S /usr/local/lib/libcrypto.so.1.1
apt-file search libcrypto.so.1.1

Nothing.

Also flatpak complains... so I guess there are a few more that depend on libcrypto.so.1.1.

I really wonder why this in /usr/local and in no package when it's so important. And where does it come from?

---

### Post by Holger_Gehrke on 2023-07-11
/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1 was part of the package libssl1.1 in Ubuntu 20.04. In Ubuntu 22.04 there's libssl3 which uses libcrypto.so.3. libcrypto.so.1.1 is still part of the core18, core20 and gnome snaps.

I'd try updating / regenerating the cache for the library loader (/etc/ld.so.cache). Read 'man ldconfig' for the details.

Holger

---

### Post by MAFoElffen on 2023-07-11
There are several packages that use that, but each installs to different places. To give you an idea of the where's... There is not just one occurrence.
```

mafoelffen@Mikes-ThinkPad-T520:~$ find / -name libcrypto.so.1.1 -exec sh -c 'file {} ' \; -print 2> /dev/null
/opt/nvidia/nsight-systems/2022.4.2/host-linux-x64/libcrypto.so.1.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, with debug_info, not stripped
/opt/nvidia/nsight-systems/2022.4.2/host-linux-x64/libcrypto.so.1.1
/opt/nvidia/nsight-compute/2022.4.0/host/linux-desktop-glibc_2_11_3-x64/libcrypto.so.1.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, stripped
/opt/nvidia/nsight-compute/2022.4.0/host/linux-desktop-glibc_2_11_3-x64/libcrypto.so.1.1
/snap/core20/1950/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=894b27aca5ad1a9f3dd02a966aeccd15a12874a9, stripped
/snap/core20/1950/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1
/snap/core20/1974/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=894b27aca5ad1a9f3dd02a966aeccd15a12874a9, stripped
/snap/core20/1974/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1
/snap/core18/2785/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=7da0bcf38b121ab12af7bb4a69cc560b73763269, stripped
/snap/core18/2785/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1
/snap/core18/2751/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=7da0bcf38b121ab12af7bb4a69cc560b73763269, stripped
/snap/core18/2751/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1

mafoelffen@Mikes-B460M:~$ find / -name libcrypto.so.1.1 -exec sh -c 'file {} ' \; -print 2> /dev/null
/snap/core20/1974/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=894b27aca5ad1a9f3dd02a966aeccd15a12874a9, stripped
/snap/core20/1974/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1
/snap/core20/1950/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=894b27aca5ad1a9f3dd02a966aeccd15a12874a9, stripped
/snap/core20/1950/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1

mafoelffen@opti-ubuntu:~$ find / -name libcrypto.so.1.1 -exec sh -c 'file {} ' \; -print 2> /dev/null
/snap/core20/1974/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=894b27aca5ad1a9f3dd02a966aeccd15a12874a9, stripped
/snap/core20/1974/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1
/snap/core20/1950/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=894b27aca5ad1a9f3dd02a966aeccd15a12874a9, stripped
/snap/core20/1950/usr/lib/x86_64-linux-gnu/libcrypto.so.1.1
/usr/lib/plexmediaserver/lib/libcrypto.so.1.1: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, BuildID[sha1]=f66655dedf04db2ccfa156f48c937d0a15a221e0, not stripped
/usr/lib/plexmediaserver/lib/libcrypto.so.1.1

```

---

### Post by tnafele on 2023-07-11
> **Holger_Gehrke said:**
> /usr/lib/x86_64-linux-gnu/libcrypto.so.1.1 was part of the package libssl1.1 in Ubuntu 20.04. In Ubuntu 22.04 there's libssl3 which uses libcrypto.so.3. libcrypto.so.1.1 is still part of the core18, core20 and gnome snaps.

I'd try updating / regenerating the cache for the library loader (/etc/ld.so.cache). Read 'man ldconfig' for the details.

Holger

Hi Holger thanks for the hints!

I know that on 22.04 libcrypto.so.1.1 is outdated. That's why I wonder why there are official packages (e.g. [cmake]("https://launchpad.net/ubuntu/jammy/amd64/cmake/3.22.1-1ubuntu1.22.04.1")) that still expect it to exist.

Maybe this library belongs to the initial filesystem and that's why it doesn't belong to any package?

Sorry I'm not really familiar with this snap stuff. I've been using Linux for over 20 years but at some point I lost track a bit. And to be honest I don't like this mix-up of dpkg, flatpack and snap.
So it could be that there are deb packages which depend on some snaps?

---

### Post by tnafele on 2023-07-11
> **MAFoElffen said:**
> There are several packages that use that, but each installs to different places. To give you an idea of the where's... There is not just one occurrence.


Yes that's right, but cmake will not find them when these paths aren't in any /etc/ld.so.conf.d/xxx.conf file.

```
root@poptart:~# apt-cache depends cmake
cmake
  Depends: libarchive13
  Depends: libc6
  Depends: libcurl4
  Depends: libexpat1
  Depends: libgcc-s1
  Depends: libjsoncpp25
  Depends: librhash0
  Depends: libstdc++6
  Depends: libuv1
  Depends: zlib1g
  Depends: cmake-data
  Depends: procps
    procps:i386
  Recommends: gcc
  Recommends: make
    make-guile
  Suggests: cmake-doc
  Suggests: ninja-build
    ninja-build:i386
  Suggests: cmake-format
```
Installing cmake doesn't install any packet that contains libcrypto.so.1.1 - Why did this ever work?

---

### Post by Holger_Gehrke on 2023-07-11
Have you taken a look at 'which cmake' ? Might be that you compiled cmake at some point yourself and installed it to /usr/local/bin which has a higher priority than /usr/bin. That happened to me for a few things; when I did a fresh install and just backed up and restored /usr/local a few program suddenly couldn't find libraries which used to be part of Ubuntu ...

Holger

---

### Post by tnafele on 2023-07-12
> **Holger_Gehrke said:**
> Have you taken a look at 'which cmake' ? Might be that you compiled cmake at some point yourself and installed it to /usr/local/bin which has a higher priority than /usr/bin. That happened to me for a few things; when I did a fresh install and just backed up and restored /usr/local a few program suddenly couldn't find libraries which used to be part of Ubuntu ...

Hi Holger,

Thanks again for the hint. Yes I also checked this and the binary directly extracted from the .deb package. Both need the  libcrypto.so.1.1

It's a mystery. It really looks like this library has to be in /usr/local/lib, but it's not from any deb package.

---

### Post by Holger_Gehrke on 2023-07-12
'cmake' from the repositories is version 3.22.1-1ubuntu1.22.04.1 and links 'librypto.so.3' according to 'ldd' and there's no mention of 'libcrypto.so.1.1' anywhere. Wherever your cmake comes from, it's not the one that you get from the standard repositories now. If the one you have installed was installed through apt, I'd take a hard look at 'apt policy cmake' and check the sources apt uses.

Holger

---

### Post by tnafele on 2023-07-12
> **Holger_Gehrke said:**
> 'cmake' from the repositories is version 3.22.1-1ubuntu1.22.04.1 and links 'librypto.so.3' according to 'ldd' and there's no mention of 'libcrypto.so.1.1' anywhere. Wherever your cmake comes from, it's not the one that you get from the standard repositories now. If the one you have installed was installed through apt, I'd take a hard look at 'apt policy cmake' and check the sources apt uses.

This is really strange. This is exactly the deb package from which I extracted the binary I checked against the one from /usr/bin. Both need libcrypto.so.1.1:
```
root@poptart:~# ldd ./cmake
	linux-vdso.so.1 (0x00007fffda3f5000)
	libz.so.1 => /lib/x86_64-linux-gnu/libz.so.1 (0x00007f52255cc000)
	libarchive.so.13 => /lib/x86_64-linux-gnu/libarchive.so.13 (0x00007f5225502000)
	libcurl.so.4 => /lib/x86_64-linux-gnu/libcurl.so.4 (0x00007f5224d59000)
[...]
	libgmp.so.10 => /lib/x86_64-linux-gnu/libgmp.so.10 (0x00007f5223747000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f5224829000)
	libcrypto.so.1.1 => not found
	libkrb5.so.3 => /lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007f522367c000)
	libk5crypto.so.3 => /lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007f522364d000)
	libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007f5224257000)
[...]
```

libcrypto3 is installed on my system but it doesn't satisfy cmake from the package cmake_3.22.1-1ubuntu1.22.04.1_amd64.deb.

The only way to satisfy it is by adding libcrypto.so.1.1

---

### Post by Holger_Gehrke on 2023-07-12
```

$ cmake --version
cmake version 3.22.1

CMake suite maintained and supported by Kitware (kitware.com/cmake).

$ ldd /usr/bin/cmake|grep cryp
    libcrypto.so.3 => /lib/x86_64-linux-gnu/libcrypto.so.3 (0x00007ffbf32f3000)
    libk5crypto.so.3 => /lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007ffbf2ac7000)

```
Just for comparison ...

Holger

---

### Post by tnafele on 2023-07-12
```
root@poptart:~# dpkg-deb -xv cmake_3.22.1-1ubuntu1.22.04.1_amd64.deb /root/out
root@poptart:~# ldd /root/out/usr/bin/cmake
[...]
	libgmp.so.10 => /lib/x86_64-linux-gnu/libgmp.so.10 (0x00007fc5e7136000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007fc5e7131000)
	**libcrypto.so.1.1** => /usr/local/lib/libcrypto.so.1.1 (0x00007fc5e6e00000)
	libkrb5.so.3 => /lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007fc5e6d35000)
[...]

root@poptart:~# /root/out/usr/bin/cmake --version
CMake Error: Could not find CMAKE_ROOT !!!
CMake has most likely not been installed correctly.
Modules directory not found in
/root/out/usr/share/cmake-3.22
cmake version 3.22.1

root@poptart:~# md5sum out/usr/bin/cmake 
b38d62d01bc40c1ab0c07ef544879c9f  out/usr/bin/cmake

```


```
root@poptart:~# mv /usr/local/lib/libcrypto.so.1.1 ~
root@poptart:~# ldconfig
root@poptart:~# ldconfig -p | grep crypto
	libmbedcrypto.so.7 (libc6,x86-64) => /lib/x86_64-linux-gnu/libmbedcrypto.so.7
	libk5crypto.so.3 (libc6,x86-64) => /lib/x86_64-linux-gnu/libk5crypto.so.3
	libk5crypto.so.3 (libc6) => /lib/i386-linux-gnu/libk5crypto.so.3
	libk5crypto.so (libc6,x86-64) => /lib/x86_64-linux-gnu/libk5crypto.so
	libcrypto.so.3 (libc6,x86-64) => /lib/x86_64-linux-gnu/libcrypto.so.3
	libcrypto.so.3 (libc6) => /lib/i386-linux-gnu/libcrypto.so.3
	libcrypto.so (libc6,x86-64) => /lib/x86_64-linux-gnu/libcrypto.so
	libbd_crypto.so.2 (libc6,x86-64) => /lib/x86_64-linux-gnu/libbd_crypto.so.2
root@poptart:~# ldd /root/out/usr/bin/cmake 
[...]
	libhogweed.so.6 => /lib/x86_64-linux-gnu/libhogweed.so.6 (0x00007f3683575000)
	libgmp.so.10 => /lib/x86_64-linux-gnu/libgmp.so.10 (0x00007f36834f3000)
	librt.so.1 => /lib/x86_64-linux-gnu/librt.so.1 (0x00007f368527a000)
	libcrypto.so.1.1 => **not found**
	libkrb5.so.3 => /lib/x86_64-linux-gnu/libkrb5.so.3 (0x00007f3683428000)
	libk5crypto.so.3 => /lib/x86_64-linux-gnu/libk5crypto.so.3 (0x00007f3684044000)
	libcom_err.so.2 => /lib/x86_64-linux-gnu/libcom_err.so.2 (0x00007f3683422000
[...]
```

:confused:

The deb comes from here: [https://launchpad.net/ubuntu/jammy/amd64/cmake/3.22.1-1ubuntu1.22.04.1](https://launchpad.net/ubuntu/jammy/amd64/cmake/3.22.1-1ubuntu1.22.04.1)

---

### Post by tnafele on 2023-07-12
Oh my I found the problem:

cmake also links to libssh.

There was also a libssh.so in my /usr/local/lib. And this one needed crypto1.1. So every binary on my system that uses libssh also needed crypto1.1!

**SOLVED!**

---

