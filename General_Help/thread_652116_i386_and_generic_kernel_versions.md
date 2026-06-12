---
title: "i386 and generic kernel versions"
date: 2007-12-28
forum: General Help
---

### Post by DugieHowsa on 2007-12-28
In an attempt to fix the missing audio problem I was having with my nvidia sound card, I somehow switched the type of kernel I was using from generic to i386.  I now have everything running fine with the generic version of the kernel, but when ever kernel updates are pushed out, my system gets switched back to i386 after reboot and I need to manually switch back to generic.

Any thoughts as to how I can get this to stop happening?

---

### Post by DugieHowsa on 2007-12-28
To clarify further, this is the guide I was using when the trouble began:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by DugieHowsa on 2008-01-03
I believe I have solved my problem.  It appears there were some bad links in my root directory:
```

user@Gutsy:/$ ls -la
total 104
drwxr-xr-x  21 root root  4096 2007-10-21 11:01 .
drwxr-xr-x  21 root root  4096 2007-10-21 11:01 ..
drwxr-xr-x   2 root root  4096 2007-10-20 07:54 bin
drwxr-xr-x   3 root root  4096 2007-12-20 20:57 boot
lrwxrwxrwx   1 root root    11 2007-06-14 16:52 cdrom -> media/cdrom
-rwxr-xr-x   1 root root     4 2005-03-27 00:38 debian-binary
drwxr-xr-x  12 root root 13720 2008-01-03 12:58 dev
drwxr-xr-x 134 root root 12288 2008-01-03 12:58 etc
drwxr-xr-x   6 root root  4096 2007-06-23 16:50 home
drwxr-xr-x   2 root root  4096 2007-04-15 07:48 initrd
lrwxrwxrwx   1 root root    29 2007-10-21 11:01 initrd.img -> boot/initrd.img-2.6.22-14-386
lrwxrwxrwx   1 root root    33 2007-10-20 08:10 initrd.img.old -> boot/initrd.img-2.6.22-14-generic
drwxr-xr-x  17 root root 12288 2007-12-18 20:37 lib
drwx------   2 root root 16384 2007-06-14 16:51 lost+found
drwxr-xr-x   5 root root  4096 2008-01-03 12:58 media
drwxr-xr-x   2 root root  4096 2007-04-12 05:11 mnt
drwxr-xr-x   6 root root  4096 2007-12-07 12:20 opt
dr-xr-xr-x 168 root root     0 2008-01-03 07:58 proc
drwxr-xr-x  14 root root  4096 2008-01-03 13:08 root
drwxr-xr-x   2 root root  4096 2007-12-18 20:37 sbin
drwxr-xr-x   2 root root  4096 2007-04-15 07:48 srv
drwxr-xr-x  12 root root     0 2008-01-03 07:58 sys
drwxrwxrwt  14 root root  4096 2008-01-03 13:08 tmp
drwxr-xr-x  13 root root  4096 2007-10-21 11:58 usr
drwxr-xr-x  15 root root  4096 2007-10-20 00:10 var
lrwxrwxrwx   1 root root    26 2007-10-21 11:01 vmlinuz -> boot/vmlinuz-2.6.22-14-386
lrwxrwxrwx   1 root root    30 2007-10-20 08:10 vmlinuz.old -> boot/vmlinuz-2.6.22-14-generic

```

the initrd.img and vmlinuz symbolic links were pointing to the i386 files, and these files no longer existed.  I deleted the broken symbolic links and replaced them with the .old versions.  

I also found a link in the /usr/src directory that pointed to the 386 source:

user@Gutsy:/usr/src$ ls -la
total 4636
drwxrwsr-x  7 root src     4096 2007-10-21 11:57 .
drwxr-xr-x 13 root root    4096 2007-10-21 11:58 ..
lrwxrwxrwx  1 root src       27 2007-10-21 11:57 linux -> linux-headers-2.6.22-14-386
drwxr-xr-x 19 root root    4096 2007-12-19 18:15 linux-headers-2.6.22-14
drwxr-xr-x  5 root root    4096 2007-12-19 18:15 linux-headers-2.6.22-14-386
drwxr-xr-x  5 root root    4096 2007-12-19 18:15 linux-headers-2.6.22-14-generic
drwxr-xr-x  3 root src     4096 2007-10-21 11:57 modules
-rw-r--r--  1 root src  2443208 2007-10-21 11:57 nvidia-kernel-2.6.22-14-386_100.14.19-0ubuntu3+2.6.22-14.46_i386.deb
-rw-r--r--  1 root root 2261622 2007-10-21 11:57 nvidia-new-kernel-source.tar.gz
drwxr-xr-x  7 root root    4096 2007-10-21 11:56 rpm

I removed the current link for the linux directory and created a new one that pointed to the generic source directory.  I am beginning to think this happened when I tried to install the nvidia drivers to enable compiz, as it appears I downloaded the wrong debian package.

Anyways, I should know if this worked after the next kernel upgrade is downloaded and installed.  For now, my fingers are crossed.

---

### Post by DugieHowsa on 2008-02-16
Well, it appears that the problem still exists.  The Update Manager is trying to download and install both 386 and generic versions of the linux-headers and linux-image files.  When this happens, its going to reconfigure by grub settings.  I can easily go back after the next reboot and modify the grub settings, but I would like to know how to keep this from happening.

Any thoughts?

---

### Post by DugieHowsa on 2008-02-16
Upon further research, I found that both of these packages were selected in the4 Synaptic Package Manager.  Unfortunately, when I tried to mark the 386 packages for removal, it would seem that they were tied to the generic packages, and I could not get rid of one with out the other.

Is there a way to break this dependancy so that I can uninstall the 386 packages and keep the generic packages?

---

### Post by DugieHowsa on 2008-02-16
It appears this time I have solved the problem.  I used apt-get to list all the linux-header and linux-image files, and removed the ones I no longer needed.

---

