---
title: "captive..."
date: 2005-03-22
forum: General Help
---

### Post by Trab on 2005-03-22
ive searched around a bit trying to find info on my problem, but i cannot get captive and ubuntu to work!

here is the error i get
```

tedd@raptor:~ $ sudo /usr/share/lufs/prepmod
+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.8.1-5-386 (base version 2.6.8.1)
Destination module directory: /lib/modules/2.6.8.1-5-386/kernel/fs/lufs
Using kernel sources: /lib/modules/2.6.8.1-5-386/build
+ set -e; /bin/mkdir -p `dirname /var/lib/lufs/lufs.ko`; /bin/rm -f /var/lib/lufs/lufs.ko; make -C /lib/modules/2.6.8.1-5-386/build SUBDIRS="/usr/share/lufs/2.6" modules EXTRA_CFLAGS=""; /bin/mv -f /usr/share/lufs/2.6/lufs.ko /var/lib/lufs/lufs.ko; /bin/rm -f /usr/share/lufs/2.6/proc.o /usr/share/lufs/2.6/.proc.o.flags /usr/share/lufs/2.6/.proc.o.cmd /usr/share/lufs/2.6/inode.o /usr/share/lufs/2.6/.inode.o.flags /usr/share/lufs/2.6/.inode.o.cmd /usr/share/lufs/2.6/dir.o /usr/share/lufs/2.6/.dir.o.flags /usr/share/lufs/2.6/.dir.o.cmd /usr/share/lufs/2.6/file.o /usr/share/lufs/2.6/.file.o.flags /usr/share/lufs/2.6/.file.o.cmd /usr/share/lufs/2.6/symlink.o /usr/share/lufs/2.6/.symlink.o.flags /usr/share/lufs/2.6/.symlink.o.cmd /usr/share/lufs/2.6/lufs.mod.o /usr/share/lufs/2.6/.lufs.mod.o.flags /usr/share/lufs/2.6/.lufs.mod.o.cmd /usr/share/lufs/2.6/lufs.o /usr/share/lufs/2.6/.lufs.o.flags /usr/share/lufs/2.6/.lufs.o.cmd /usr/share/lufs/2.6/lufs.mod.c /usr/share/lufs/2.6/.lufs.ko.cmd;
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
make: Entering directory `/usr/src/linux-headers-2.6.8.1-5-386'
  CC [M]  /usr/share/lufs/2.6/dir.o
/bin/sh: line 1: gcc: command not found
make[1]: *** [/usr/share/lufs/2.6/dir.o] Error 127
make: *** [_module_/usr/share/lufs/2.6] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-5-386'
+ find /lib/modules/2.6.8.1-5-386/build -name .depend|xargs rm -f; rm -f /lib/modules/2.6.8.1-5-386/build/scripts/mkdep; rm -f /lib/modules/2.6.8.1-5-386/build/scripts/split-include; make -C /lib/modules/2.6.8.1-5-386/build dep
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
make: Entering directory `/usr/src/linux-headers-2.6.8.1-5-386'
*** Warning: make dep is unnecessary now.
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-5-386'
+ set -e; /bin/mkdir -p `dirname /var/lib/lufs/lufs.ko`; /bin/rm -f /var/lib/lufs/lufs.ko; make -C /lib/modules/2.6.8.1-5-386/build SUBDIRS="/usr/share/lufs/2.6" modules EXTRA_CFLAGS=""; /bin/mv -f /usr/share/lufs/2.6/lufs.ko /var/lib/lufs/lufs.ko; /bin/rm -f /usr/share/lufs/2.6/proc.o /usr/share/lufs/2.6/.proc.o.flags /usr/share/lufs/2.6/.proc.o.cmd /usr/share/lufs/2.6/inode.o /usr/share/lufs/2.6/.inode.o.flags /usr/share/lufs/2.6/.inode.o.cmd /usr/share/lufs/2.6/dir.o /usr/share/lufs/2.6/.dir.o.flags /usr/share/lufs/2.6/.dir.o.cmd /usr/share/lufs/2.6/file.o /usr/share/lufs/2.6/.file.o.flags /usr/share/lufs/2.6/.file.o.cmd /usr/share/lufs/2.6/symlink.o /usr/share/lufs/2.6/.symlink.o.flags /usr/share/lufs/2.6/.symlink.o.cmd /usr/share/lufs/2.6/lufs.mod.o /usr/share/lufs/2.6/.lufs.mod.o.flags /usr/share/lufs/2.6/.lufs.mod.o.cmd /usr/share/lufs/2.6/lufs.o /usr/share/lufs/2.6/.lufs.o.flags /usr/share/lufs/2.6/.lufs.o.cmd /usr/share/lufs/2.6/lufs.mod.c /usr/share/lufs/2.6/.lufs.ko.cmd;
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
make: Entering directory `/usr/src/linux-headers-2.6.8.1-5-386'
  CC [M]  /usr/share/lufs/2.6/dir.o
