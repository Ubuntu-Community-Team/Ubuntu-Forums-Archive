---
title: "Cannot execute this file, has anyone seenthis before."
date: 2008-03-15
forum: General Help
---

### Post by danielf30 on 2008-03-15
This is relating to a nerverwinter nights server. The binary does otsee to want to run. 

thanks for any help..

this is on 7.10 amd 64 version

root@arcana:/home/nwnd/neverwinternights# ls -la nwserver
-rwxrwxr-x 1 nwnd nwnd 3691072 2006-08-15 15:15 nwserver
root@arcana:/home/nwnd/neverwinternights# file nwserver
nwserver: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.5, dynamically linked (uses shared libs), stripped
root@arcana:/home/nwnd/neverwinternights# lsattr nwserver
------------------ nwserver
root@arcana:/home/nwnd/neverwinternights# ./nwserver
-su: ./nwserver: No such file or directory
root@arcana:/home/nwnd/neverwinternights# strace ./nwserver
execve("./nwserver", ["./nwserver"], [/* 15 vars */]) = -1 ENOENT (No such file or directory)
dup(2)                                  = 3
fcntl(3, F_GETFL)                       = 0x8002 (flags O_RDWR|O_LARGEFILE)
fstat(3, {st_mode=S_IFCHR|0600, st_rdev=makedev(136, 0), ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2b1b33f87000
lseek(3, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
write(3, "strace: exec: No such file or di"..., 40strace: exec: No such file or directory
) = 40
close(3)                                = 0
munmap(0x2b1b33f87000, 4096)            = 0
exit_group(1)                           = ?
Process 4382 detached
root@arcana:/home/nwnd/neverwinternights#

---

### Post by danielf30 on 2008-03-15
HA HA I found the fix

had to install the 32bit compatability LIBs

here is the command.
 apt-get install ia32-libs


:) :) :) :)

---

