---
title: "adb server didnt ACK"
date: 2015-03-09
forum: General Help
---

### Post by brandonabandon on 2015-03-09
HELLO, im unable to start the adb server. im running ubuntu 12.04.5 32bit. the same issue with natty. i did strace on adb ```
brandonabandon@beazt:~$ strace adb fork-server server
execve("/home/brandonabandon/android-sdk-linux/platform-tools/adb", ["adb", "fork-server", "server"], [/* 36 vars */]) = 0
brk(0)                                  = 0xb95ee000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb75f5000
readlink("/proc/self/exe", "/home/brandonabandon/android-sdk-linux/platform-tools/adb", 4096) = 57
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/tls/i686/cmov/librt.so.1", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat64("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/tls/i686/cmov", 0xbfebe5a0) = -1 ENOENT (No such file or directory)
open("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/tls/i686/librt.so.1", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat64("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/tls/i686", 0xbfebe5a0) = -1 ENOENT (No such file or directory)
open("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/tls/cmov/librt.so.1", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat64("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/tls/cmov", 0xbfebe5a0) = -1 ENOENT (No such file or directory)
open("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/tls/librt.so.1", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat64("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/tls", 0xbfebe5a0) = -1 ENOENT (No such file or directory)
open("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/i686/cmov/librt.so.1", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat64("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/i686/cmov", 0xbfebe5a0) = -1 ENOENT (No such file or directory)
open("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/i686/librt.so.1", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat64("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/i686", 0xbfebe5a0) = -1 ENOENT (No such file or directory)
open("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/cmov/librt.so.1", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat64("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/cmov", 0xbfebe5a0) = -1 ENOENT (No such file or directory)
open("/home/brandonabandon/android-sdk-linux/platform-tools/../lib/librt.so.1", O_RDONLY|O_CLOEXEC) = -1 ENOENT (No such file or directory)
stat64("/home/brandonabandon/android-sdk-linux/platform-tools/../lib", 0xbfebe5a0) = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=67471, ...}) = 0
mmap2(NULL, 67471, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb75e4000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/librt.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\30\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=30684, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb75e3000
mmap2(NULL, 33360, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb75da000
mmap2(0xb75e1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6) = 0xb75e1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libdl.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\n\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=13940, ...}) = 0
mmap2(NULL, 16504, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb75d5000
mmap2(0xb75d8000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2) = 0xb75d8000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libpthread.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p[\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=124663, ...}) = 0
mmap2(NULL, 107008, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb75ba000
mmap2(0xb75d1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16) = 0xb75d1000
mmap2(0xb75d3000, 4608, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb75d3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/i386-linux-gnu/libstdc++.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0]\4\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=905712, ...}) = 0
mmap2(NULL, 935336, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb74d5000
mprotect(0xb75ad000, 4096, PROT_NONE)   = 0
mmap2(0xb75ae000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xd8) = 0xb75ae000
mmap2(0xb75b3000, 26024, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb75b3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libm.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000D\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=173576, ...}) = 0
mmap2(NULL, 176256, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb74a9000
mmap2(0xb74d3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x29) = 0xb74d3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libgcc_s.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\37\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=116232, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb74a8000
mmap2(NULL, 119344, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb748a000
mmap2(0xb74a6000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1b) = 0xb74a6000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0@\226\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1734120, ...}) = 0
mmap2(NULL, 1747676, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb72df000
mprotect(0xb7483000, 4096, PROT_NONE)   = 0
mmap2(0xb7484000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1a4) = 0xb7484000
mmap2(0xb7487000, 10972, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7487000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb72de000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb72dd000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb72dd700, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7484000, 8192, PROT_READ)   = 0
mprotect(0xb74a6000, 4096, PROT_READ)   = 0
mprotect(0xb74d3000, 4096, PROT_READ)   = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb72dc000
mprotect(0xb75ae000, 16384, PROT_READ)  = 0
mprotect(0xb75d1000, 4096, PROT_READ)   = 0
mprotect(0xb75d8000, 4096, PROT_READ)   = 0
mprotect(0xb75e1000, 4096, PROT_READ)   = 0
mprotect(0xb7617000, 4096, PROT_READ)   = 0
munmap(0xb75e4000, 67471)               = 0
set_tid_address(0xb72dd768)             = 12878
set_robust_list(0xb72dd770, 0xc)        = 0
futex(0xbfebebb4, FUTEX_WAIT_BITSET_PRIVATE|FUTEX_CLOCK_REALTIME, 1, NULL, b72dd700) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGRTMIN, {0xb75bf570, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb75bf5f0, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="beazt", ...}) = 0
rt_sigaction(SIGPIPE, {SIG_IGN, [PIPE], SA_RESTART}, {SIG_DFL, [], 0}, 8) = 0
socketpair(PF_FILE, SOCK_STREAM, 0, [3, 4]) = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(4, F_SETFL, O_RDONLY|O_NONBLOCK) = 0
brk(0)                                  = 0xb95ee000
brk(0xb960f000)                         = 0xb960f000
open("/home/brandonabandon/.android/adb_usb.ini", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
rt_sigaction(SIGALRM, {0xb763b7d0, [], 0}, NULL, 8) = 0
mmap2(NULL, 8392704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_STACK, -1, 0) = 0xb6adb000
mprotect(0xb6adb000, 4096, PROT_NONE)   = 0
clone(child_stack=0xb72db424, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0xb72dbba8, {entry_number:6, base_addr:0xb72dbb40, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}, child_tidptr=0xb72dbba8) = 12879
mmap2(NULL, 8392704, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS|MAP_STACK, -1, 0) = 0xb62da000
mprotect(0xb62da000, 4096, PROT_NONE)   = 0
clone(child_stack=0xb6ada424, flags=CLONE_VM|CLONE_FS|CLONE_FILES|CLONE_SIGHAND|CLONE_THREAD|CLONE_SYSVSEM|CLONE_SETTLS|CLONE_PARENT_SETTID|CLONE_CHILD_CLEARTID, parent_tidptr=0xb6adaba8, {entry_number:6, base_addr:0xb6adab40, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}, child_tidptr=0xb6adaba8) = 12880
stat64("/home/brandonabandon/.android", {st_mode=S_IFDIR|0775, st_size=4096, ...}) = 0
stat64("/home/brandonabandon/.android/adbkey", 0xbfeb9a10) = -1 ENOENT (No such file or directory)
time(NULL)                              = 1425926691
--- SIGILL (Illegal instruction) @ 0 (0) ---
+++ killed by SIGILL (core dumped) +++
Illegal instruction (core dumped)
```

no adb process within taskmanager. i did udev rules. my phone is able to connect via debugging. any suggestions?

---

### Post by brandonabandon on 2015-03-11
[http://www.webupd8.org/2012/08/install-adb-and-fastboot-android-tools.html](http://www.webupd8.org/2012/08/install-adb-and-fastboot-android-tools.html) this method is easier anyhow. sdk always worked before on this unit. good thing i dont need eclipse.

---