/bin/sh: line 1: gcc: command not found
make[1]: *** [/usr/share/lufs/2.6/dir.o] Error 127
make: *** [_module_/usr/share/lufs/2.6] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-5-386'
Failed to prepare lufs.ko module for your Linux kernel 2.6.8.1-5-386.
Detected Linux kernel sources "/lib/modules/2.6.8.1-5-386/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.8.1-5-386/build
                /usr/src/kernel-headers-2.6.8.1-5-386
                /usr/src/linux-2.6.8.1-5-386
                /usr/src/linux-2.6.8.1
                /usr/src/linux
                /usr/src/kernel-source-2.6.8.1-5-386

```


it seems that my heads dont match up with my kernel version....=/ how can i fix this?
synaptic has yet to be of great help in this issue, please help!

thanks
-Trab

---

### Post by bored2k on 2005-03-22
> **Trab]ive searched around a bit trying to find info on my problem, but i cannot get captive and ubuntu to work!

here is the error i get
```

tedd@raptor:~ $ sudo /usr/share/lufs/prepmod
+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.8.1-5-386 (base version 2.6.8.1)
Destination module directory: /lib/modules/2.6.8.1-5-386/kernel/fs/lufs
Using kernel sources: /lib/modules/2.6.8.1-5-386/build
+ set -e said:**
>   /usr/share/lufs/2.6/dir.o
/bin/sh: line 1: gcc: command not found
make[1]: *** [/usr/share/lufs/2.6/dir.o] Error 127
make: *** [_module_/usr/share/lufs/2.6] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-5-386'
+ find /lib/modules/2.6.8.1-5-386/build -name .depend|xargs rm -f; rm -f /lib/modules/2.6.8.1-5-386/build/scripts/mkdep; rm -f /lib/modules/2.6.8.1-5-386/build/scripts/split-include; make -C /lib/modules/2.6.8.1-5-386/build dep
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
make: Entering directory `/usr/src/linux-headers-2.6.8.1-5-386'
*** Warning: make dep is unnecessary now.
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-5-386'
+ set -e; /bin/mkdir -p `dirname /var/lib/lufs/lufs.ko`; /bin/rm -f /var/lib/lufs/lufs.ko; make -C /lib/modules/2.6.8.1-5-386/build SUBDIRS="/usr/share/lufs/2.6" modules EXTRA_CFLAGS=""; /bin/mv -f /usr/share/lufs/2.6/lufs.ko /var/lib/lufs/lufs.ko; /bin/rm -f /usr/share/lufs/2.6/proc.o /usr/share/lufs/2.6/.proc.o.flags /usr/share/lufs/2.6/.proc.o.cmd /usr/share/lufs/2.6/inode.o /usr/share/lufs/2.6/.inode.o.flags /usr/share/lufs/2.6/.inode.o.cmd /usr/share/lufs/2.6/dir.o /usr/share/lufs/2.6/.dir.o.flags /usr/share/lufs/2.6/.dir.o.cmd /usr/share/lufs/2.6/file.o /usr/share/lufs/2.6/.file.o.flags /usr/share/lufs/2.6/.file.o.cmd /usr/share/lufs/2.6/symlink.o /usr/share/lufs/2.6/.symlink.o.flags /usr/share/lufs/2.6/.symlink.o.cmd /usr/share/lufs/2.6/lufs.mod.o /usr/share/lufs/2.6/.lufs.mod.o.flags /usr/share/lufs/2.6/.lufs.mod.o.cmd /usr/share/lufs/2.6/lufs.o /usr/share/lufs/2.6/.lufs.o.flags /usr/share/lufs/2.6/.lufs.o.cmd /usr/share/lufs/2.6/lufs.mod.c /usr/share/lufs/2.6/.lufs.ko.cmd;
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
make: Entering directory `/usr/src/linux-headers-2.6.8.1-5-386'
  CC [M]  /usr/share/lufs/2.6/dir.o
