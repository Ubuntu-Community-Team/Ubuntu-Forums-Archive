---
title: "Oracle client setup"
date: 2008-06-01
forum: General Help
---

### Post by donkeyX on 2008-06-01
Hey Guys,

I have decided to take the leap and try to use my work pc as a ubuntu box. This will be a large task as we currently use 
 - oralce,
 - visual source safe
 - Peopletools App Designer and 
 - toad

Now i know that this is a large list of things but i am currently stuck on setting up the oracle client with sqlplus. I have installed the client packages and can run sqlplus but for some reason sqlplus does not see my tnsnames.ora file so i cannot connect to anything. I have created the env variable TNS_ADMIN and pointed it to the dir that holds the tnsnames.ora file.

Any help would be appreciated.

PS: will continue the other questions further on ;)

Cheers Dave

---

### Post by donkeyX on 2008-06-27
Ok, 

Considering all the help that i am getting on this topic so far, i will add some info myself: 

I have added and installed the required client files and it seems to be working because i can specify the full connection identifier and connect to the db. However, i am still having the problem that i cannot use the tnsnames.ora which is very annoying as we have many, many env's that we need to connect to. 

I have created the env variables for $ORACLE_HOME and $TNS_ADMIN but still no luck????


Cheers Dave

---

### Post by dmflad on 2008-08-03
See if this helps: [http://www.nextre.it/oracledocs/oracleonubuntu.html](http://www.nextre.it/oracledocs/oracleonubuntu.html)
or [http://www.pythian.com/blogs/968/installing-oracle-11g-on-ubuntu-804-lts-hardy-heron](http://www.pythian.com/blogs/968/installing-oracle-11g-on-ubuntu-804-lts-hardy-heron)

I'm just now trying to get Oracle 11g client on Ubuntu. My work env is WinXP PCs and RHEL servers running Oracle but I've been running Ubuntu on my work LT for awhile. I think I had Oracle XE on Ubuntu but lost everything when I moved to U 8.04. So now I'm doing stuff all over again.  I have PLSQL Developer running on LT but without Oracle Client I can't conn to all my work dbs.

---

### Post by dmflad on 2008-08-03
I had to set DISPLAY differently:
      **export DISPLAY=:0.0**
and to test it I did:
     ** xcalc**     #This should make the calculator show up on your screen

In Oracle Client Install windows I did:
• picked Administrator install
• Oracle Base : **/u01/oracle**
• Software Location : Name: **client11g** Path: **/u01/oracle/client11g**

Install appears to have gone okay but since I'm at home I don't have access to any work dbs - so next thing is to install 11gDB

---

### Post by davisond on 2008-10-07
using the ubuntu/debian packages, sqlplus looks in several places for the tnsnames config.  You can see what it's trying to do by running the program under strace and then grepping the output for "tns" for example.  Here's what I got:

```
davisond@davisond-laptop ~ $ strace sqlplus user/pass@MY_DB > strace.out 2>&1

davisond@davisond-laptop ~ $ grep tns strace.out 
access("/etc/tnsnav.ora", F_OK)         = -1 ENOENT (No such file or directory)
access("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/network/admin/tnsnav.ora", F_OK) = -1 ENOENT (No such file or directory)
access("/home/davisond/.tnsnames.ora", F_OK) = -1 ENOENT (No such file or directory)
access("/etc/tnsnames.ora", F_OK)       = -1 ENOENT (No such file or directory)
access("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/network/admin/tnsnames.ora", F_OK) = -1 ENOENT (No such file or directory)
```

So I just placed mine in /home/davisond/.tnsnames.ora and it works fine now.

Happy SQL'ing.

---

### Post by donkeyX on 2009-01-08
hey davidsond,

Thanks heaps for the reply you are the first person who has given me a glimor of hope that this can be solved.... Anyway, it looks like mine is not looking for tnsnames.ora at all??? how can i change this so it does look for it? Sorry about the large post but i have to get this solved soon or i will have to drop ubuntu as my work machine :(


```

execve("/usr/lib/oracle/oracle_client/bin/sqlplus", ["sqlplus", "user/pass@STUDD1"], [/* 42 vars */]) = 0
brk(0)                                  = 0x8633000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb8076000
readlink("/proc/self/exe", "/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/sqlplus", 4096) = 63
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686/sse2/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686/sse2/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686/sse2/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686/sse2", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/sse2/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/sse2/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/sse2/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/sse2", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686/sse2/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686/sse2/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686/sse2/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686/sse2", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/sse2/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/sse2/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/sse2/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/sse2", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libsqlplus.so", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0PH\1\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=726188, ...}) = 0
mmap2(NULL, 725448, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7fc4000
mmap2(0xb806d000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa9) = 0xb806d000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libclntsh.so.10.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\343"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=14273496, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fc3000
mmap2(NULL, 14356808, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7211000
mmap2(0xb7f4d000, 397312, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xd3c) = 0xb7f4d000
mmap2(0xb7fae000, 82248, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7fae000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libnnz10.so", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300:\6"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=2106868, ...}) = 0
mmap2(NULL, 2115380, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb700c000
mmap2(0xb71e9000, 159744, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1dc) = 0xb71e9000
mmap2(0xb7210000, 1844, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7210000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls/i686/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls/i686/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls/i686/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls/i686", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/i686/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/i686/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/i686/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/i686", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("tls/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/libdl.so.2", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("tls/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/sse2/libdl.so.2", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("tls/cmov/libdl.so.2", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("tls/libdl.so.2", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/sse2/libdl.so.2", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("i686/cmov/libdl.so.2", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("i686/libdl.so.2", O_RDONLY)       = -1 ENOENT (No such file or directory)
open("sse2/cmov/libdl.so.2", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("sse2/libdl.so.2", O_RDONLY)       = -1 ENOENT (No such file or directory)
open("cmov/libdl.so.2", O_RDONLY)       = -1 ENOENT (No such file or directory)
open("libdl.so.2", O_RDONLY)            = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=68409, ...}) = 0
mmap2(NULL, 68409, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6ffb000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \n\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9676, ...}) = 0
mmap2(NULL, 12408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6ff7000
mmap2(0xb6ff9000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb6ff9000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/cmov/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/cmov/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/libm.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("tls/sse2/cmov/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/sse2/libm.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("tls/cmov/libm.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("tls/libm.so.6", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("i686/sse2/cmov/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/sse2/libm.so.6", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("i686/cmov/libm.so.6", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("i686/libm.so.6", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("sse2/cmov/libm.so.6", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("sse2/libm.so.6", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("cmov/libm.so.6", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("libm.so.6", O_RDONLY)             = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@4\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=149332, ...}) = 0
mmap2(NULL, 151680, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6fd1000
mmap2(0xb6ff5000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x23) = 0xb6ff5000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/cmov/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/cmov/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/sse2/cmov/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/sse2/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/cmov/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/libpthread.so.0", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("i686/sse2/cmov/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/sse2/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/cmov/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/libpthread.so.0", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("sse2/cmov/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("sse2/libpthread.so.0", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("cmov/libpthread.so.0", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("libpthread.so.0", O_RDONLY)       = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000H\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=116457, ...}) = 0
mmap2(NULL, 98784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6fb8000
mmap2(0xb6fcd000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14) = 0xb6fcd000
mmap2(0xb6fcf000, 4576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6fcf000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/cmov/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/cmov/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/libnsl.so.1", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("tls/sse2/cmov/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/sse2/libnsl.so.1", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("tls/cmov/libnsl.so.1", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("tls/libnsl.so.1", O_RDONLY)       = -1 ENOENT (No such file or directory)
open("i686/sse2/cmov/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/sse2/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/cmov/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/libnsl.so.1", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("sse2/cmov/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("sse2/libnsl.so.1", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("cmov/libnsl.so.1", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("libnsl.so.1", O_RDONLY)           = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnsl.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\00001\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=87804, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6fb7000
mmap2(NULL, 100328, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6f9e000
mmap2(0xb6fb3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14) = 0xb6fb3000
mmap2(0xb6fb5000, 6120, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6fb5000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/cmov/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/cmov/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/libc.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("tls/sse2/cmov/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/sse2/libc.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("tls/cmov/libc.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("tls/libc.so.6", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("i686/sse2/cmov/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/sse2/libc.so.6", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("i686/cmov/libc.so.6", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("i686/libc.so.6", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("sse2/cmov/libc.so.6", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("sse2/libc.so.6", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("cmov/libc.so.6", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("libc.so.6", O_RDONLY)             = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340g\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1425800, ...}) = 0
mmap2(NULL, 1431152, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6e40000
mmap2(0xb6f98000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x158) = 0xb6f98000
mmap2(0xb6f9b000, 9840, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6f9b000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6e3f000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb6e3f8c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb6f98000, 8192, PROT_READ)   = 0
mprotect(0xb6fb3000, 4096, PROT_READ)   = 0
mprotect(0xb6fcd000, 4096, PROT_READ)   = 0
mprotect(0xb6ff5000, 4096, PROT_READ)   = 0
mprotect(0xb6ff9000, 4096, PROT_READ)   = 0
mprotect(0xb700c000, 1953792, PROT_READ|PROT_WRITE) = 0
mprotect(0xb700c000, 1953792, PROT_READ|PROT_EXEC) = 0
mprotect(0xb7211000, 13877248, PROT_READ|PROT_WRITE) = 0
mprotect(0xb7211000, 13877248, PROT_READ|PROT_EXEC) = 0
mprotect(0xb7fc4000, 692224, PROT_READ|PROT_WRITE) = 0
mprotect(0xb7fc4000, 692224, PROT_READ|PROT_EXEC) = 0
mprotect(0xb8093000, 4096, PROT_READ)   = 0
munmap(0xb6ffb000, 68409)               = 0
set_tid_address(0xb6e3f908)             = 12784
set_robust_list(0xb6e3f910, 0xc)        = 0
futex(0xbf893450, 0x81 /* FUTEX_??? */, 1) = 0
rt_sigaction(SIGRTMIN, {0xb6fbc2e0, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb6fbc720, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="donkeyhome", ...}) = 0
brk(0)                                  = 0x8633000
brk(0x8654000)                          = 0x8654000
mmap2(NULL, 143360, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6e1c000
futex(0xb6ffa06c, 0x81 /* FUTEX_??? */, 2147483647) = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libsqlplusic.so", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\\\7\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1432504, ...}) = 0
mmap2(NULL, 1435468, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6cbd000
mmap2(0xb6e1b000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15d) = 0xb6e1b000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libociei.so", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libocixe.so", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p&\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=44617172, ...}) = 0
mmap2(NULL, 44620148, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb422f000
mmap2(0xb6cbb000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2a8b) = 0xb6cbb000
close(3)                                = 0
mprotect(0xb422f000, 44613632, PROT_READ|PROT_WRITE) = 0
mprotect(0xb422f000, 44613632, PROT_READ|PROT_EXEC) = 0
mmap2(NULL, 155648, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb4209000
fcntl64(140850200, F_SETFD, FD_CLOEXEC) = -1 EBADF (Bad file descriptor)
fcntl64(140850736, F_SETFD, FD_CLOEXEC) = -1 EBADF (Bad file descriptor)
brk(0x8675000)                          = 0x8675000
fcntl64(140853208, F_SETFD, FD_CLOEXEC) = -1 EBADF (Bad file descriptor)
gettimeofday({1231474590, 615993}, NULL) = 0
open("/etc/localtime", O_RDONLY)        = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=413, ...}) = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=413, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb4208000
read(3, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\4\0\0\0\4\0\0"..., 4096) = 413
_llseek(3, -8, [405], SEEK_CUR)         = 0
read(3, "\nEST-10\n", 4096)             = 8
close(3)                                = 0
munmap(0xb4208000, 4096)                = 0
mmap2(NULL, 385024, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41ab000
gettimeofday({1231474590, 618654}, NULL) = 0
access("/usr/lib/oracle/network/admin/sqlnet.ora", F_OK) = 0
open("/usr/lib/oracle/network/admin/sqlnet.ora", O_RDONLY|O_LARGEFILE) = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFREG|0777, st_size=191, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41aa000
read(3, "TRACE_LEVEL_CLIENT = OFF\r\n#sqlne"..., 4096) = 191
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb41aa000, 4096)                = 0
access("/usr/lib/oracle/network/admin/sqlnet.ora", F_OK) = 0
open("/usr/lib/oracle/network/admin/sqlnet.ora", O_RDONLY|O_LARGEFILE) = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFREG|0777, st_size=191, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41aa000
read(3, "TRACE_LEVEL_CLIENT = OFF\r\n#sqlne"..., 4096) = 191
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb41aa000, 4096)                = 0
fcntl64(140922840, F_SETFD, FD_CLOEXEC) = -1 EBADF (Bad file descriptor)
times(NULL)                             = 1719888474
brk(0x8696000)                          = 0x8696000
rt_sigprocmask(SIG_BLOCK, [INT], NULL, 8) = 0
rt_sigaction(SIGINT, {0xb7cd6500, ~[ILL ABRT BUS FPE SEGV USR2 XCPU XFSZ SYS RTMIN RT_1], SA_RESTART|SA_SIGINFO}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [INT], NULL, 8) = 0
gettimeofday({1231474590, 621464}, NULL) = 0
gettimeofday({1231474590, 621591}, NULL) = 0
fstat64(1, {st_mode=S_IFREG|0777, st_size=35366, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41aa000
write(1, "\nSQL*Plus: Release 10.2.0.1.0 - "..., 128
SQL*Plus: Release 10.2.0.1.0 - Production on Fri Jan 9 14:16:30 2009

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

) = 128
getcwd("/usr/lib/oracle/network/admin", 256) = 30
brk(0x86b7000)                          = 0x86b7000
access("/usr/lib/oracle/network/admin/sqlnet.ora", F_OK) = 0
open("/usr/lib/oracle/network/admin/sqlnet.ora", O_RDONLY|O_LARGEFILE) = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFREG|0777, st_size=191, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41a9000
read(3, "TRACE_LEVEL_CLIENT = OFF\r\n#sqlne"..., 4096) = 191
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb41a9000, 4096)                = 0
access("/home/binneyd/.sqlnet.ora", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/oracle/network/admin/cli_12784.trc", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/oracle/network/admin/sqlnet.ora", F_OK) = 0
open("/usr/lib/oracle/network/admin/sqlnet.ora", O_RDONLY|O_LARGEFILE) = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFREG|0777, st_size=191, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41a9000
read(3, "TRACE_LEVEL_CLIENT = OFF\r\n#sqlne"..., 4096) = 191
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb41a9000, 4096)                = 0
access("/usr/lib/oracle/network/admin/intchg.ora", F_OK) = -1 ENOENT (No such file or directory)
access("/etc/intchg.ora", F_OK)         = -1 ENOENT (No such file or directory)
access("/usr/lib/oracle/oracle_client/network/admin/intchg.ora", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/oracle/network/admin/tnsnav.ora", F_OK) = 0
open("/usr/lib/oracle/network/admin/tnsnav.ora", O_RDONLY|O_LARGEFILE) = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFREG|0777, st_size=71908, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41a9000
read(3, "# C:\\ORANT\\NET80\\ADMIN\\TNSNAMES."..., 4096) = 4096
read(3, ")\r\n  )\r\n\r\nARPROD.WORLD =\r\n  (DES"..., 4096) = 4096
read(3, "cqu.edu.au)(PORT = 1521))\r\n    ("..., 4096) = 4096
read(3, "ST = b87e01s01-vip.cqu.edu.au)\r\n"..., 4096) = 4096
read(3, "OL = TCP)\r\n      (HOST = b19e01s"..., 4096) = 4096
read(3, "cqu.edu.au)\r\n    )\r\n  )\r\n\r\nSTUDE"..., 4096) = 4096
read(3, "au)\r\n      (INSTANCE_NAME = CS89"..., 4096) = 4096
read(3, ".au)\r\n      (PORT = 1521)\r\n    )"..., 4096) = 4096
read(3, " CS89A1.cqu.edu.au)\r\n    )\r\n  )\r"..., 4096) = 4096
read(3, " 1521))\r\n      (ADDRESS = (PROTO"..., 4096) = 4096
read(3, "(PORT = 1521))\r\n    (ADDRESS = ("..., 4096) = 4096
read(3, "(CONNECT_DATA = \r\n      (SERVER "..., 4096) = 4096
read(3, "DESCRIPTION =\r\n    (ADDRESS = (P"..., 4096) = 4096
read(3, "ATA = (SID = hetr2))\r\n  )\r\n\r\n###"..., 4096) = 4096
read(3, "pilot.cqu.edu.au)(PORT = 1521))\r"..., 4096) = 4096
read(3, "A =\r\n      (SID = CONMGMT)\r\n    "..., 4096) = 4096
read(3, "TOCOL = TCP)(HOST = jet.cqu.edu."..., 4096) = 4096
read(3, "   (CONNECT_DATA = \r\n      (SERV"..., 4096) = 2276
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb41a9000, 4096)                = 0
gettimeofday({1231474590, 641387}, NULL) = 0
open("/usr/lib/oracle/oracle_client/network/names/.sdns.ora", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
getrlimit(RLIMIT_NOFILE, {rlim_cur=1024, rlim_max=1024}) = 0
getcwd("/usr/lib/oracle/network/admin", 256) = 30
gettimeofday({1231474590, 641857}, NULL) = 0
open("/usr/lib/oracle/oracle_client/network/names/.sdns.ora", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
fcntl64(141133136, F_SETFD, FD_CLOEXEC) = -1 EBADF (Bad file descriptor)
write(1, "ERROR:\n", 7ERROR:
)                 = 7
write(1, "ORA-12154: TNS:could not resolve"..., 66ORA-12154: TNS:could not resolve the connect identifier specified
) = 66
write(1, "\n\n", 2

)                     = 2
write(1, "Enter user-name: ", 17Enter user-name: )       = 17
brk(0x86dd000)                          = 0x86dd000
fstat64(0, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41a9000
read(0,  <unfinished ...>
execve("/usr/lib/oracle/oracle_client/bin/sqlplus", ["sqlplus", "user/pass@STUDD1"], [/* 42 vars */]) = 0
brk(0)                                  = 0x8633000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb8076000
readlink("/proc/self/exe", "/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/sqlplus", 4096) = 63
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686/sse2/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686/sse2/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686/sse2/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686/sse2", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/i686", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/sse2/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/sse2/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/sse2/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/sse2", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/tls", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686/sse2/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686/sse2/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686/sse2/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686/sse2", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/i686", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/sse2/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/sse2/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/sse2/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/sse2", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/cmov/libsqlplus.so", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/cmov", 0xbf892d9c) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libsqlplus.so", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0PH\1\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=726188, ...}) = 0
mmap2(NULL, 725448, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7fc4000
mmap2(0xb806d000, 36864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa9) = 0xb806d000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libclntsh.so.10.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\343"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=14273496, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7fc3000
mmap2(NULL, 14356808, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7211000
mmap2(0xb7f4d000, 397312, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xd3c) = 0xb7f4d000
mmap2(0xb7fae000, 82248, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7fae000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libnnz10.so", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300:\6"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=2106868, ...}) = 0
mmap2(NULL, 2115380, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb700c000
mmap2(0xb71e9000, 159744, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1dc) = 0xb71e9000
mmap2(0xb7210000, 1844, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7210000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/i686", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/tls", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/i686", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../lib", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/i686", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/tls", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/i686", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../../oracle/lib", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls/i686/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls/i686/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls/i686/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls/i686", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/tls/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/tls", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/i686/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/i686/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/i686/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/i686/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/i686", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/sse2/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/sse2", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib/cmov", 0xbf892d48) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
stat64("/usr/lib/oracle/oracle_client/lib", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("tls/i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/libdl.so.2", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("tls/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/sse2/libdl.so.2", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("tls/cmov/libdl.so.2", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("tls/libdl.so.2", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("i686/sse2/cmov/libdl.so.2", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/sse2/libdl.so.2", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("i686/cmov/libdl.so.2", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("i686/libdl.so.2", O_RDONLY)       = -1 ENOENT (No such file or directory)
open("sse2/cmov/libdl.so.2", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("sse2/libdl.so.2", O_RDONLY)       = -1 ENOENT (No such file or directory)
open("cmov/libdl.so.2", O_RDONLY)       = -1 ENOENT (No such file or directory)
open("libdl.so.2", O_RDONLY)            = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=68409, ...}) = 0
mmap2(NULL, 68409, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb6ffb000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 \n\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9676, ...}) = 0
mmap2(NULL, 12408, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6ff7000
mmap2(0xb6ff9000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb6ff9000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/cmov/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/cmov/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/libm.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("tls/sse2/cmov/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/sse2/libm.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("tls/cmov/libm.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("tls/libm.so.6", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("i686/sse2/cmov/libm.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/sse2/libm.so.6", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("i686/cmov/libm.so.6", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("i686/libm.so.6", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("sse2/cmov/libm.so.6", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("sse2/libm.so.6", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("cmov/libm.so.6", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("libm.so.6", O_RDONLY)             = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@4\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=149332, ...}) = 0
mmap2(NULL, 151680, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6fd1000
mmap2(0xb6ff5000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x23) = 0xb6ff5000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/cmov/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/cmov/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/sse2/cmov/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/sse2/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/cmov/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/libpthread.so.0", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("i686/sse2/cmov/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/sse2/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/cmov/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/libpthread.so.0", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("sse2/cmov/libpthread.so.0", O_RDONLY) = -1 ENOENT (No such file or directory)
open("sse2/libpthread.so.0", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("cmov/libpthread.so.0", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("libpthread.so.0", O_RDONLY)       = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000H\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=116457, ...}) = 0
mmap2(NULL, 98784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6fb8000
mmap2(0xb6fcd000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14) = 0xb6fcd000
mmap2(0xb6fcf000, 4576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6fcf000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/cmov/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/cmov/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/libnsl.so.1", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("tls/sse2/cmov/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/sse2/libnsl.so.1", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("tls/cmov/libnsl.so.1", O_RDONLY)  = -1 ENOENT (No such file or directory)
open("tls/libnsl.so.1", O_RDONLY)       = -1 ENOENT (No such file or directory)
open("i686/sse2/cmov/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/sse2/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/cmov/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/libnsl.so.1", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("sse2/cmov/libnsl.so.1", O_RDONLY) = -1 ENOENT (No such file or directory)
open("sse2/libnsl.so.1", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("cmov/libnsl.so.1", O_RDONLY)      = -1 ENOENT (No such file or directory)
open("libnsl.so.1", O_RDONLY)           = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnsl.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\00001\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=87804, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6fb7000
mmap2(NULL, 100328, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6f9e000
mmap2(0xb6fb3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x14) = 0xb6fb3000
mmap2(0xb6fb5000, 6120, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6fb5000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/oracle_client/lib/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/cmov/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/sse2/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/cmov/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/i686/libc.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("tls/sse2/cmov/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("tls/sse2/libc.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("tls/cmov/libc.so.6", O_RDONLY)    = -1 ENOENT (No such file or directory)
open("tls/libc.so.6", O_RDONLY)         = -1 ENOENT (No such file or directory)
open("i686/sse2/cmov/libc.so.6", O_RDONLY) = -1 ENOENT (No such file or directory)
open("i686/sse2/libc.so.6", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("i686/cmov/libc.so.6", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("i686/libc.so.6", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("sse2/cmov/libc.so.6", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("sse2/libc.so.6", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("cmov/libc.so.6", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("libc.so.6", O_RDONLY)             = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340g\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1425800, ...}) = 0
mmap2(NULL, 1431152, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6e40000
mmap2(0xb6f98000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x158) = 0xb6f98000
mmap2(0xb6f9b000, 9840, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb6f9b000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6e3f000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb6e3f8c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb6f98000, 8192, PROT_READ)   = 0
mprotect(0xb6fb3000, 4096, PROT_READ)   = 0
mprotect(0xb6fcd000, 4096, PROT_READ)   = 0
mprotect(0xb6ff5000, 4096, PROT_READ)   = 0
mprotect(0xb6ff9000, 4096, PROT_READ)   = 0
mprotect(0xb700c000, 1953792, PROT_READ|PROT_WRITE) = 0
mprotect(0xb700c000, 1953792, PROT_READ|PROT_EXEC) = 0
mprotect(0xb7211000, 13877248, PROT_READ|PROT_WRITE) = 0
mprotect(0xb7211000, 13877248, PROT_READ|PROT_EXEC) = 0
mprotect(0xb7fc4000, 692224, PROT_READ|PROT_WRITE) = 0
mprotect(0xb7fc4000, 692224, PROT_READ|PROT_EXEC) = 0
mprotect(0xb8093000, 4096, PROT_READ)   = 0
munmap(0xb6ffb000, 68409)               = 0
set_tid_address(0xb6e3f908)             = 12784
set_robust_list(0xb6e3f910, 0xc)        = 0
futex(0xbf893450, 0x81 /* FUTEX_??? */, 1) = 0
rt_sigaction(SIGRTMIN, {0xb6fbc2e0, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb6fbc720, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="donkeyhome", ...}) = 0
brk(0)                                  = 0x8633000
brk(0x8654000)                          = 0x8654000
mmap2(NULL, 143360, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb6e1c000
futex(0xb6ffa06c, 0x81 /* FUTEX_??? */, 2147483647) = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libsqlplusic.so", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\\\7\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1432504, ...}) = 0
mmap2(NULL, 1435468, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb6cbd000
mmap2(0xb6e1b000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15d) = 0xb6e1b000
close(3)                                = 0
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libociei.so", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/oracle/xe/app/oracle/product/10.2.0/client/bin/../lib/libocixe.so", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p&\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=44617172, ...}) = 0
mmap2(NULL, 44620148, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb422f000
mmap2(0xb6cbb000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2a8b) = 0xb6cbb000
close(3)                                = 0
mprotect(0xb422f000, 44613632, PROT_READ|PROT_WRITE) = 0
mprotect(0xb422f000, 44613632, PROT_READ|PROT_EXEC) = 0
mmap2(NULL, 155648, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb4209000
fcntl64(140850200, F_SETFD, FD_CLOEXEC) = -1 EBADF (Bad file descriptor)
fcntl64(140850736, F_SETFD, FD_CLOEXEC) = -1 EBADF (Bad file descriptor)
brk(0x8675000)                          = 0x8675000
fcntl64(140853208, F_SETFD, FD_CLOEXEC) = -1 EBADF (Bad file descriptor)
gettimeofday({1231474590, 615993}, NULL) = 0
open("/etc/localtime", O_RDONLY)        = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=413, ...}) = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=413, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb4208000
read(3, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\4\0\0\0\4\0\0"..., 4096) = 413
_llseek(3, -8, [405], SEEK_CUR)         = 0
read(3, "\nEST-10\n", 4096)             = 8
close(3)                                = 0
munmap(0xb4208000, 4096)                = 0
mmap2(NULL, 385024, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41ab000
gettimeofday({1231474590, 618654}, NULL) = 0
access("/usr/lib/oracle/network/admin/sqlnet.ora", F_OK) = 0
open("/usr/lib/oracle/network/admin/sqlnet.ora", O_RDONLY|O_LARGEFILE) = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFREG|0777, st_size=191, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41aa000
read(3, "TRACE_LEVEL_CLIENT = OFF\r\n#sqlne"..., 4096) = 191
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb41aa000, 4096)                = 0
access("/usr/lib/oracle/network/admin/sqlnet.ora", F_OK) = 0
open("/usr/lib/oracle/network/admin/sqlnet.ora", O_RDONLY|O_LARGEFILE) = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFREG|0777, st_size=191, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41aa000
read(3, "TRACE_LEVEL_CLIENT = OFF\r\n#sqlne"..., 4096) = 191
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb41aa000, 4096)                = 0
fcntl64(140922840, F_SETFD, FD_CLOEXEC) = -1 EBADF (Bad file descriptor)
times(NULL)                             = 1719888474
brk(0x8696000)                          = 0x8696000
rt_sigprocmask(SIG_BLOCK, [INT], NULL, 8) = 0
rt_sigaction(SIGINT, {0xb7cd6500, ~[ILL ABRT BUS FPE SEGV USR2 XCPU XFSZ SYS RTMIN RT_1], SA_RESTART|SA_SIGINFO}, {SIG_DFL}, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [INT], NULL, 8) = 0
gettimeofday({1231474590, 621464}, NULL) = 0
gettimeofday({1231474590, 621591}, NULL) = 0
fstat64(1, {st_mode=S_IFREG|0777, st_size=35366, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41aa000
write(1, "\nSQL*Plus: Release 10.2.0.1.0 - "..., 128
SQL*Plus: Release 10.2.0.1.0 - Production on Fri Jan 9 14:16:30 2009

Copyright (c) 1982, 2005, Oracle.  All rights reserved.

) = 128
getcwd("/usr/lib/oracle/network/admin", 256) = 30
brk(0x86b7000)                          = 0x86b7000
access("/usr/lib/oracle/network/admin/sqlnet.ora", F_OK) = 0
open("/usr/lib/oracle/network/admin/sqlnet.ora", O_RDONLY|O_LARGEFILE) = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFREG|0777, st_size=191, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41a9000
read(3, "TRACE_LEVEL_CLIENT = OFF\r\n#sqlne"..., 4096) = 191
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb41a9000, 4096)                = 0
access("/home/binneyd/.sqlnet.ora", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/oracle/network/admin/cli_12784.trc", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/oracle/network/admin/sqlnet.ora", F_OK) = 0
open("/usr/lib/oracle/network/admin/sqlnet.ora", O_RDONLY|O_LARGEFILE) = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFREG|0777, st_size=191, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41a9000
read(3, "TRACE_LEVEL_CLIENT = OFF\r\n#sqlne"..., 4096) = 191
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb41a9000, 4096)                = 0
access("/usr/lib/oracle/network/admin/intchg.ora", F_OK) = -1 ENOENT (No such file or directory)
access("/etc/intchg.ora", F_OK)         = -1 ENOENT (No such file or directory)
access("/usr/lib/oracle/oracle_client/network/admin/intchg.ora", F_OK) = -1 ENOENT (No such file or directory)
access("/usr/lib/oracle/network/admin/tnsnav.ora", F_OK) = 0
open("/usr/lib/oracle/network/admin/tnsnav.ora", O_RDONLY|O_LARGEFILE) = 3
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fstat64(3, {st_mode=S_IFREG|0777, st_size=71908, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41a9000
read(3, "# C:\\ORANT\\NET80\\ADMIN\\TNSNAMES."..., 4096) = 4096
read(3, ")\r\n  )\r\n\r\nARPROD.WORLD =\r\n  (DES"..., 4096) = 4096
read(3, "cqu.edu.au)(PORT = 1521))\r\n    ("..., 4096) = 4096
read(3, "ST = b87e01s01-vip.cqu.edu.au)\r\n"..., 4096) = 4096
read(3, "OL = TCP)\r\n      (HOST = b19e01s"..., 4096) = 4096
read(3, "cqu.edu.au)\r\n    )\r\n  )\r\n\r\nSTUDE"..., 4096) = 4096
read(3, "au)\r\n      (INSTANCE_NAME = CS89"..., 4096) = 4096
read(3, ".au)\r\n      (PORT = 1521)\r\n    )"..., 4096) = 4096
read(3, " CS89A1.cqu.edu.au)\r\n    )\r\n  )\r"..., 4096) = 4096
read(3, " 1521))\r\n      (ADDRESS = (PROTO"..., 4096) = 4096
read(3, "(PORT = 1521))\r\n    (ADDRESS = ("..., 4096) = 4096
read(3, "(CONNECT_DATA = \r\n      (SERVER "..., 4096) = 4096
read(3, "DESCRIPTION =\r\n    (ADDRESS = (P"..., 4096) = 4096
read(3, "ATA = (SID = hetr2))\r\n  )\r\n\r\n###"..., 4096) = 4096
read(3, "pilot.cqu.edu.au)(PORT = 1521))\r"..., 4096) = 4096
read(3, "A =\r\n      (SID = CONMGMT)\r\n    "..., 4096) = 4096
read(3, "TOCOL = TCP)(HOST = jet.cqu.edu."..., 4096) = 4096
read(3, "   (CONNECT_DATA = \r\n      (SERV"..., 4096) = 2276
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb41a9000, 4096)                = 0
gettimeofday({1231474590, 641387}, NULL) = 0
open("/usr/lib/oracle/oracle_client/network/names/.sdns.ora", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
getrlimit(RLIMIT_NOFILE, {rlim_cur=1024, rlim_max=1024}) = 0
getcwd("/usr/lib/oracle/network/admin", 256) = 30
gettimeofday({1231474590, 641857}, NULL) = 0
open("/usr/lib/oracle/oracle_client/network/names/.sdns.ora", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
fcntl64(141133136, F_SETFD, FD_CLOEXEC) = -1 EBADF (Bad file descriptor)
write(1, "ERROR:\n", 7ERROR:
)                 = 7
write(1, "ORA-12154: TNS:could not resolve"..., 66ORA-12154: TNS:could not resolve the connect identifier specified
) = 66
write(1, "\n\n", 2

)                     = 2
write(1, "Enter user-name: ", 17Enter user-name: )       = 17
brk(0x86dd000)                          = 0x86dd000
fstat64(0, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb41a9000
read(0,  <unfinished ...>

```
[/CODE]

---

### Post by donkeyX on 2009-01-26
Hey Guys,

You know the saying that sometimes the simplest answer is the correct one.. Well the solution to this problem ended up being dos2unix over the tnsnames.ora and the sqlnet.ora files. That fixed the problem straight away, but is very annoying that there is no error message or any glimmer that this is the problem. It was only luck that ended up letting me find the answer to this :(

Cheers Dave and thanks for all the help

---

