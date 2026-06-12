---
title: "blktrace, BLKTRACESETUP: Inappropriate ioctl for device"
date: 2007-04-14
forum: General Help
---

### Post by useche on 2007-04-14
Hi Guys,

I had installed in my laptop (Dell Inspiron 600m) ubuntu 6.10 and blktrace works just fine with my /dev/hda device. However, after installing Feisty, the blktrace program do not work anymore when I try to trace the /dev/sda device (the same device as in the 6.10 but exported in a different way). The error:
```
BLKTRACESETUP: Inappropriate ioctl for device
Failed to start trace on /dev/sda
```

Maybe an important clue for you guys is the output of strace:
```
execve("/usr/sbin/blktrace", ["blktrace", "/dev/sda"], [/* 19 vars */]) = 0
brk(0)                                  = 0x804e000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f43000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=44834, ...}) = 0
mmap2(NULL, 44834, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f38000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20H\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=112362, ...}) = 0
mmap2(NULL, 90592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7f21000
mmap2(0xb7f34000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xb7f34000
mmap2(0xb7f36000, 4576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f36000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0`\1\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1307104, ...}) = 0
mmap2(NULL, 1312164, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7de0000
mmap2(0xb7f1b000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13b) = 0xb7f1b000
mmap2(0xb7f1e000, 9636, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7f1e000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7ddf000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7dde000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7dde6c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7f1b000, 4096, PROT_READ)   = 0
munmap(0xb7f38000, 44834)               = 0
set_tid_address(0xb7dde708)             = 6652
sendto(-1210194160, umovestr: Input/output error
0xc, 3086176244, MSG_EOR|MSG_ERRQUEUE|MSG_DONTWAIT|MSG_FIN|MSG_SYN|MSG_NOSIGNAL|MSG_MORE|0xb7dd0000, {sa_family=AF_DECnet, sa_data="\0\0\320=\0\0\r\0\0\0p\362\0\0"}, 3218401176) = 0
rt_sigaction(SIGRTMIN, {0xb7f253f0, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb7f25300, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="beer", ...})  = 0
open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE) = -1 ENOENT (No such file or directory)
brk(0)                                  = 0x804e000
brk(0x806f000)                          = 0x806f000
open("/usr/share/locale/locale.alias", O_RDONLY) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2586, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f42000
read(3, "# Locale name alias data base.\n#"..., 4096) = 2586
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb7f42000, 4096)                = 0
open("/usr/lib/locale/en_US/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/lib/locale/en/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en_US/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_NUMERIC", O_RDONLY) = -1 ENOENT (No such file or directory)
statfs64("/sys/kernel/debug", 84, {f_type=0x64626720, f_bsize=4096, f_blocks=0, f_bfree=0, f_bavail=0, f_files=0, f_ffree=0, f_fsid={0, 0}, f_namelen=255, f_frsize=4096}) = 0
open("/dev/sda", O_RDONLY|O_NONBLOCK|O_LARGEFILE) = 3
open("/proc/stat", O_RDONLY)            = 4
fstat64(4, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f42000
read(4, "cpu  11986 123 1724 174139 9643 "..., 1024) = 645
read(4, "", 1024)                       = 0
close(4)                                = 0
munmap(0xb7f42000, 4096)                = 0
rt_sigaction(SIGINT, {0x804a950, [INT], SA_RESTART}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGHUP, {0x804a950, [HUP], SA_RESTART}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGTERM, {0x804a950, [TERM], SA_RESTART}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGALRM, {0x804a950, [ALRM], SA_RESTART}, {SIG_DFL}, 8) = 0
rt_sigaction(SIGPIPE, {SIG_IGN}, {SIG_DFL}, 8) = 0
ioctl(3, 0xc0401273, 0xbfd4e608)        = -1 ENOTTY (Inappropriate ioctl for device)
dup(2)                                  = 4
fcntl64(4, F_GETFL)                     = 0x2 (flags O_RDWR)
fstat64(4, {st_mode=S_IFCHR|0600, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f42000
_llseek(4, 0, 0xbfd4e064, SEEK_CUR)     = -1 ESPIPE (Illegal seek)
write(4, "BLKTRACESETUP: Inappropriate ioc"..., 46BLKTRACESETUP: Inappropriate ioctl for device
) = 46
close(4)                                = 0
munmap(0xb7f42000, 4096)                = 0
close(3)                                = 0
write(2, "Failed to start trace on /dev/sd"..., 34Failed to start trace on /dev/sda
) = 34
exit_group(1)                           = ?
Process 6652 detached

```

I do not know if I am missing some lilbrary or a should trace my device through other device  file that I don't know. Have some of you been able to run blktrace with Feisty?

Thanks in advance,

Luis

---

### Post by gnuthor on 2007-12-26
Dunno about feisty, but in gutsy (and my custom 2.6.23 kernel) you need to:

A) rebuild your kernel with option CONFIG_BLK_DEV_IO_TRACE
    (Enable the block layer/Support for tracing block io actions [Y])

B) mount debugfs
  sudo mount -t debugfs debugfs /sys/kernel/debug

A takes care of the IOCTL problem (as you've just added that particular feature to your block devices), B is just generally needed by blktrace ;-)

---

