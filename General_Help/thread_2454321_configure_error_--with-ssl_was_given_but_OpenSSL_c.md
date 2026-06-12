---
title: "configure: error: --with-ssl was given but OpenSSL could not be detecte"
date: 2020-11-27
forum: General Help
---

### Post by fairbird on 2020-11-27
I have try to compile and build libcurl inside my toolcahin folder by using cross compile but always I got same error... on Ubuntu 20.04.1

1-First I build openssl by this steps
```
export TOOLCHAIN=/home/MY/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi
export CC=$TOOLCHAIN/bin/arm-linux-gnueabi-gcc-7.5.0
export RANLIB=$TOOLCHAIN/bin/arm-linux-gnueabi-ranlib
export PATH="$TOOLCHAIN/bin:$PATH"
./Configure linux-generic32 --prefix=$TOOLCHAIN/arm-linux-gnueabi/libc/usr no-async
make depends
make
make install
.
.
.
cp libcrypto.pc /home/MY/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi/arm-linux-gnueabi/sysroot/usr/lib/pkgconfig
chmod 644 /home/MY/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi/arm-linux-gnueabi/sysroot/usr/lib/pkgconfig/libcrypto.pc
cp libssl.pc /home/MY/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi/arm-linux-gnueabi/sysroot/usr/lib/pkgconfig
chmod 644 /home/MY/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi/arm-linux-gnueabi/sysroot/usr/lib/pkgconfig/libssl.pc
cp openssl.pc /home/MY/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi/arm-linux-gnueabi/sysroot/usr/lib/pkgconfig
chmod 644 /home/MY/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi/arm-linux-gnueabi/sysroot/usr/lib/pkgconfig/openssl.pc
.
.
.
~/$ ls -n from gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi
total 36
drwxr-xr-x 6 raed raed  4096 &#1606;&#1608;&#1601; 26 12:31 arm-linux-gnueabi
drwxr-xr-x 2 raed raed  4096 &#1583;&#1610;&#1587;  4  2019 bin
-rw-r--r-- 1 raed raed 11287 &#1583;&#1610;&#1587;  4  2019 gcc-linaro-7.5.0-2019.12-linux-manifest.txt
drwxr-xr-x 3 raed raed  4096 &#1583;&#1610;&#1587;  4  2019 include
drwxr-xr-x 3 raed raed  4096 &#1583;&#1610;&#1587;  4  2019 lib
drwxr-xr-x 3 raed raed  4096 &#1583;&#1610;&#1587;  4  2019 libexec
drwxr-xr-x 8 raed raed  4096 &#1583;&#1610;&#1587;  4  2019 share

~/$ ls -n from arm-linux-gnueabi/libc/usr
total 28
drwxr-xr-x  2 raed raed 4096 &#1606;&#1608;&#1601; 26 12:18 bin
drwxr-xr-x 34 raed raed 4096 &#1606;&#1608;&#1601; 26 12:18 include
drwxr-xr-x  6 raed raed 4096 &#1606;&#1608;&#1601; 26 12:18 lib
drwxr-xr-x  3 raed raed 4096 &#1583;&#1610;&#1587;  4  2019 libexec
drwxr-xr-x  2 raed raed 4096 &#1583;&#1610;&#1587;  4  2019 sbin
drwxr-xr-x  5 raed raed 4096 &#1583;&#1610;&#1587;  4  2019 share drwxrwxr-x  6 raed raed 4096 &#1606;&#1608;&#1601; 26 12:18 ssl
```

2-Then I have try to build libcurl with--ssl but I have got error
```
cd curl-7.72.0
export TOOLCHAIN=/home/MY/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi
export CC=$TOOLCHAIN/bin/arm-linux-gnueabi-gcc-7.5.0
export RANLIB=$TOOLCHAIN/bin/arm-linux-gnueabi-ranlib
export PATH="$TOOLCHAIN/bin:$PATH"
./configure --with-ssl=/home/MY/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi/arm-linux-gnueabi/libc/usr --host=arm-linux-gnueabi
.
.
.
configure: PKG_CONFIG_LIBDIR will be set to "/home/MY/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi/arm-linux-gnueabi/libc/usr/lib/pkgconfig"
checking for arm-linux-gnueabi-pkg-config... /usr/bin/pkg-config
checking for openssl options with pkg-config... found
configure: pkg-config: SSL_LIBS: "-lssl -lcrypto"
configure: pkg-config: SSL_LDFLAGS: "-L/home/MY/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi/arm-linux-gnueabi/libc/usr/lib"
configure: pkg-config: SSL_CPPFLAGS: "-I/home/MY/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi/arm-linux-gnueabi/libc/usr/include"
checking for HMAC_Update in -lcrypto... no
checking for HMAC_Init_ex in -lcrypto... no
checking OpenSSL linking with -ldl... no
checking OpenSSL linking with -ldl and -lpthread... no
configure: OPT_SSL: /home/MY/gcc-linaro-7.5.0-2019.12-x86_64_arm-linux-gnueabi/arm-linux-gnueabi/libc/usr
configure: OPENSSL_ENABLED:  configure: error: --with-ssl was given but OpenSSL could not be detected
```

---

### Post by SeijiSensei on 2020-11-27
Try running "sudo apt build-dep curl". It will download any missing source packages for dependencies.

---

### Post by fairbird on 2020-11-27
Thank you for answer ...
Already I do that method .. And same error I have got it ...

Than problem is some things happens to path of openssl or liburl ...
I have already install last version of libcurl on my system ..

I need to build libcurl by cross compile inside my toolchain not inside system ..

---

### Post by DuckHook on 2020-11-27
@fairbird

Please do not post using nonstandard styles and fonts. It is hard on the eyes and garbles anything within code boxes.

*Thread moved to **General Help** as the more appropriate forum.*

---

### Post by fairbird on 2020-11-27
Thank you ..
I solve the issue ... 
The problem is with zlib need to build it inside toolchain and add this in configure seetings
```
--with-zlib=$prefix/lib
```

---

