---
title: "CRITICAL - error while loading shared libraries: libpcre.so.3"
date: 2016-04-04
forum: General Help
---

### Post by mysql69 on 2016-04-04
Hi,

I have been upgrading the libpcre libraries and I do not know how but now the system display errors like this one:

ls: error while loading shared libraries: libpcre.so.3: cannot open shared object file: No such file or directory

Some commands are not working (ls, cd, vi, apt-get, dpkg,...)
I cannot connect by SSH into the server and I do not know what to do

Please, could you help me with this critical issue.
It is very important for me.

Thanks in advance

---

### Post by QDR06VV9 on 2016-04-04
See if this gets you sorted out.
[http://askubuntu.com/questions/309228/apache-service-not-starting](http://askubuntu.com/questions/309228/apache-service-not-starting)

---

### Post by Impavidus on 2016-04-05
Not sure what you did exactly. Could you elaborate?

Anyway, libpcre.so.3 should be a symbolic link to the most recent version of libpcre.so.3.x.x. You may have broken that link. There can be both a 32-bit and a 64-bit version. On my system:```
$ dpkg --search libpcre.so.3
libpcre3:i386: /lib/i386-linux-gnu/libpcre.so.3.13.1
libpcre3:amd64: /lib/x86_64-linux-gnu/libpcre.so.3
libpcre3:i386: /lib/i386-linux-gnu/libpcre.so.3
libpcre3:amd64: /lib/x86_64-linux-gnu/libpcre.so.3.13.1

$  ls -l /lib/{i386,x86_64}-linux-gnu/libpcre.so.3{,.13.1}
lrwxrwxrwx 1 root root     17 mrt 29 15:40 /lib/i386-linux-gnu/libpcre.so.3 -> libpcre.so.3.13.1
-rw-r--r-- 1 root root 464176 mrt 29 15:41 /lib/i386-linux-gnu/libpcre.so.3.13.1
lrwxrwxrwx 1 root root     17 mrt 29 15:40 /lib/x86_64-linux-gnu/libpcre.so.3 -> libpcre.so.3.13.1
-rw-r--r-- 1 root root 448440 mrt 29 15:40 /lib/x86_64-linux-gnu/libpcre.so.3.13.1

```If nothing else works, try fixing using a live disk.

Generally, it's not a very good idea to manually replace files in /lib, as many vital tools depend on specific versions. If you manually installed some software that depends on a more recent version, there may be other ways to install two versions of libpcre alongside each other.

---

### Post by mysql69 on 2016-04-05
> **Impavidus said:**
> Not sure what you did exactly. Could you elaborate?

Anyway, libpcre.so.3 should be a symbolic link to the most recent version of libpcre.so.3.x.x. You may have broken that link. There can be both a 32-bit and a 64-bit version. On my system:```
$ dpkg --search libpcre.so.3
libpcre3:i386: /lib/i386-linux-gnu/libpcre.so.3.13.1
libpcre3:amd64: /lib/x86_64-linux-gnu/libpcre.so.3
libpcre3:i386: /lib/i386-linux-gnu/libpcre.so.3
libpcre3:amd64: /lib/x86_64-linux-gnu/libpcre.so.3.13.1

$  ls -l /lib/{i386,x86_64}-linux-gnu/libpcre.so.3{,.13.1}
lrwxrwxrwx 1 root root     17 mrt 29 15:40 /lib/i386-linux-gnu/libpcre.so.3 -> libpcre.so.3.13.1
-rw-r--r-- 1 root root 464176 mrt 29 15:41 /lib/i386-linux-gnu/libpcre.so.3.13.1
lrwxrwxrwx 1 root root     17 mrt 29 15:40 /lib/x86_64-linux-gnu/libpcre.so.3 -> libpcre.so.3.13.1
-rw-r--r-- 1 root root 448440 mrt 29 15:40 /lib/x86_64-linux-gnu/libpcre.so.3.13.1

```If nothing else works, try fixing using a live disk.

Generally, it's not a very good idea to manually replace files in /lib, as many vital tools depend on specific versions. If you manually installed some software that depends on a more recent version, there may be other ways to install two versions of libpcre alongside each other.

Thanks for your answer Impavidus.

I have reboot the server and now the system can not boot.
Kernel Panic - not syncing: Attempted to kill init!

I think that my problem was to removed the symbolic lync as you said.
How can I restore from a live cd? I have never done before.

Regards

---

### Post by Impavidus on 2016-04-05
You can put a live dvd or live usb (the same you use to install a desktop system) into the computer and boot from that. Once you reach the desktop, you can mount the root partition of the installed system and fix things. You can also chroot into the installed system and use the package manager to fix things. See [https://help.ubuntu.com/community/LiveCdRecovery](https://help.ubuntu.com/community/LiveCdRecovery).

---