/bin/sh: line 1: gcc: command not found
make[1]: *** [/usr/share/lufs/2.6/dir.o] Error 127
make: *** [_module_/usr/share/lufs/2.6] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-5-386'
Failed to prepare lufs.ko module for your Linux kernel 2.6.8.1-5-386.
Detected Linux kernel sources "/lib/modules/2.6.8.1-5-386/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.8.1-5-386/build
                /usr/src/kernel-headers-2.6.8.1-5-386
                /usr/src/linux-2.6.8.1-5-386
                /usr/src/linux-2.6.8.1
                /usr/src/linux
                /usr/src/kernel-source-2.6.8.1-5-386

```


it seems that my heads dont match up with my kernel version....=/ how can i fix this?
synaptic has yet to be of great help in this issue, please help!

thanks
-Trab
 [http://ubuntuforums.org/showthread.php?t=10175&highlight=captive+ntfs](http://ubuntuforums.org/showthread.php?t=10175&highlight=captive+ntfs) [how to]

I have a saying that goes: If you dont know how to install something in Linux, its probably because you're not prepared to use it .

Word of advice: **backup**

---

### Post by Trab on 2005-03-26
while ur concern form my computers well being is appcrated, i would rather have captive installed :-)
i checked my headers via apt-get...heres the errors...
```

