---
title: "&quot;you do not have sufficient privileges&quot;"
date: 2007-11-08
forum: General Help
---

### Post by Majin Zero on 2007-11-08
I unchecked "save this session" And now when I start up my machine, after logging in, I get "you do not have sufficient privileges" And my panel doesn't open.

All I get are my desktop and desktop icons.

What happened, and how can I fix it?

Many thanks in advance.

---

### Post by taurus on 2007-11-08
Could be permissions problem with your account.  Open a terminal, Applications -> Accessories -> Terminal, and post the outputs of these commands here.

```
id
ls -la ~  [COLOR="Blue"]<-- Don't include files/directories that you don't want the world to see.[/COLOR]
```

---

### Post by Majin Zero on 2007-11-09
wow, my memory is horrible; it actually says:

This configuration could not be loaded

You are not allowed to access the system configuration

Anyhow; here's the info you asked for:

> ferris@Lappy:/$ id
uid=1000(ferris) gid=1000(ferris) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),104(scanner),112(netdev),113(lpadmin),115(powerdev),117(admin),1000(ferris)
ferris@Lappy:/$ ls -la
total 88
drwxr-xr-x  21 root root  4096 2007-07-12 00:16 .
drwxr-xr-x  21 root root  4096 2007-07-12 00:16 ..
drwxr-xr-x   2 root root  4096 2007-11-01 17:41 bin
drwxr-xr-x   3 root root  4096 2007-11-01 17:53 boot
lrwxrwxrwx   1 root root    11 2007-07-10 15:50 cdrom -> media/cdrom
drwxr-xr-x  12 root root 13520 2007-11-09 12:11 dev
drwxr-xr-x 107 root root  4096 2007-11-09 12:11 etc
drwxr-xr-x   3 root root  4096 2007-07-10 16:58 home
drwxr-xr-x   2 root root  4096 2007-07-10 15:54 initrd
lrwxrwxrwx   1 root root    33 2007-07-12 00:16 initrd.img -> boot/initrd.img-2.6.20-16-generic
lrwxrwxrwx   1 root root    33 2007-07-10 16:05 initrd.img.old -> boot/initrd.img-2.6.20-15-generic
drwxr-xr-x  16 root root  4096 2007-09-21 18:50 lib
drwx------   2 root root 16384 2007-07-10 15:49 lost+found
drwxr-xr-x   4 root root  4096 2007-11-09 12:11 media
drwxr-xr-x   2 root root  4096 2007-04-12 05:11 mnt
drwxr-xr-x   2 root root  4096 2007-07-10 15:54 opt
dr-xr-xr-x  96 root root     0 2007-11-09 12:10 proc
-rw-------   1 root root  1024 2007-07-10 16:36 .rnd
drwxr-xr-x  15 root root  4096 2007-11-09 11:54 root
drwxr-xr-x   2 root root  4096 2007-11-01 17:41 sbin
drwxr-xr-x   2 root root  4096 2007-07-10 15:54 srv
drwxr-xr-x  11 root root     0 2007-11-09 12:10 sys
drwxrwxrwt   8 root root  4096 2007-11-09 12:12 tmp
drwxr-xr-x  12 root root  4096 2007-09-21 18:13 usr
drwxr-xr-x  14 root root  4096 2007-07-10 17:01 var
lrwxrwxrwx   1 root root    30 2007-07-12 00:16 vmlinuz -> boot/vmlinuz-2.6.20-16-generic
lrwxrwxrwx   1 root root    30 2007-07-10 16:05 vmlinuz.old -> boot/vmlinuz-2.6.20-15-generic


---

