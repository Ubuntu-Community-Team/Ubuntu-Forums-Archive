---
title: "Grub error 15 (after usplash-switcher)"
date: 2008-02-03
forum: General Help
---

### Post by sunzaru on 2008-02-03
grrrr.. changing the boot screen from kubuntu to ubuntu seems like more of a pain that i thought it would be.

quick background, i'm now to ubuntu.. fairly new to linux. I started w/ ubuntu and installed the kde desktop.  it changed my boot/shutdown screens to Kubuntu.  I went to change it back.. only got the shutdown image to change.  did some more looking around and found usplash-switcher.  This apeared to allow me to change the boot screen also.  however... when i rebooted i got 

"Error 15: file not found" 

"press any key"  (forget exact wording here)

however... i was using ubuntu for the last week or so, not like it was a change to the HDDs or partitions.

menu.lst shows
```

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=53c1498d-7f71-4dc8-b9c8-47872b542dbb ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=53c1498d-7f71-4dc8-b9c8-47872b542dbb ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=53c1498d-7f71-4dc8-b9c8-47872b542dbb ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=53c1498d-7f71-4dc8-b9c8-47872b542dbb ro single
initrd		/boot/initrd.img-2.6.20-15-generic

```

the Ubuntu, kernal 2.6.20-16-generic (both versions) give the same error.  I'm in right now on the ubuntu, kernal 2.6.20-15-generic.  

I present two problems (that i can see)

[LIST=1]
[*]How do i fix grub to allow me to use the updated kernal that i was using for the last 3-4 days.
[*]How do i change the boot screen back to ubuntu? (kernal 2.6.20-15-generic shows ubuntu boot splash)
[/LIST]

---

### Post by sunzaru on 2008-02-03
addendum:

```

ls -la /boot
-rwxr-xr-x  1 root root 6939720 2008-01-25 23:16 initrd.img-2.6.20-15-generic
-rwxr-xr-x  1 root root 6946262 2008-01-25 23:15 initrd.img-2.6.20-15-generic.bak
-rw-r--r--  1 root root 6939397 2008-01-25 23:16 initrd.img-2.6.20-16-generic.bak
-rw-r--r--  1 root root 6938467 2008-01-27 06:39 initrd.img-2.6.20-16-generic.dpkg-bak

```

don't know if this will be helpfull but... it looks like the system made a backup of itself prior to a change on 2008-1-25

---

### Post by zvacet on 2008-02-03
It is not 

/boot/initrd.img-2.6.20-16-generic

but 

**/boot/intrid.img**-2.6.20-16-generic

---

### Post by sunzaru on 2008-02-03
err... i'm not following you here.  are you saying that my files are named wrong?

i'm confused because the files are listed as above but i CAN get into ubuntu using the 2.6.20-15-generic  just not the 2.6.20-16

```

ls -la /boot
drwxr-xr-x  4 root root    4096 2008-02-02 14:40 .
drwxr-xr-x 23 root root    4096 2008-02-02 17:24 ..
-rwxr-xr-x  1 root root  414210 2008-01-25 23:15 abi-2.6.20-15-generic
-rwxr-xr-x  1 root root  414274 2008-01-25 23:15 abi-2.6.20-16-generic
-rwxr-xr-x  1 root root   83234 2008-01-25 23:15 config-2.6.20-15-generic
-rwxr-xr-x  1 root root   83217 2008-01-25 23:15 config-2.6.20-16-generic
drwxr-xr-x  2 root root    4096 2008-01-25 23:24 grub
-rwxr-xr-x  1 root root 7936165 2008-01-25 23:15 initrd
-rwxr-xr-x  1 root root 6939720 2008-01-25 23:16 initrd.img-2.6.20-15-generic
-rwxr-xr-x  1 root root 6946262 2008-01-25 23:15 initrd.img-2.6.20-15-generic.bak
-rw-r--r--  1 root root 6939397 2008-01-25 23:16 initrd.img-2.6.20-16-generic.bak
-rw-r--r--  1 root root 6938467 2008-01-27 06:39 initrd.img-2.6.20-16-generic.dpkg-bak
-rwxr-xr-x  1 root root 1745100 2008-01-25 23:15 linux
-rwxr-xr-x  1 root root   94600 2008-01-25 23:15 memtest86+.bin
-rwxr-xr-x  1 root root  806942 2008-01-25 23:15 System.map-2.6.20-15-generic
-rwxr-xr-x  1 root root  807071 2008-01-25 23:15 System.map-2.6.20-16-generic
-rwxr-xr-x  1 root root 1745100 2008-01-25 23:15 vmlinuz-2.6.20-15-generic
-rwxr-xr-x  1 root root 1747372 2008-01-25 23:15 vmlinuz-2.6.20-16-generic
drwxr-xr-x  2 root root    4096 2008-01-25 23:15 winboot

```

---

### Post by sunzaru on 2008-02-03
I ran System-Administration-> Startup Manager

Then restored back to ubuntu default.. all is well now.  bad theme image... maybe.. who knows.. anwyay.. it's fixed ;)

---