tedd@raptor:~ $ uname -a
Linux raptor 2.6.8.1-5-386 #1 Mon Mar 14 21:44:04 UTC 2005 i686 GNU/Linux
tedd@raptor:~ $ sudo apt-get install linux-headers-2.6.8.1-5-386
Password:
Reading Package Lists... Done
Building Dependency Tree... Done
linux-headers-2.6.8.1-5-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
tedd@raptor:~ $ sudo captive-install-acquire
tedd@raptor:~ $ sudo /usr/share/lufs/prepmod
+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.8.1-5-386 (base version 2.6.8.1)
Destination module directory: /lib/modules/2.6.8.1-5-386/kernel/fs/lufs
Using kernel sources: /lib/modules/2.6.8.1-5-386/build
+ set -e; /bin/mkdir -p `dirname /var/lib/lufs/lufs.ko`; /bin/rm -f /var/lib/lufs/lufs.ko; make -C /lib/modules/2.6.8.1-5-386/build SUBDIRS="/usr/share/lufs/2.6" modules EXTRA_CFLAGS=""; /bin/mv -f /usr/share/lufs/2.6/lufs.ko /var/lib/lufs/lufs.ko; /bin/rm -f /usr/share/lufs/2.6/proc.o /usr/share/lufs/2.6/.proc.o.flags /usr/share/lufs/2.6/.proc.o.cmd /usr/share/lufs/2.6/inode.o /usr/share/lufs/2.6/.inode.o.flags /usr/share/lufs/2.6/.inode.o.cmd /usr/share/lufs/2.6/dir.o /usr/share/lufs/2.6/.dir.o.flags /usr/share/lufs/2.6/.dir.o.cmd /usr/share/lufs/2.6/file.o /usr/share/lufs/2.6/.file.o.flags /usr/share/lufs/2.6/.file.o.cmd /usr/share/lufs/2.6/symlink.o /usr/share/lufs/2.6/.symlink.o.flags /usr/share/lufs/2.6/.symlink.o.cmd /usr/share/lufs/2.6/lufs.mod.o /usr/share/lufs/2.6/.lufs.mod.o.flags /usr/share/lufs/2.6/.lufs.mod.o.cmd /usr/share/lufs/2.6/lufs.o /usr/share/lufs/2.6/.lufs.o.flags /usr/share/lufs/2.6/.lufs.o.cmd /usr/share/lufs/2.6/lufs.mod.c /usr/share/lufs/2.6/.lufs.ko.cmd;
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
make: Entering directory `/usr/src/linux-headers-2.6.8.1-5-386'
  CC [M]  /usr/share/lufs/2.6/dir.o
/bin/sh: line 1: gcc: command not found
make[1]: *** [/usr/share/lufs/2.6/dir.o] Error 127
make: *** [_module_/usr/share/lufs/2.6] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-5-386'
+ find /lib/modules/2.6.8.1-5-386/build -name .depend|xargs rm -f; rm -f /lib/modules/2.6.8.1-5-386/build/scripts/mkdep; rm -f /lib/modules/2.6.8.1-5-386/build/scripts/split-include; make -C /lib/modules/2.6.8.1-5-386/build dep
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
make: Entering directory `/usr/src/linux-headers-2.6.8.1-5-386'
*** Warning: make dep is unnecessary now.
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-5-386'
+ set -e; /bin/mkdir -p `dirname /var/lib/lufs/lufs.ko`; /bin/rm -f /var/lib/lufs/lufs.ko; make -C /lib/modules/2.6.8.1-5-386/build SUBDIRS="/usr/share/lufs/2.6" modules EXTRA_CFLAGS=""; /bin/mv -f /usr/share/lufs/2.6/lufs.ko /var/lib/lufs/lufs.ko; /bin/rm -f /usr/share/lufs/2.6/proc.o /usr/share/lufs/2.6/.proc.o.flags /usr/share/lufs/2.6/.proc.o.cmd /usr/share/lufs/2.6/inode.o /usr/share/lufs/2.6/.inode.o.flags /usr/share/lufs/2.6/.inode.o.cmd /usr/share/lufs/2.6/dir.o /usr/share/lufs/2.6/.dir.o.flags /usr/share/lufs/2.6/.dir.o.cmd /usr/share/lufs/2.6/file.o /usr/share/lufs/2.6/.file.o.flags /usr/share/lufs/2.6/.file.o.cmd /usr/share/lufs/2.6/symlink.o /usr/share/lufs/2.6/.symlink.o.flags /usr/share/lufs/2.6/.symlink.o.cmd /usr/share/lufs/2.6/lufs.mod.o /usr/share/lufs/2.6/.lufs.mod.o.flags /usr/share/lufs/2.6/.lufs.mod.o.cmd /usr/share/lufs/2.6/lufs.o /usr/share/lufs/2.6/.lufs.o.flags /usr/share/lufs/2.6/.lufs.o.cmd /usr/share/lufs/2.6/lufs.mod.c /usr/share/lufs/2.6/.lufs.ko.cmd;
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
/usr/src/linux-headers-2.6.8.1-5-386/scripts/gcc-version.sh: line 1: gcc: command not found
make: Entering directory `/usr/src/linux-headers-2.6.8.1-5-386'
  CC [M]  /usr/share/lufs/2.6/dir.o
/bin/sh: line 1: gcc: command not found
make[1]: *** [/usr/share/lufs/2.6/dir.o] Error 127
make: *** [_module_/usr/share/lufs/2.6] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-5-386'
Failed to prepare lufs.ko module for your Linux kernel 2.6.8.1-5-386.
Detected Linux kernel sources "/lib/modules/2.6.8.1-5-386/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.8.1-5-386/build
                /usr/src/kernel-headers-2.6.8.1-5-386
                /usr/src/linux-2.6.8.1-5-386
                /usr/src/linux-2.6.8.1
                /usr/src/linux
                /usr/src/kernel-source-2.6.8.1-5-386
tedd@raptor:~ $ sudo apt-get install linux-headers-2.6.8.1-5-386
Reading Package Lists... Done
Building Dependency Tree... Done
linux-headers-2.6.8.1-5-386 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 40 not upgraded.
tedd@raptor:~ $

```

any more help? 
i know its a big thing to understand, i dont fully get it, but i think it doesnt like my kernel headers...any way to trick it to work?
thanks!
-Trab

---

