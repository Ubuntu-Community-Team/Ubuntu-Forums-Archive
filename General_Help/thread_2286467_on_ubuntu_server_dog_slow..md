---
title: "/ on ubuntu server dog slow."
date: 2015-07-12
forum: General Help
---

### Post by ed-driesen on 2015-07-12
So here's the deal. I have a server at home set up with two 2TB WD greens (raid1).
Whenever I do a 'ls  /', 'cd /va<hits tab>'  the ssh session becomes unresponsive, and htop & iotop show 99% usage of disc and/or cpu usage. It's slowing my system waaaaay down.
I hate a booboo a while ago with thousands of files occupying the root folder (bad script dumped files in root), but I fixed that.

What I've tried so far;

[LIST]
[*]/forcefsck and rebooting
[*]e2fsck -D via live CD
[*]e4defrag
[*]wdidle3 tools (disabling parking)
[*]checking partitions (they start at 2048)
[/LIST]

If anyone could point me toward a solution , I would be sooooo hapy!

---

### Post by dino99 on 2015-07-12
i does not know how it is with 2TB raid1, but that should mean a lot of files to sort & list i suppose
disk-manager & htop might help you know the free space on / & the partitions, the used swap, ...

and your logs are also a good place to glance at

---

### Post by ed-driesen on 2015-07-12
Yeah, been down that alley.... 
Next thing to try is to cleart some space (92% full)

I've bought one of [these]("http://www.conrad.be/ce/nl/product/417037/HD3402JSC-35-inch-SATA-HDD-behuizing-USB-30-eSATA?ref=searchDetail"), and stitched some old drives together via lvm to put my non-essentials on it (movies etc...). Moving as we speak....

---

### Post by collisionystm on 2015-07-12
Is this a software raid? Have you checked the SMART status of the drives? You may have a failing disk.

---

### Post by ed-driesen on 2015-07-13
nope smart is sane....
Freeing space didn't do the trick

Could this be the problem ( / size and tmp size)
```

mutrax@homeserver:/$ ls -lah
totaal 225M
drwxr-xr-x  24 root   root      84M jul 13 20:45 .
drwxr-xr-x  24 root   root      84M jul 13 20:45 ..
drwxr-xr-x   2 root   root     4,0K jun 20 22:19 bin
drwxr-xr-x   4 root   root     4,0K jul 10 07:38 boot
drwxr-xr-x  19 root   root     4,4K jul 13 20:36 dev
drwxr-xr-x 179 root   root      12K jul 13 11:18 etc
drwxr-xr-x   7 root   root     4,0K jul 20  2014 home
lrwxrwxrwx   1 root   root       33 mei  4  2014 initrd.img -> boot/initrd.img-3.13.0-24-generic
lrwxrwxrwx   1 root   root       37 jul 19  2012 initrd.img.old -> /boot/initrd.img-3.2.0-23-generic-pae
drwxrwx---   4 mutrax libvirtd 4,0K apr  5 20:10 kvm
drwxr-xr-x  24 root   root     4,0K mrt 23 22:38 lib
lrwxrwxrwx   1 root   root       34 mei  4  2014 libnss3.so -> /usr/lib/i386-linux-gnu/libnss3.so
drwx------   2 root   root      16K jul 19  2012 lost+found
drwxr-xr-x   5 root   root     4,0K aug  5  2014 media
drwxr-xr-x   6 root   root     4,0K jun 20 22:02 mnt
-rw-------   1 root   root      119 jul 24  2014 nohup.out
drwxr-xr-x   7 root   root     4,0K jul 10 07:39 opt
dr-xr-xr-x 199 root   root        0 jul 11 10:15 proc
-rw-------   1 root   root     1,0K jul 19  2012 .rnd
drwx------  29 root   root     4,0K jul 10 18:16 root
drwxr-xr-x  31 root   root     1,2K jul 13 15:40 run
drwxr-xr-x   2 root   root      12K jun 20 22:17 sbin
drwxr-xr-x   3 root   root     4,0K jul 19  2012 srv
dr-xr-xr-x  13 root   root        0 jul 11 10:16 sys
drwxrwxrwt  11 root   root      56M jul 13 20:50 tmp
drwxr-xr-x   5 root   root     4,0K jul 13 10:40 twonky
drwxr-xr-x   5 root   root     4,0K mrt 24  2014 twonkymedia
drwxr-xr-x  10 root   root     4,0K feb 14 15:31 usr
drwxr-xr-x  17 root   root     4,0K mei  5  2014 var
lrwxrwxrwx   1 root   root       30 mei  4  2014 vmlinuz -> boot/vmlinuz-3.13.0-24-generic
lrwxrwxrwx   1 root   root       33 jul 19  2012 vmlinuz.old -> boot/vmlinuz-3.2.0-23-generic-pae
```

Ok, 
Owncloud dumps session files in tmp, added a daily cronjob 

```
find /tmp/sess* -mtime +5 -exec rm {} \; 
```

So that won't grow to idiot proportions so you can't rm them because of ```
Argument list too long
``` (deleted first with ```
find . -name "sess*" -print0 | xargs -0 rm
```

---

