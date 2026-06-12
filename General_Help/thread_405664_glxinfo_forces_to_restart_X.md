---
title: "glxinfo forces to restart X"
date: 2007-04-10
forum: General Help
---

### Post by Zero Override on 2007-04-10
People,

I just came across a strange happening on my system. When I try to run 'glxinfo' from a terminal, it looks like X is restarting... :o I don't know for sure, if it already was this way before the update to Feisty, or if it came after the update.

The problem is, that I just don't know where to look for this problem, is it xorg.conf related? :S

Thanks in advance for your help and time! :)

---

### Post by heimo on 2007-04-10
I'm afraid I can't help to solve this, but I'd run it with strace, output redirected to a file and see if it has any clues.
```
strace glxinfo > ~/glxinfo.log
[after crash]
less ~/glxinfo.log

```

---

### Post by Zero Override on 2007-04-10
That leaves me with an almost empty file...

Just this line;
```
name of display: :0.0
```
... :(

---

### Post by heimo on 2007-04-10
Oh, that's not you or strace. It's me and my syntax. Wait a minute. I'll update this post. 

Use this one:
```

2> ~/glxinfo.log strace glxinfo
```

---

### Post by Zero Override on 2007-04-10
That does give me some output, but it looks not like a normal glxinfo... :? Or is it? :p

```
execve("/usr/bin/glxinfo", ["glxinfo"], [/* 31 vars */]) = 0
brk(0)                                  = 0x804d000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f0a000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=51247, ...}) = 0
mmap2(NULL, 51247, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7efd000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libGL.so.1", O_RDONLY)   = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220\272"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=386460, ...}) = 0
mmap2(NULL, 390600, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e9d000
mmap2(0xb7efa000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x5d) = 0xb7efa000
mmap2(0xb7efc000, 1480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7efc000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0`\1\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1307104, ...}) = 0
mmap2(NULL, 1312164, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7d5c000
mmap2(0xb7e97000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13b) = 0xb7e97000
mmap2(0xb7e9a000, 9636, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7e9a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libX11.so.6", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200s\1"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=986540, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7d5b000
mmap2(NULL, 986876, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c6a000
mmap2(0xb7d57000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xed) = 0xb7d57000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXext.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\200*\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=56156, ...}) = 0
mmap2(NULL, 55228, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c5c000
mmap2(0xb7c69000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xd) = 0xb7c69000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXxf86vm.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\260\v\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=16220, ...}) = 0
mmap2(NULL, 19068, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c57000
mmap2(0xb7c5b000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0xb7c5b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P4\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=153424, ...}) = 0
mmap2(NULL, 155776, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c30000
mmap2(0xb7c55000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x24) = 0xb7c55000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libpthread.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20H\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=112362, ...}) = 0
mmap2(NULL, 90592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c19000
mmap2(0xb7c2c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13) = 0xb7c2c000
mmap2(0xb7c2e000, 4576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7c2e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libdl.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\n\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9684, ...}) = 0
mmap2(NULL, 12412, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c15000
mmap2(0xb7c17000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7c17000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libdrm.so.2", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340&\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=34492, ...}) = 0
mmap2(NULL, 34600, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c0c000
mmap2(0xb7c14000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8) = 0xb7c14000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7c0b000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXau.so.6", O_RDONLY)  = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\340\t\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=7356, ...}) = 0
mmap2(NULL, 10256, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c08000
mmap2(0xb7c0a000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1) = 0xb7c0a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libXdmcp.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300\17"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=17080, ...}) = 0
mmap2(NULL, 19968, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c03000
mmap2(0xb7c07000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3) = 0xb7c07000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7c02000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7c028d0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7e97000, 4096, PROT_READ)   = 0
mprotect(0xb7e9d000, 380928, PROT_READ|PROT_WRITE) = 0
mprotect(0xb7e9d000, 380928, PROT_READ|PROT_EXEC) = 0
munmap(0xb7efd000, 51247)               = 0
set_tid_address(0xb7c02918)             = 10557
sendto(-1212143328, umovestr: Input/output error
0xc, 3082997748, MSG_PROXY|MSG_EOR|MSG_ERRQUEUE|MSG_DONTWAIT|MSG_CONFIRM|0xb7c00000, {sa_family=AF_DECnet, sa_data="\0\0\320=\0\0\r\0\0\0p\362\0\0"}, 3213205640) = 0
rt_sigaction(SIGRTMIN, {0xb7c1d3f0, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb7c1d300, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="coen-laptop", ...}) = 0
brk(0)                                  = 0x804d000
brk(0x806e000)                          = 0x806e000
uname({sys="Linux", node="coen-laptop", ...}) = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 3
uname({sys="Linux", node="coen-laptop", ...}) = 0
uname({sys="Linux", node="coen-laptop", ...}) = 0
connect(3, {sa_family=AF_FILE, path="/tmp/.X11-unix/X0"}, 19) = 0
uname({sys="Linux", node="coen-laptop", ...}) = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
access("/home/coen/.Xauthority", R_OK)  = 0
open("/home/coen/.Xauthority", O_RDONLY) = 4
fstat64(4, {st_mode=S_IFREG|0600, st_size=122, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f09000
read(4, "\1\0\0\vcoen-laptop\0\0010\0\22MIT-MAGIC-CO"..., 4096) = 122
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb7f09000, 4096)                = 0
writev(3, [{"l\0\v\0\0\0\22\0\20\0\0\0", 12}, {"MIT-MAGIC-COOKIE-1", 18}, {"\0\0", 2}, {"\311Z\0220\32\353`\365k\373\256=\6\3413\367", 16}], 4) = 48
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(3, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
read(3, "\1\0\v\0\0\0Q\0", 8)           = 8
read(3, "\300*/\4\0\0\340\2\377\377\37\0\0\1\0\0\24\0\377\377\1"..., 324) = 324
write(3, "7\0\5\0\0\0\340\2P\0\0\0\10\0\0\0\377\377\377\0b\0\5\0"..., 64) = 64
read(3, "\1\"\2\0\0\0\0\0\1\203\0\0\1\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
read(3, "\1\10\3\0\250\6\0\0\37\0\0\0\0\0\0\0\236\32\0\0\0\0\0\0"..., 32) = 32
readv(3, [{"*Box.background:\t#ede9e3\n*Box.fo"..., 6814}, {"\0\0", 2}], 2) = 6816
write(3, "\203\0\1\0", 4)               = 4
read(3, "\1\234\4\0\0\0\0\0\377\377?\0\0\0\0\0\0\0\0\0\0\0\0\0\234"..., 32) = 32
writev(3, [{"b\0\5\0\t\0\340\2", 8}, {"XKEYBOARD", 9}, {"\0\0\0", 3}], 3) = 20
read(3, "\1\"\5\0\0\0\0\0\1\223o\254\0\20\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(3, "\223\0\2\0\1\0\0\0", 8)       = 8
read(3, "\1\1\6\0\0\0\0\0\1\0\0\0\250\264\305\277g\"\24\10\270\234"..., 32) = 32
fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f09000
write(1, "name of display: :0.0\n", 22) = 22
writev(3, [{"b\0\3\0\3\0\0\0", 8}, {"GLX", 3}, {"\0", 1}], 3) = 12
read(3, "\1\"\7\0\0\0\0\0\1\217M\231\0\20\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(3, "\217\7\3\0\1\0\0\0\4\0\0\0", 12) = 12
read(3, "\1\0\10\0\0\0\0\0\1\0\0\0\2\0\0\0@\370\274\267X\264\305"..., 32) = 32
writev(3, [{"b\7\5\0\v\0\0\0", 8}, {"XFree86-DRI", 11}, {"\0", 1}], 3) = 20
read(3, "\1\"\t\0\0\0\0\0\0\0\0\0\0\20\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 32) = 32
write(3, "\217\23\3\0\0\0\0\0\2\0\0\0", 12) = 12
read(3, "\1\4\n\0\1\0\0\0\360\377\377\377\4\0\0\0\200:\274\267\4"..., 32) = 32
read(3, "1.2\0", 4)                     = 4
write(3, "\217\23\3\0\0\0\0\0\3\0\0\0", 12) = 12
read(3, "\1\4\v\0C\0\0\0\360\377\377\377\t\1\0\0\200:\274\267\4"..., 32) = 32
read(3, "GLX_ARB_multisample GLX_EXT_visu"..., 265) = 265
read(3, "\351\355\0", 3)                = 3
write(3, "\217\21\4\0\4\0\1\0\3\0\0\0\0\0\0\0", 16) = 16
read(3, "\1\217\f\0\30\1\0\0\5\0\0\0\34\0\0\0J\6\t\10\204\306\35"..., 32) = 32
read(3, "\v\200\0\0N\0\0\0\23\200\0\0N\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0\"\0\0\0\23\200\0\0\"\0\0\0\22\200\0\0\1\0\0"..., 224) = 224
read(3, "\v\200\0\0#\0\0\0\23\200\0\0#\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0$\0\0\0\23\200\0\0$\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
read(3, "\v\200\0\0%\0\0\0\23\200\0\0%\0\0\0\22\200\0\0\1\0\0\0"..., 224) = 224
futex(0xb7efb144, FUTEX_WAKE, 2147483647) = 0
mmap2(NULL, 266240, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7bc1000
write(3, "\217\24\f\3\1\0\0\0\4\0\0\0\36\f\0\0GL_ARB_depth_tex"..., 3224) = 3224
read(3, 0xbf859ddc, 32)                 = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN, revents=POLLIN|POLLHUP}], 1, -1) = 1
read(3, "", 32)                         = 0
write(2, "X connection to :0.0 broken (exp"..., 65X connection to :0.0 broken (explicit kill or server shutdown).

) = 65
exit_group(1)                           = ?
Process 10557 detached
```

---

### Post by heimo on 2007-04-10
Doesn't give me any clues. :( Do you have glx working? Does glxgears crash X too?

---

