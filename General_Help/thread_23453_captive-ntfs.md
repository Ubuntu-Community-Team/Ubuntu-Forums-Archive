---
title: "captive-ntfs"
date: 2005-04-02
forum: General Help
---

### Post by t3rm1n8r1x on 2005-04-02
I installed captive-ntfs to be able to write to my winxp ntfs partition, but now I can't mount it. the site told me to run /usr/share/lufs/prepmod to see why, but I don't understand the output. anyone want to help me?

sudo /usr/share/lufs/prepmod
Password:
+ /sbin/modprobe lufs 2>/dev/null
Preparing LUFS kernel module... Run /usr/share/lufs/prepmod if problems occur.
Running kernel version: 2.6.8.1-3-386 (base version 2.6.8.1)
Destination module directory: /lib/modules/2.6.8.1-3-386/kernel/fs/lufs
Using kernel sources: /lib/modules/2.6.8.1-3-386/build
+ set -e; /bin/mkdir -p `Untitled 1dirname /var/lib/lufs/lufs.ko`; /bin/rm -f /var/lib/luf s/lufs.ko; make -C /lib/modules/2.6.8.1-3-386/build SUBDIRS="/usr/share/lufs/2.6 " modules EXTRA_CFLAGS=""; /bin/mv -f /usr/share/lufs/2.6/lufs.ko /var/lib/lufs/ lufs.ko; /bin/rm -f /usr/share/lufs/2.6/proc.o /usr/share/lufs/2.6/.proc.o.flags  /usr/share/lufs/2.6/.proc.o.cmd /usr/share/lufs/2.6/inode.o /usr/share/lufs/2.6 /.inode.o.flags /usr/share/lufs/2.6/.inode.o.cmd /usr/share/lufs/2.6/dir.o /usr/ share/lufs/2.6/.dir.o.flags /usr/share/lufs/2.6/.dir.o.cmd /usr/share/lufs/2.6/f ile.o /usr/share/lufs/2.6/.file.o.flags /usr/share/lufs/2.6/.file.o.cmd /usr/sha re/lufs/2.6/symlink.o /usr/share/lufs/2.6/.symlink.o.flags /usr/share/lufs/2.6/. symlink.o.cmd /usr/share/lufs/2.6/lufs.mod.o /usr/share/lufs/2.6/.lufs.mod.o.fla gs /usr/share/lufs/2.6/.lufs.mod.o.cmd /usr/share/lufs/2.6/lufs.o /usr/share/luf s/2.6/.lufs.o.flags /usr/share/lufs/2.6/.lufs.o.cmd /usr/share/lufs/2.6/lufs.mod .c /usr/share/lufs/2.6/.lufs.ko.cmd;
/usr/src/linux-headers-2.6.8.1-3-386/scripts/gcc-version.sh: line 1: gcc: comman d not found
/usr/src/linux-headers-2.6.8.1-3-386/scripts/gcc-version.sh: line 1: gcc: comman d not found
make: Entering directory `/usr/src/linux-headers-2.6.8.1-3-386'
  CC [M]  /usr/share/lufs/2.6/dir.o
/bin/sh: line 1: gcc: command not found
make[1]: *** [/usr/share/lufs/2.6/dir.o] Error 127
make: *** [_module_/usr/share/lufs/2.6] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-3-386'
+ find /lib/modules/2.6.8.1-3-386/build -name .depend|xargs rm -f; rm -f /lib/mo dules/2.6.8.1-3-386/build/scripts/mkdep; rm -f /lib/modules/2.6.8.1-3-386/build/ scripts/split-include; make -C /lib/modules/2.6.8.1-3-386/build dep
/usr/src/linux-headers-2.6.8.1-3-386/scripts/gcc-version.sh: line 1: gcc: comman d not found
/usr/src/linux-headers-2.6.8.1-3-386/scripts/gcc-version.sh: line 1: gcc: comman d not found
make: Entering directory `/usr/src/linux-headers-2.6.8.1-3-386'
*** Warning: make dep is unnecessary now.
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-3-386'
+ set -e; /bin/mkdir -p `dirname /var/lib/lufs/lufs.ko`; /bin/rm -f /var/lib/luf s/lufs.ko; make -C /lib/modules/2.6.8.1-3-386/build SUBDIRS="/usr/share/lufs/2.6 " modules EXTRA_CFLAGS=""; /bin/mv -f /usr/share/lufs/2.6/lufs.ko /var/lib/lufs/ lufs.ko; /bin/rm -f /usr/share/lufs/2.6/proc.o /usr/share/lufs/2.6/.proc.o.flags  /usr/share/lufs/2.6/.proc.o.cmd /usr/share/lufs/2.6/inode.o /usr/share/lufs/2.6 /.inode.o.flags /usr/share/lufs/2.6/.inode.o.cmd /usr/share/lufs/2.6/dir.o /usr/ share/lufs/2.6/.dir.o.flags /usr/share/lufs/2.6/.dir.o.cmd /usr/share/lufs/2.6/f ile.o /usr/share/lufs/2.6/.file.o.flags /usr/share/lufs/2.6/.file.o.cmd /usr/sha re/lufs/2.6/symlink.o /usr/share/lufs/2.6/.symlink.o.flags /usr/share/lufs/2.6/. symlink.o.cmd /usr/share/lufs/2.6/lufs.mod.o /usr/share/lufs/2.6/.lufs.mod.o.fla gs /usr/share/lufs/2.6/.lufs.mod.o.cmd /usr/share/lufs/2.6/lufs.o /usr/share/luf s/2.6/.lufs.o.flags /usr/share/lufs/2.6/.lufs.o.cmd /usr/share/lufs/2.6/lufs.mod .c /usr/share/lufs/2.6/.lufs.ko.cmd;
/usr/src/linux-headers-2.6.8.1-3-386/scripts/gcc-version.sh: line 1: gcc: comman d not found
/usr/src/linux-headers-2.6.8.1-3-386/scripts/gcc-version.sh: line 1: gcc: comman d not found
make: Entering directory `/usr/src/linux-headers-2.6.8.1-3-386'
  CC [M]  /usr/share/lufs/2.6/dir.o
/bin/sh: line 1: gcc: command not found
make[1]: *** [/usr/share/lufs/2.6/dir.o] Error 127
make: *** [_module_/usr/share/lufs/2.6] Error 2
make: Leaving directory `/usr/src/linux-headers-2.6.8.1-3-386'
Failed to prepare lufs.ko module for your Linux kernel 2.6.8.1-3-386.
Detected Linux kernel sources "/lib/modules/2.6.8.1-3-386/build" do not appear to be valid.
Please install kernel-source-x.y.z.i386.rpm or kernel-headers_x.y.z_i386.deb.
The following directory paths were search (first existing directory used):
                /lib/modules/2.6.8.1-3-386/build
                /usr/src/kernel-headers-2.6.8.1-3-386
                /usr/src/linux-2.6.8.1-3-386
                /usr/src/linux-2.6.8.1
                /usr/src/linux
                /usr/src/kernel-source-2.6.8.1-3-386

---

### Post by Juergen on 2005-04-02
Well, I think your main problem is this:
> /bin/sh: line 1: gcc: command not foundInstall the package 'build-essential' to get all the stuff needed to compile and try again.

---

