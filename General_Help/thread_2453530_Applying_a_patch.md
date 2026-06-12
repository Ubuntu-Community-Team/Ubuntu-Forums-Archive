---
title: "Applying a patch?"
date: 2020-11-12
forum: General Help
---

### Post by David_Partridge on 2020-11-12
After reporting a problem to the linux-usb mailing list about Seagate USB-ATA bridge not supporting "Write Same" I have been sent a patch to try on my system:

 Ubuntu 20.04.1 LTS (GNU/Linux 5.4.0-53-generic x86_64)

```
From 53a5cacbf61ce6a4935723849ad602f38d8f9a52 Mon Sep 17 00:00:00 2001
From: Oliver Neukum <oneukum@suse.com>
Date: Wed, 11 Nov 2020 12:37:15 +0100
Subject: [PATCH] USB: UAS: introduce a quirk to set no_write_same

UAS does not share the pessimistic assumption storage
is making that devices cannot deal with WRITE_SAME.
A few devices supported by UAS, are reported to not
deal well with WRITE_SAME. Those need a quirk.

Signed-off-by: Oliver Neukum <oneukum@suse.com>
---
 drivers/usb/storage/uas.c | 3 +++
 drivers/usb/storage/usb.c | 3 +++
 include/linux/usb_usual.h | 2 ++
 3 files changed, 8 insertions(+)

diff --git a/drivers/usb/storage/uas.c b/drivers/usb/storage/uas.c
index c8a577309e8f..1e1daa3da4b5 100644
--- a/drivers/usb/storage/uas.c
+++ b/drivers/usb/storage/uas.c
@@ -874,6 +874,9 @@ static int uas_slave_configure(struct scsi_device *sdev)
     if (devinfo->flags & US_FL_NO_READ_CAPACITY_16)
         sdev->no_read_capacity_16 = 1;
 
+    /* Some disks cannot handle WRITE_SAME */
+    if (devinfo->flags & US_FL_NO_SAME)
+        sdev->no_write_same = 1;
     /*
      * Some disks return the total number of blocks in response
      * to READ CAPACITY rather than the highest block number.
diff --git a/drivers/usb/storage/usb.c b/drivers/usb/storage/usb.c
index c2ef367cf257..08b469511043 100644
--- a/drivers/usb/storage/usb.c
+++ b/drivers/usb/storage/usb.c
@@ -541,6 +541,9 @@ void usb_stor_adjust_quirks(struct usb_device *udev, unsigned long *fflags)
         case 'j':
             f |= US_FL_NO_REPORT_LUNS;
             break;
+        case 'k':
+            f |= US_FL_NO_SAME;
+            break;
         case 'l':
             f |= US_FL_NOT_LOCKABLE;
             break;
diff --git a/include/linux/usb_usual.h b/include/linux/usb_usual.h
index 4a19ac3f24d0..6b03fdd69d27 100644
--- a/include/linux/usb_usual.h
+++ b/include/linux/usb_usual.h
@@ -84,6 +84,8 @@
         /* Cannot handle REPORT_LUNS */            \
     US_FLAG(ALWAYS_SYNC, 0x20000000)            \
         /* lies about caching, so always sync */    \
+    US_FLAG(NO_SAME, 0x40000000)                \
+        /* Cannot handle WRITE_SAME */            \
 
 #define US_FLAG(name, value)    US_FL_##name = value ,
 enum { US_DO_ALL_FLAGS };
-- 
2.26.2



```

Please could one of you kind folks tell me exactly how I do this please?

Thanks
David

---

### Post by David_Partridge on 2020-11-14
In the absence of any guidance I tried following the <https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel>

I did [FONT=courier new]apt-get source linux-image-$(uname -r)[FONT=arial]followed by [FONT=courier new]LANG=C fakeroot debian/rules binary
[/FONT]
But while that generated some large .deb files, I cannot find the source files for the kernel that I need to patch.

Where are they please?  Or do I need to do more things that aren't in the wiki?

David

[/FONT]


[/FONT]

---

### Post by David_Partridge on 2020-11-14
In the absence of any guidance I tried following the <https://wiki.ubuntu.com/Kernel/BuildYourOwnKernel>

I did [FONT=courier new]apt-get source linux-image-$(uname -r)[FONT=arial]followed by [FONT=courier new]LANG=C fakeroot debian/rules binary
[/FONT]
But while that generated some large .deb files, I cannot find the source files for the kernel that I need to patch.

