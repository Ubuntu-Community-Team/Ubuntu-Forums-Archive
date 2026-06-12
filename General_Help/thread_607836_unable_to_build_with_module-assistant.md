---
title: "unable to build with module-assistant"
date: 2007-11-09
forum: General Help
---

### Post by edccmu22 on 2007-11-09
I'm trying to get shfs working, but I'm stuck on the following line:

$sudo module-assistant build shfs

In the interactive mode is says: "Build of package shfs-source failed!"

The log file looks like this:

```

dh_clean
make -C Linux-2.6 clean
make[1]: Entering directory `/usr/src/modules/shfs/Linux-2.6'
rm -rf linux-2.6.22-14-generic linux-2.6.22-14-generic.orig;
rm -f linux-2.6.22-14-generic.diff
rm -f *.o *.ko *.mod.c .*o.cmd
make[1]: Leaving directory `/usr/src/modules/shfs/Linux-2.6'
/usr/bin/make  -f debian/rules kdist_clean kdist_config binary-modules
make[1]: Entering directory `/usr/src/modules/shfs'
dh_clean
make -C Linux-2.6 clean
make[2]: Entering directory `/usr/src/modules/shfs/Linux-2.6'
rm -rf linux-2.6.22-14-generic linux-2.6.22-14-generic.orig;
rm -f linux-2.6.22-14-generic.diff
rm -f *.o *.ko *.mod.c .*o.cmd
make[2]: Leaving directory `/usr/src/modules/shfs/Linux-2.6'
for templ in /usr/src/modules/shfs/debian/shfs-module-_KVERS_.postinst /usr/src/modules/shfs/debian/shfs-module-_KVERS_.postinst.backup /usr/src/modules/shfs/debian/shfs-module-_KVERS_.postinst.modules.in; do \
    cp $templ `echo $templ | sed -e 's/_KVERS_/2.6.22-14-generic/g'` ; \
  done
for templ in `ls debian/*.modules.in` ; do \
    test -e ${templ%.modules.in}.backup || cp ${templ%.modules.in} ${templ%.modules.in}.backup 2>/dev/null || true; \
    sed -e 's/##KVERS##/2.6.22-14-generic/g ;s/#KVERS#/2.6.22-14-generic/g ; s/_KVERS_/2.6.22-14-generic/g ; s/##KDREV##/2.6.22-14.46/g ; s/#KDREV#/2.6.22-14.46/g ; s/_KDREV_/2.6.22-14.46/g  ' < $templ > ${templ%.modules.in}; \
  done
dh_testdir
dh_testroot
dh_clean -k
env MODVERSIONS=detect make -C Linux-2.6 KERNEL_SOURCES=/usr/src/linux KERNEL=linux-2.6.22-14-generic
make[2]: Entering directory `/usr/src/modules/shfs/Linux-2.6'
make -C /usr/src/linux SUBDIRS=/usr/src/modules/shfs/Linux-2.6 modules
make[3]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /usr/src/modules/shfs/Linux-2.6/dcache.o
In file included from /usr/src/modules/shfs/Linux-2.6/dcache.c:24:
/usr/src/modules/shfs/Linux-2.6/shfs_fs.h:76: warning: ‘kmem_cache_t’ is deprecated
/usr/src/modules/shfs/Linux-2.6/shfs_fs.h:77: warning: ‘kmem_cache_t’ is deprecated
/usr/src/modules/shfs/Linux-2.6/shfs_fs.h:78: warning: ‘kmem_cache_t’ is deprecated
/usr/src/modules/shfs/Linux-2.6/shfs_fs.h:79: warning: ‘kmem_cache_t’ is deprecated
In file included from /usr/src/modules/shfs/Linux-2.6/dcache.c:26:
/usr/src/modules/shfs/Linux-2.6/shfs_debug.h:22: warning: ‘kmem_cache_t’ is deprecated
/usr/src/modules/shfs/Linux-2.6/shfs_debug.h:35: warning: ‘kmem_cache_t’ is deprecated
  CC [M]  /usr/src/modules/shfs/Linux-2.6/dir.o
In file included from /usr/src/modules/shfs/Linux-2.6/dir.c:17:
/usr/src/modules/shfs/Linux-2.6/shfs_fs.h:76: warning: ‘kmem_cache_t’ is deprecated
/usr/src/modules/shfs/Linux-2.6/shfs_fs.h:77: warning: ‘kmem_cache_t’ is deprecated
/usr/src/modules/shfs/Linux-2.6/shfs_fs.h:78: warning: ‘kmem_cache_t’ is deprecated
/usr/src/modules/shfs/Linux-2.6/shfs_fs.h:79: warning: ‘kmem_cache_t’ is deprecated
In file included from /usr/src/modules/shfs/Linux-2.6/dir.c:19:
/usr/src/modules/shfs/Linux-2.6/shfs_debug.h:22: warning: ‘kmem_cache_t’ is deprecated
/usr/src/modules/shfs/Linux-2.6/shfs_debug.h:35: warning: ‘kmem_cache_t’ is deprecated
/usr/src/modules/shfs/Linux-2.6/dir.c: In function ‘shfs_create’:
/usr/src/modules/shfs/Linux-2.6/dir.c:305: error: ‘struct inode’ has no member named ‘u’
/usr/src/modules/shfs/Linux-2.6/dir.c:306: error: ‘struct inode’ has no member named ‘u’
make[4]: *** [/usr/src/modules/shfs/Linux-2.6/dir.o] Error 1
make[3]: *** [_module_/usr/src/modules/shfs/Linux-2.6] Error 2
make[3]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make[2]: *** [default] Error 2
make[2]: Leaving directory `/usr/src/modules/shfs/Linux-2.6'
make[1]: *** [binary-modules] Error 2
make[1]: Leaving directory `/usr/src/modules/shfs'
make: *** [kdist_build] Error 2

```

I can't tell what exactly is going wrong here.  Any help would be much appreciated.  Thanks in advance.

---

### Post by wsams on 2008-01-17
I'm having this exact same error.

---

### Post by bernt_ on 2008-02-04
Same errors here too.

But the sad thing is:
the last chnages in the shfs-cvs-tree are 3 year ago!

It seem that this project has died :-(

---

