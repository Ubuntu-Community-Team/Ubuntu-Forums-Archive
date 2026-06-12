---
title: "Firefox fails to start"
date: 2007-08-07
forum: General Help
---

### Post by satimis on 2007-08-07
Hi folks,

Ubuntu 7.04


Firefox fails to start finally after starting.  This happens after removing Acrobat Reader download on Internet and reinstall it on repo.

On terminal;
$ firefox &```

[1] 5467
satimis@ubuntu704:~$ ** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

```
It hung here.

Ran;
$ strace -r firefox -x echo &> /tmp/log
It also hung here.

$ sudo tail /tmp/log 
Password:```

     0.006570 rt_sigaction(SIGCHLD, {SIG_DFL}, {SIG_IGN}, 8) = 0
     0.000240 close(64)                 = 0
     0.000104 close(65)                 = 0
     0.000111 fcntl64(63, F_GETFD)      = 0
     0.000104 fcntl64(63, F_SETFD, FD_CLOEXEC) = 0
     0.000132 fcntl64(63, F_GETFL)      = 0 (flags O_RDONLY)
     0.000125 fstat64(63, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
     0.000184 mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb67ac000
     0.000139 _llseek(63, 0, 0xbff336ec, SEEK_CUR) = -1 ESPIPE (Illegal seek)
     0.000151 read(63, 


```

Please advise how to fix the problem.  TIA


satimis

---