Where are they please?  Or do I need to do more things that aren't in the wiki?

David

[/FONT]


[/FONT]

---

### Post by David_Partridge on 2020-11-16
Anyone out there who knows how to do this???  Surely someone must know?  I installed the source package, but AFAICT nothing gets compiled ...

---

### Post by norobro on 2020-11-16
The kernel source should be in the directory /usr/src/linux-5.4.0. If not then execute: ```
$ sudo apt-get source linux
```

Once you have the source you need to apply the patch. Save the patch file somewhere and then cd to the kernel source root directory (/usr/src/linux-5.4.0) and run: ```
sudo patch -l -p1 < /path/to/patchfile
```

Next, copy your current config file from /boot to the kernel source root directory. Something like this:```
sudo cp /boot/config-5.4.0-54-generic /usr/src/linux-5.4.0/.config
```

Then follow the directions in your link for building and installing the kernel.

---

### Post by David_Partridge on 2020-11-17
Thanks, that got me further, and after I untar'd the source archive I was able to apply the patch OK.

However when I did: fakeroot debian/rules binary

I got```

: 
:
: 
Debug: install-source
install -d /usr/src/linux-source-5.4.0/debian/linux-source-5.4.0/usr/src/linux-source-5.4.0
Debug: /usr/src/linux-source-5.4.0/debian/stamps/stamp-prepare-perarch
rm -rf /usr/src/linux-source-5.4.0/debian/build/tools-perarch
install -d /usr/src/linux-source-5.4.0/debian/build/tools-perarch
rsync -a --exclude debian --exclude debian.master --exclude debian.master --exclude .git -a ./ /usr/src/linux-source-5.4.0/debian/build/tools-perarch/
touch /usr/src/linux-source-5.4.0/debian/stamps/stamp-prepare-perarch
touch: cannot touch '/usr/src/linux-source-5.4.0/debian/stamps/stamp-prepare-perarch': No such file or directory
make: *** [debian/rules.d/2-binary-arch.mk:662: /usr/src/linux-source-5.4.0/debian/stamps/stamp-prepare-perarch] Error 1
```

i then tried: LANG=C fakeroot debian/rules binary-headers binary-generic binary-perarch

