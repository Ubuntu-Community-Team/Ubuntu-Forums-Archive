---
title: "permissions change in root hard drive"
date: 2008-01-14
forum: General Help
---

### Post by ninicoco on 2008-01-14
I made a big mistake, i change the permissions in the root hard drive. i did this in the terminal #chmod 644 /

So now ubuntu doesn't start anymore and i can not have access with the cd.

Any one know how to fix that or i have to re-install everything?

---

### Post by erpo on 2008-01-14
> i can not have access with the cd.

What the heck does that mean? You can not "have" access "with" the cd?

You removed execute permissions from the root directory. The execute permission for a directory controls whether or not you (or a program) can list the contents of the directory. You need to
```
# chmod 755 /
```

---

### Post by ninicoco on 2008-01-14
I mean i can't see or access to the hard drive with the ubuntu cd, it's like i have no hard drive. 

> **erpo said:**
> You removed execute permissions from the root directory. The execute permission for a directory controls whether or not you (or a program) can list the contents of the directory. You need to
```
# chmod 755 /
``` How can do that? Ubuntu doesn't start on the hard drive (access denied) so i have to use ubuntu cd.
 If i do ```
# chmod 755 /
``` that gonna change the root cd not the hard drive. how can i change that on the hard drive please?

---

### Post by rodo-&gt;dave on 2008-01-14
Here is a ls -al of my root:

```

~$ ls -al /
total 84
drwxr-xr-x  21 root root  4096 2007-12-22 16:49 .
drwxr-xr-x  21 root root  4096 2007-12-22 16:49 ..
drwxr-xr-x   2 root root  4096 2007-12-22 16:05 bin
drwxr-xr-x   3 root root  4096 2007-12-19 13:56 boot
lrwxrwxrwx   1 root root    11 2007-12-04 17:51 cdrom -> media/cdrom
drwxr-xr-x  12 root root 13980 2008-01-14 06:35 dev
drwxr-xr-x 111 root root  4096 2008-01-14 06:36 etc
drwxr-xr-x   3 root root  4096 2007-12-04 18:03 home
drwxr-xr-x   2 root root  4096 2007-04-15 06:48 initrd
lrwxrwxrwx   1 root root    33 2007-12-04 18:48 initrd.img -> boot/initrd.img-2.6.20-16-generic
lrwxrwxrwx   1 root root    33 2007-12-04 18:06 initrd.img.old -> boot/initrd.img-2.6.20-15-generic
drwxr-xr-x  16 root root  4096 2007-12-10 07:10 lib
drwx------   2 root root 16384 2007-12-04 17:50 lost+found
drwxr-xr-x   3 root root  4096 2008-01-14 06:35 media
drwxr-xr-x   2 root root  4096 2007-04-12 04:11 mnt
drwxr-xr-x   2 root root  4096 2007-04-15 06:48 opt
dr-xr-xr-x 129 root root     0 2008-01-14 06:34 proc
drwxr-xr-x   8 root root  4096 2007-12-19 13:33 root
drwxr-xr-x   2 root root  4096 2007-12-10 07:10 sbin
drwxr-xr-x   2 root root  4096 2007-04-15 06:48 srv
drwxr-xr-x  11 root root     0 2008-01-14 06:34 sys
drwxrwxrwt  10 root root  4096 2008-01-14 06:42 tmp
drwxr-xr-x  13 root root  4096 2007-12-22 16:07 usr
drwxr-xr-x  15 root root  4096 2007-04-15 07:01 var
lrwxrwxrwx   1 root root    30 2007-12-04 18:48 vmlinuz -> boot/vmlinuz-2.6.20-16-generic
lrwxrwxrwx   1 root root    30 2007-12-04 18:06 vmlinuz.old -> boot/vmlinuz-2.6.20-15-generic
~$ 

```

good luck

---

### Post by p_quarles on 2008-01-14
You'll need to choose the "System Rescue Mode" option on the installation cd. This will bring up a root shell on the partition of your choice (and, obviously, you want to choose root). This will allow you to modify the permissions settings in the filesystem.

Please note, however, that this will be a complicated operation, and there's no guarantee that any kind of quick fix will bring the system back to life. The good thing is that you didn't run the chmod command recursively, so I'm guessing that if you can get the / directory to look like what robo->dave posted, you'll be able to recover the system.

---

