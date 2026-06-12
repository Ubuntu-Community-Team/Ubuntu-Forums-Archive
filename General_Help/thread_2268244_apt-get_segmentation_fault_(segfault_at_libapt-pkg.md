---
title: "apt-get segmentation fault (segfault at libapt-pkg)"
date: 2015-03-07
forum: General Help
---

### Post by xnd on 2015-03-07
Hello

Since this morning, I couldn't run apt-get and having no idea why. This is what I did so far:

# apt-get update
(updating list)
Fetched 2.797 kB in 7s (363 kB/s)                                              
Segmentation faultsts... 33%

# apt-get install firefox (just a random app, same outcome to all)
Reading package lists.. 33%
Segmentation faultsts... 33%

# dmesg 
[ 1582.411234] apt-get[3436]: segfault at 7ff19fffad54 ip 00007ff1a1dc1507 sp 00007fff48a54f00 error 6 in libapt-pkg.so.4.12.0[7ff1a1cd2000+145000]
[ 1584.516803] apt-get[3439]: segfault at 7ff544971d54 ip 00007ff546738507 sp 00007fffa9bd6eb0 error 6 in libapt-pkg.so.4.12.0[7ff546649000+145000]

# strace apt-get install firefox
```
stat("/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-amd64_Packages", {st_mode=S_IFREG|0644, st_size=663770, ...}) = 0
umask(0)                                = 022
umask(022)                              = 0
open("/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_trusty_multiverse_binary-amd64_Packages", O_RDONLY) = 7
fcntl(7, F_SETFD, FD_CLOEXEC)           = 0
fstat(7, {st_mode=S_IFREG|0644, st_size=663770, ...}) = 0
close(7)                                = 0
fstat(6, {st_mode=S_IFREG|0644, st_size=663770, ...}) = 0
fstat(6, {st_mode=S_IFREG|0644, st_size=663770, ...}) = 0
read(6, "dcore4 (>= 1.2.2)\nConflicts: avi"..., 32053) = 32053
read(6, "aintainer: Jeremy Schoenhaar <je"..., 32602) = 32602
read(6, "407e2f57885a6d64155b52654c\nSHA25"..., 32204) = 32204
read(6, "s: https://bugs.launchpad.net/ub"..., 31916) = 31916
lseek(5, 26214399, SEEK_SET)            = 26214399
write(5, "\0", 1)                       = 1
mremap(0x7f6c912c0000, 25165824, 26214400, MREMAP_MAYMOVE) = 0x7f6c8f9c0000
--- SIGSEGV {si_signo=SIGSEGV, si_code=SEGV_MAPERR, si_addr=0x7f6c92a90d54} ---
+++ killed by SIGSEGV +++
Segmentation fault
```

Tried:

# rm -rf /var/cache/apt
# rm -rf /var/log/apt

# dpkg-reconfigure libapt-pkg4.12

Any thoughts? Thank you!

---