but that got me:```
root@charon:/usr/src/linux-source-5.4.0# LANG=C fakeroot debian/rules binary-headers binary-generic binary-perarch
Debug: prepare-indep
dh_prep -i
Debug: install-headers
dh_testdir
dh_testroot
install -d /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54
find . -path './debian' -prune -o -path './debian.master' -prune \
  -o -path './include/*' -prune \
  -o -path './scripts/*' -prune -o -type f \
  \( -name 'Makefile*' -o -name 'Kconfig*' -o -name 'Kbuild*' -o \
     -name '*.sh' -o -name '*.pl' -o -name '*.lds' \) \
  -print | cpio -pd --preserve-modification-time /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54
18832 blocks
cp -a scripts include /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54
(find arch -name include -type d -print | \
    xargs -n1 -i: find : -type f) | \
    cpio -pd --preserve-modification-time /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/csky/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/csky/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/unicore32/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/unicore32/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/alpha/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/alpha/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/arm/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/arm/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/ia64/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/ia64/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/arc/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/arc/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/c6x/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/c6x/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/um/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/nds32/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/nds32/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/arm64/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/arm64/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/powerpc/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/powerpc/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/mips/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/mips/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/sh/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/sh/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/xtensa/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/xtensa/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/microblaze/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/microblaze/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/h8300/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/h8300/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/riscv/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/riscv/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/s390/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/s390/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/hexagon/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/hexagon/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/nios2/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/nios2/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/x86/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/x86/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/openrisc/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/openrisc/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/m68k/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/m68k/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/parisc/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/parisc/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/sparc/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-source-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/sparc/include/asm/Kbuild not created: newer or same age version exists
29749 blocks
Debug: binary-headers
dh_installchangelogs -plinux-headers-5.4.0-54
dh_installdocs -plinux-headers-5.4.0-54
dh_compress -plinux-headers-5.4.0-54
dh_fixperms -plinux-headers-5.4.0-54
dh_installdeb -plinux-headers-5.4.0-54
flock -w 60 /usr/src/linux-source-5.4.0/debian/.LOCK dh_gencontrol -plinux-headers-5.4.0-54
dh_md5sums -plinux-headers-5.4.0-54
dh_builddeb -plinux-headers-5.4.0-54
dpkg-deb: building package 'linux-headers-5.4.0-54' in '../linux-headers-5.4.0-54_5.4.0-54.60_all.deb'.
cc -o debian/scripts/fix-filenames debian/scripts/fix-filenames.c
Debug: /usr/src/linux-source-5.4.0/debian/stamps/stamp-prepare-tree-generic
install -d /usr/src/linux-source-5.4.0/debian/build/build-generic
touch /usr/src/linux-source-5.4.0/debian/build/build-generic/ubuntu-build
[ "false" != 'true' ] && true || \
    rsync -a --exclude debian --exclude debian.master --exclude debian.master * /usr/src/linux-source-5.4.0/debian/build/build-generic
cat /usr/src/linux-source-5.4.0/debian.master/config/config.common.ubuntu /usr/src/linux-source-5.4.0/debian.master/config/amd64/config.common.amd64 /usr/src/linux-source-5.4.0/debian.master/config/amd64/config.flavour.generic | sed -e 's/.*CONFIG_VERSION_SIGNATURE.*/CONFIG_VERSION_SIGNATURE="Ubuntu 5.4.0-54.60-generic 5.4.65"/' > /usr/src/linux-source-5.4.0/debian/build/build-generic/.config
find /usr/src/linux-source-5.4.0/debian/build/build-generic -name "*.ko" | xargs rm -f
make ARCH=x86 CROSS_COMPILE= KERNELVERSION=5.4.0-54-generic CONFIG_DEBUG_SECTION_MISMATCH=y KBUILD_BUILD_VERSION="60" LOCALVERSION= localver-extra= CFLAGS_MODULE="-DPKG_ABI=54" O=/usr/src/linux-source-5.4.0/debian/build/build-generic -j1 syncconfig prepare scripts
make[1]: Entering directory '/usr/src/linux-source-5.4.0'
make[2]: Entering directory '/usr/src/linux-source-5.4.0/debian/build/build-generic'
***
*** The source tree is not clean, please run 'make ARCH=x86 mrproper'
*** in /usr/src/linux-source-5.4.0
***
make[3]: *** [/usr/src/linux-source-5.4.0/Makefile:562: outputmakefile] Error 1
make[2]: *** [/usr/src/linux-source-5.4.0/Makefile:340: __build_one_by_one] Error 2
make[2]: Leaving directory '/usr/src/linux-source-5.4.0/debian/build/build-generic'
make[1]: *** [Makefile:179: sub-make] Error 2
make[1]: Leaving directory '/usr/src/linux-source-5.4.0'
make: *** [debian/rules.d/2-binary-arch.mk:34: /usr/src/linux-source-5.4.0/debian/stamps/stamp-prepare-tree-generic] Error 2
root@charon:/usr/src/linux-source-5.4.0# 

```

