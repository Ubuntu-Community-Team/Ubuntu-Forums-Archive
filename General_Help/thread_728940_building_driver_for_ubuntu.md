---
title: "building driver for ubuntu"
date: 2008-03-19
forum: General Help
---

### Post by mgazb on 2008-03-19
Hi,
I am trying to build a driver for ubuntu 7.10 with 2.6.22.14 kernel. It has been built previously for a Fedora 7 system.

I have a problem where it is looking for asm/mach_apicdef.h and can't find it. It does exist in the source tree under asm-i386.

I have installed linux-source and build-essential. Are there some extra packages that I should have?

Also, I notice that linux-source installs in /usr/src. I can only compile it if I am root and in /usr/src/linux-source-2.6.22. Is this normal? I tried copying the whole tree to my home directory but it doesn't build.

thanks

dan

---

### Post by nick_h on 2008-03-19
> I can only compile it if I am root and in /usr/src/linux-source-2.6.22. Is this normal?
Yes, but you should also be able to copy it to your home directory and build it from there without being root.  You will need root permissions to install it though.

What driver are you building?

The [Master Kernel Thread](http://ubuntuforums.org/showthread.php?t=311158) may be helpful.

---

### Post by mgazb on 2008-03-25
Thanks Nick,
I've looked at the Master Kernel Thread. It builds in /usr/src using make-kpkg. According to most of the books, it's a bad idea to build in /usr/src. 

What does make-kpkg do? I've read the manpage, but I ought to be able to build it as me and then install it as root.

thanks

dan

---

### Post by mgazb on 2008-03-25
I've managed to build two kernels (2.6.22.9 and 2.6.24) as myself and then installed.

```

make
sudo make install

```

I've edited /boot/grub/menu.lst to add these new builds but when I try to reboot, I get

```

Error15: File not found

```

Which file can't be found?
How can  correct this?

thanks

dan

---

### Post by nick_h on 2008-03-25
> What does make-kpkg do? I've read the manpage, but I ought to be able to build it as me and then install it as root.
make-kpkg builds a kernel and makes packages for you to install through the apt package mechanism.

You can build it as you, only the installation requires root privilege.  You can also build it under your home directory instead of in /usr/src.

There is also no reason why you can't build a kernel manually.  Ubuntu kernels are built to load with an initrd file though so you will have to build one as part of the installation process.  Have a look at the manual page for the update-initramfs command.  One of the examples creates a new initrd file.

---

### Post by mgazb on 2008-03-27
Thanks Nick,
I did manage to get it working.
First I got
```

root@io:/boot# update-initramfs -c -k 2.6.22.9
update-initramfs: Generating /boot/initrd.img-2.6.22.9
Cannot find /lib/modules/2.6.22.9
update-initramfs: failed for /boot/initrd.img-2.6.22.9

```

I found out by digging through the Makefile that I needed to use 
```

make modules_install

```

I still get a lot of warnings:
```

root@io:/usr/src/linux-source-2.6.22# update-initramfs -c -k 2.6.22.9
update-initramfs: Generating /boot/initrd.img-2.6.22.9
find: /lib/firmware/2.6.22.9: No such file or directory
find: /lib/firmware/2.6.22.9: No such file or directory
find: /lib/firmware/2.6.22.9: No such file or directory
find: /lib/firmware/2.6.22.9: No such file or directory
find: /lib/firmware/2.6.22.9: No such file or directory
find: /lib/firmware/2.6.22.9: No such file or directory

```

I notice that the file sizes of the newly generated initrd files (2.6.22.9, 2.6.24) is a lot bigger than the pre-existing ones. Is this due to the missing firmware support?

```

 dwhs1@io:~$ ls -l /boot
total 109848
-rw-r--r-- 1 root root   424317 2008-02-12 10:39 abi-2.6.22-14-generic
lrwxrwxrwx 1 root root       15 2008-03-27 09:52 config -> config-2.6.22.9
-rw-r--r-- 1 root root    75311 2008-02-12 10:39 config-2.6.22-14-generic
-rw-r--r-- 1 root root    81875 2008-03-27 09:52 config-2.6.22.9
-rw-r--r-- 1 root root    81875 2008-03-19 13:52 config-2.6.22.9.old
-rw-r--r-- 1 root root    86502 2008-03-25 15:50 config-2.6.24
lrwxrwxrwx 1 root root       13 2008-03-25 15:50 config.old -> config-2.6.24
drwxr-xr-x 2 root root     4096 2008-03-25 15:55 grub
-rw-r--r-- 1 root root  7232810 2008-03-18 13:14 initrd.img-2.6.22-14-generic
-rw-r--r-- 1 root root  7520548 2008-03-18 10:39 initrd.img-2.6.22-14-generic.bak
-rw-r--r-- 1 root root 44016406 2008-03-27 09:58 initrd.img-2.6.22.9
-rw-r--r-- 1 root root 42217221 2008-03-27 09:45 initrd.img-2.6.24
-rw-r--r-- 1 root root   103204 2007-09-28 11:06 memtest86+.bin
lrwxrwxrwx 1 root root       19 2008-03-27 09:52 System.map -> System.map-2.6.22.9
-rw-r--r-- 1 root root   823535 2008-02-12 10:39 System.map-2.6.22-14-generic
-rw-r--r-- 1 root root   823535 2008-03-27 09:52 System.map-2.6.22.9
-rw-r--r-- 1 root root   823535 2008-03-19 13:52 System.map-2.6.22.9.old
-rw-r--r-- 1 root root   862919 2008-03-25 15:50 System.map-2.6.24
lrwxrwxrwx 1 root root       17 2008-03-25 15:50 System.map.old -> System.map-2.6.24
lrwxrwxrwx 1 root root       16 2008-03-27 09:52 vmlinuz -> vmlinuz-2.6.22.9
-rw-r--r-- 1 root root  1764536 2008-02-12 10:39 vmlinuz-2.6.22-14-generic
-rw-r--r-- 1 root root  1763032 2008-03-27 09:52 vmlinuz-2.6.22.9
-rw-r--r-- 1 root root  1763032 2008-03-19 13:52 vmlinuz-2.6.22.9.old
-rw-r--r-- 1 root root  1796352 2008-03-25 15:50 vmlinuz-2.6.24
lrwxrwxrwx 1 root root       14 2008-03-25 15:50 vmlinuz.old -> vmlinuz-2.6.24

```


Also when I boot the new kernel, it goes through the maintenance mode (type root password or Ctrl-D to continue.

thanks

dan

---

### Post by nick_h on 2008-03-27
There is a good online book called [Linux Kernel in a Nutshell](http://www.kroah.com/lkn/) by Greg Kroah-Hartman that is worth reading.
 
The warnings about the firmware directory are expected.  You could copy them over from another kernel version.

The big initrd files are caused by the fact that the Ubuntu kernel enables debugging symbols in the default configuration.  I think it strips them out later with the *strip* command.

---

