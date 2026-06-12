---
title: "No such file or directory"
date: 2013-08-23
forum: General Help
---

### Post by hoodieatpst on 2013-08-23
```

bogdan@bogdan:~$ cd /usr/bin
bogdan@bogdan:/usr/bin$ ls -l ./net
net              netkit-ftp       net.samba3       netselect        net-snmp-config
bogdan@bogdan:/usr/bin$ ls -l ./netselect
-rwxr-xr-x 1 root root 15256 &#1075;&#1088;&#1091; 16  2011 ./netselect
bogdan@bogdan:/usr/bin$
bogdan@bogdan:/usr/bin$ ldd ./netselect
        linux-vdso.so.1 =>  (0x00007fff86da9000)
        libc.so.6 => /lib/x86_64-linux-gnu/libc.so.6 (0x00007fa33a965000)
        /lib/ld-linux-x86-64.so.2 => /lib64/ld-linux-x86-64.so.2 (0x00007fa33ad4c000)
bogdan@bogdan:/usr/bin$ ./netselect
bash: ./netselect: No such file or directory

```

But file is there. This is binary file, not script.

---

### Post by sanderj on 2013-08-23
Bogdan, how did you install netselect?

What is the output of:

```
uname -a
lsb_release -a
ll /lib64/ld-linux-x86-64.so.2

```

Post the output here

FYI:

```
sander@R540:~/oud-Downloads/netselect$ ll netselect
-rwsrwxr-x 1 root sander 61057 Aug 23 16:53 netselect*
sander@R540:~/oud-Downloads/netselect$ ./netselect
Usage: netselect [-v] [-vv] [-t min_tries] [-m max_ttl] host [host...]
sander@R540:~/oud-Downloads/netselect$
```

So it works on my system.

---