:(

David

---

### Post by norobro on 2020-11-17
> **David_Partridge said:**
> ... after I untar'd the source archive ...Are you applying the patches necessary to bring it to point release 54? The file linux_5.4.0-54.60.diff.gz, listed below, contains the patches. 

Please post a directory listing of /usr/src.

After executing 'apt-get source linux' my /usr/src directory looks like the following:```
/usr/src $ ls -l 
total 182644
drwxr-xr-x 27 root root      4096 Nov 17 16:59 linux-5.4.0
-rw-r--r--  1 root root   5474703 Nov 10 17:22 linux_5.4.0-54.60.diff.gz
-rw-r--r--  1 root root      7220 Nov 10 17:22 linux_5.4.0-54.60.dsc
-rw-r--r--  1 root root 170244619 Dec 11  2019 linux_5.4.0.orig.tar.gz
-rw-r--r--  1 root root      2257 Nov 17 10:19 usb.patch

```

---

### Post by David_Partridge on 2020-11-17
Here you go:

```
amonra@charon:~$ ll /usr/src
total 182652
drwxr-xr-x 1 root root       696 Nov 17 19:45 ./
drwxr-xr-x 1 root root       130 Nov  3 11:01 ../
drwxr-xr-x 1 root root       418 Nov 17 20:33 aacraid-1.2.1.59002/
drwxr-xr-x 1 root root       634 Nov 17 15:06 linux-5.4.0/
-rw-r--r-- 1 root root   5474703 Nov 10 23:22 linux_5.4.0-54.60.diff.gz
-rw-r--r-- 1 root root      7220 Nov 10 23:22 linux_5.4.0-54.60.dsc
-rw-r--r-- 1 root root 170244619 Dec 11  2019 linux_5.4.0.orig.tar.gz
drwxr-xr-x 1 root root       272 Nov 12 04:10 linux-headers-5.4.0-53/
drwxr-xr-x 1 root root       394 Nov 12 04:11 linux-headers-5.4.0-53-generic/
drwxr-xr-x 1 root root       272 Nov 16 16:08 linux-headers-5.4.0-54/
-rw-r--r-- 1 root root  11273416 Nov 17 14:00 linux-headers-5.4.0-54_5.4.0-54.60_all.deb
drwxr-xr-x 1 root root       394 Nov 16 16:09 linux-headers-5.4.0-54-generic/
drwxr-xr-x 1 root root       136 Nov  5 17:14 linux-signed-5.4.0/
-rw-r--r-- 1 root root      2179 Nov 10 23:22 linux-signed_5.4.0-54.60.dsc
-rw-r--r-- 1 root root     18716 Nov 10 23:22 linux-signed_5.4.0-54.60.tar.xz
lrwxrwxrwx 1 root root        45 Nov  5 17:03 linux-source-5.4.0.tar.bz2 -> linux-source-5.4.0/linux-source-5.4.0.tar.bz2


```

Thank you
David

---

### Post by norobro on 2020-11-18
Okay, let's try starting over:```
cd /usr/src
rm -rf linux-5.4.0
dpkg-source -x linux_5.4.0-54.60.dsc
cp /boot/config-5.4.0-54-generic /usr/src/linux-5.4.0/.config
cd /usr/src/linux-5.4.0
#apply your patch here.
LANG=C fakeroot debian/rules binary-headers binary-generic binary-perarch
```The dpkg-source (man dpkg-source) command will extract the original 5.4.0 kernel source and apply the patches in the diff file.

Hope this helps.

---

### Post by David_Partridge on 2020-11-22
I did exactly as you proposed here's the result (tl;dr - didn't work):

```
root@charon:/usr/src/linux-5.4.0# patch -l -p1 < /home/amonra/0001-USB-UAS-introduce-a-quirk-to-set-no_write_same.patch 
patching file drivers/usb/storage/uas.c
Hunk #1 succeeded at 857 (offset -17 lines).
patching file drivers/usb/storage/usb.c
patching file include/linux/usb_usual.h
root@charon:/usr/src/linux-5.4.0# LANG=C fakeroot debian/rules binary-headers binary-generic binary-perarch
Debug: prepare-indep
dh_prep -i
Debug: install-headers
dh_testdir
dh_testroot
install -d /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54
find . -path './debian' -prune -o -path './debian.master' -prune \
  -o -path './include/*' -prune \
  -o -path './scripts/*' -prune -o -type f \
  \( -name 'Makefile*' -o -name 'Kconfig*' -o -name 'Kbuild*' -o \
     -name '*.sh' -o -name '*.pl' -o -name '*.lds' \) \
  -print | cpio -pd --preserve-modification-time /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54
18832 blocks
cp -a scripts include /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54
(find arch -name include -type d -print | \
    xargs -n1 -i: find : -type f) | \
    cpio -pd --preserve-modification-time /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/alpha/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/alpha/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/arc/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/arc/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/arm/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/arm/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/arm64/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/arm64/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/c6x/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/c6x/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/csky/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/csky/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/h8300/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/h8300/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/hexagon/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/hexagon/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/ia64/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/ia64/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/m68k/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/m68k/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/microblaze/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/microblaze/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/mips/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/mips/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/nds32/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/nds32/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/nios2/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/nios2/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/openrisc/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/openrisc/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/parisc/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/parisc/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/powerpc/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/powerpc/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/riscv/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/riscv/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/s390/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/s390/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/sh/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/sh/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/sparc/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/sparc/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/um/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/unicore32/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/unicore32/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/x86/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/x86/include/uapi/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/xtensa/include/asm/Kbuild not created: newer or same age version exists
cpio: /usr/src/linux-5.4.0/debian/linux-headers-5.4.0-54/usr/src/linux-headers-5.4.0-54/arch/xtensa/include/uapi/asm/Kbuild not created: newer or same age version exists
29749 blocks
Debug: binary-headers
dh_installchangelogs -plinux-headers-5.4.0-54
dh_installdocs -plinux-headers-5.4.0-54
dh_compress -plinux-headers-5.4.0-54
dh_fixperms -plinux-headers-5.4.0-54
dh_installdeb -plinux-headers-5.4.0-54
flock -w 60 /usr/src/linux-5.4.0/debian/.LOCK dh_gencontrol -plinux-headers-5.4.0-54
dh_md5sums -plinux-headers-5.4.0-54
dh_builddeb -plinux-headers-5.4.0-54
dpkg-deb: building package 'linux-headers-5.4.0-54' in '../linux-headers-5.4.0-54_5.4.0-54.60_all.deb'.
cc -o debian/scripts/fix-filenames debian/scripts/fix-filenames.c
Debug: /usr/src/linux-5.4.0/debian/stamps/stamp-prepare-tree-generic
install -d /usr/src/linux-5.4.0/debian/build/build-generic
touch /usr/src/linux-5.4.0/debian/build/build-generic/ubuntu-build
[ "false" != 'true' ] && true || \
    rsync -a --exclude debian --exclude debian.master --exclude debian.master * /usr/src/linux-5.4.0/debian/build/build-generic
cat /usr/src/linux-5.4.0/debian.master/config/config.common.ubuntu /usr/src/linux-5.4.0/debian.master/config/amd64/config.common.amd64 /usr/src/linux-5.4.0/debian.master/config/amd64/config.flavour.generic | sed -e 's/.*CONFIG_VERSION_SIGNATURE.*/CONFIG_VERSION_SIGNATURE="Ubuntu 5.4.0-54.60-generic 5.4.65"/' > /usr/src/linux-5.4.0/debian/build/build-generic/.config
find /usr/src/linux-5.4.0/debian/build/build-generic -name "*.ko" | xargs rm -f
make ARCH=x86 CROSS_COMPILE= KERNELVERSION=5.4.0-54-generic CONFIG_DEBUG_SECTION_MISMATCH=y KBUILD_BUILD_VERSION="60" LOCALVERSION= localver-extra= CFLAGS_MODULE="-DPKG_ABI=54" O=/usr/src/linux-5.4.0/debian/build/build-generic -j1 syncconfig prepare scripts
make[1]: Entering directory '/usr/src/linux-5.4.0'
make[2]: Entering directory '/usr/src/linux-5.4.0/debian/build/build-generic'
***
*** The source tree is not clean, please run 'make ARCH=x86 mrproper'
*** in /usr/src/linux-5.4.0
***
make[3]: *** [/usr/src/linux-5.4.0/Makefile:562: outputmakefile] Error 1
make[2]: *** [/usr/src/linux-5.4.0/Makefile:340: __build_one_by_one] Error 2
make[2]: Leaving directory '/usr/src/linux-5.4.0/debian/build/build-generic'
make[1]: *** [Makefile:179: sub-make] Error 2
make[1]: Leaving directory '/usr/src/linux-5.4.0'
make: *** [debian/rules.d/2-binary-arch.mk:34: /usr/src/linux-5.4.0/debian/stamps/stamp-prepare-tree-generic] Error 2
root@charon:/usr/src/linux-5.4.0# 



```

---

### Post by David_Partridge on 2020-12-01
Anyone ???

---

### Post by jeremy31 on 2020-12-01
Download the attached file, right click, extract here.  Then copy it to /lib/modules/5.4.0-54-generic/kernel/drivers/usb/storage/ and reboot into 5.4.0-54 with Secure boot disabled in BIOS, see if it works.
I am not sure why you had issues as I don't try to build entire kernels just to patch one module

---

### Post by David_Partridge on 2020-12-02
Hi again,

Many thanks for the file.

It appears that I need uas.ko (and if you could build for 5.4.0-56 (instead of 54) that would make my life a bit simpler).

Thanks again

David

---

### Post by jeremy31 on 2020-12-02
Try this one, both usb-storage and uas are there built on 5.4.0-56
[https://www.dropbox.com/s/7bmvip0pbinq5vt/storage.tar.gz?dl=0](https://www.dropbox.com/s/7bmvip0pbinq5vt/storage.tar.gz?dl=0)

---

### Post by David_Partridge on 2020-12-09
Thank you very much for the help!  I've now been able to test the patch and it's on its way to the stable tree...

---

