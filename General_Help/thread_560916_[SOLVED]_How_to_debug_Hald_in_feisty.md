---
title: "[SOLVED] How to debug Hald in feisty?"
date: 2007-09-26
forum: General Help
---

### Post by Dardie on 2007-09-26
Please help?

I can't get hald to start in feisty. I think brought on by an abortive attempt to use module-assistant to install cdfs, followed by a manual compile install of that module.

I would really appreciate some advice on how best to go about problem-solving this, apart from getting up to speed on dbus and hald which I am already trying to do by reading the specs.

None of the files mentioned as problematic have changed, and I have tried setting each to rwxrwxrwx with no effect.

I would really appreciate any suggestions on resolving this, and I'd also like to help to improve the robustness and error reporting of the desktop when hald fails once I've resolved it. In my case, gdm just hangs and its not obvious to the general user that hald is to blame (or how to get back to a working console / x session). Apart from that, most of the other things that break when hald is broken also give no indication of what is going on.

Anyway this is the output (2 times, because it's not entirely deterministic), strace output below that:
[FONT="Courier New"]
root@dard:~# hald --daemon=no --verbose=yes
10:35:45.088 [I] hald.c:529: hal 0.5.9
10:35:45.088 [I] hald.c:594: Will not daemonize
10:35:45.089 [I] hald_dbus.c:4806: local server is listening at unix:abstract=/var/run/hald/dbus-0u4sBHcpLq,guid=af4aa898e5c3a660a700a10046fb2511
10:35:45.091 [I] hald_runner.c:299: Runner has pid 8317
Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
10:35:45.092 [I] hald_runner.c:180: runner connection is 0x80931c8
10:35:45.093 [I] mmap_cache.c:251: cache mtime is 1190121594
10:35:45.093 [W] ids.c:294: Couldn't stat pci.ids file '/usr/share/misc/pci.ids', errno=13: Permission denied
10:35:45.093 [W] ids.c:515: Couldn't stat usb.ids file '/usr/share/misc/usb.ids', errno=13: Permission denied
10:35:45.093 [E] osspec.c:310: Unable to inotify_add_watch() for '/usr/share/hal/fdi/preprobe': Permission denied
*** [DIE] osspec.c:watch_fdi_files():389 : Error watching fdi files
root@dard:~# 
root@dard:~# 
root@dard:~# hald --daemon=no --verbose=yes
10:36:53.877 [I] hald.c:529: hal 0.5.9
10:36:53.877 [I] hald.c:594: Will not daemonize
10:36:53.878 [I] hald_dbus.c:4806: local server is listening at unix:abstract=/var/run/hald/dbus-675MBziF89,guid=e68e0b2087813117c6e4b60046fb2555
Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
10:36:53.882 [I] hald_runner.c:299: Runner has pid 8348
10:36:53.883 [W] ci-tracker.c:200: Could not get uid for connection: org.freedesktop.DBus.Error.NameHasNoOwner Could not get UID of name 'org.freedesktop.DBus': no such name
10:36:53.883 [E] hald_dbus.c:4461: Cannot get caller info for org.freedesktop.DBus
10:36:53.883 [I] hald_runner.c:180: runner connection is 0x8093570
10:36:53.884 [I] mmap_cache.c:251: cache mtime is 1190121594
10:36:53.885 [W] ids.c:294: Couldn't stat pci.ids file '/usr/share/misc/pci.ids', errno=13: Permission denied
10:36:53.886 [W] ids.c:515: Couldn't stat usb.ids file '/usr/share/misc/usb.ids', errno=13: Permission denied
10:36:53.886 [E] osspec.c:310: Unable to inotify_add_watch() for '/usr/share/hal/fdi/preprobe': Permission denied
*** [DIE] osspec.c:watch_fdi_files():389 : Error watching fdi files
[/FONT]

STRACE OUTPUT
==========
[FONT="Courier New"]root@dard:~/# strace hald --daemon=no --verbose=yes
execve("/usr/sbin/hald", ["hald", "--daemon=no", "--verbose=yes"], [/* 34 vars */]) = 0
brk(0)                                  = 0x808d000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f44000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY)      = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=91139, ...}) = 0
mmap2(NULL, 91139, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb7f2d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libdbus-glib-1.so.2", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`l\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=110132, ...}) = 0
mmap2(NULL, 109024, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7f12000
mmap2(0xb7f2c000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1a) = 0xb7f2c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libgobject-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300x\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=237072, ...}) = 0
mmap2(NULL, 237252, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ed8000
mmap2(0xb7f11000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x39) = 0xb7f11000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libglib-2.0.so.0", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P\364\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=606288, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7ed7000
mmap2(NULL, 609924, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e42000
mmap2(0xb7ed6000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x93) = 0xb7ed6000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libdbus-1.so.3", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240Q\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=203808, ...}) = 0
mmap2(NULL, 207068, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7e0f000
mmap2(0xb7e41000, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x31) = 0xb7e41000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libm.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0P4\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=153424, ...}) = 0
mmap2(NULL, 155776, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7de8000
mmap2(0xb7e0d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x24) = 0xb7e0d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libc.so.6", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0`\1\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=1307104, ...}) = 0
mmap2(NULL, 1312164, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7ca7000
mmap2(0xb7de2000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x13b) = 0xb7de2000
mmap2(0xb7de5000, 9636, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7de5000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnsl.so.1", O_RDONLY) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`0\0\000"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=79596, ...}) = 0
mmap2(NULL, 91944, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7c90000
mmap2(0xb7ca3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x12) = 0xb7ca3000
mmap2(0xb7ca5000, 5928, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb7ca5000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7c8f000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7c8e000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7c8e6c0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7de2000, 4096, PROT_READ)   = 0
munmap(0xb7f2d000, 91139)               = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f43000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f42000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f41000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f40000
gettimeofday({1190864710, 746858}, NULL) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3f000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3e000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3d000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3c000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3b000
brk(0)                                  = 0x808d000
brk(0x80ae000)                          = 0x80ae000
gettimeofday({1190864710, 748095}, {4294966876, 0}) = 0
open("/etc/localtime", O_RDONLY)        = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=73, ...}) = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=73, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3a000
read(3, "TZif\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\2\0\0\0\2\0"..., 4096) = 73
close(3)                                = 0
munmap(0xb7f3a000, 4096)                = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=73, ...}) = 0
write(2, "10:45:10.748 [I] hald.c:529: hal"..., 3910:45:10.748 [I] hald.c:529: hal 0.5.9
) = 39
gettimeofday({1190864710, 749256}, {4294966876, 0}) = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=73, ...}) = 0
write(2, "10:45:10.749 [I] hald.c:594: Wil"..., 4810:45:10.749 [I] hald.c:594: Will not daemonize
) = 48
pipe([3, 4])                            = 0
fstat64(3, {st_mode=S_IFIFO|0600, st_size=0, ...}) = 0
fcntl64(3, F_GETFL)                     = 0 (flags O_RDONLY)
rt_sigaction(SIGTERM, {0x8056a40, [TERM], SA_RESTART}, {SIG_DFL}, 8) = 0
open("/dev/urandom", O_RDONLY)          = 5
read(5, "\313\360\235\313\275e\361!:^", 10) = 10
close(5)                                = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 5
bind(5, {sa_family=AF_FILE, path=@/var/run/hald/dbus-Rs7RDdt7w6}, 32) = 0
listen(5, 30)                           = 0
fcntl64(5, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(5, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
fcntl64(5, F_GETFD)                     = 0
fcntl64(5, F_SETFD, FD_CLOEXEC)         = 0
gettimeofday({1190864710, 751116}, NULL) = 0
open("/dev/urandom", O_RDONLY)          = 6
read(6, "I\266II\252\260<\344\313\21|C", 12) = 12
close(6)                                = 0
gettimeofday({1190864710, 751520}, {4294966876, 0}) = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=73, ...}) = 0
write(2, "10:45:10.751 [I] hald_dbus.c:480"..., 14610:45:10.751 [I] hald_dbus.c:4806: local server is listening at unix:abstract=/var/run/hald/dbus-Rs7RDdt7w6,guid=49b64949aab03ce4cb117c0046fb2746
) = 146
fstat64(5, {st_mode=S_IFSOCK|0777, st_size=0, ...}) = 0
fcntl64(5, F_GETFL)                     = 0x802 (flags O_RDWR|O_NONBLOCK)
socket(PF_FILE, SOCK_STREAM, 0)         = 6
connect(6, {sa_family=AF_FILE, path="/var/run/dbus/system_bus_socket"}, 33) = 0
fcntl64(6, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(6, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
fcntl64(6, F_GETFD)                     = 0
fcntl64(6, F_SETFD, FD_CLOEXEC)         = 0
getuid32()                              = 0
rt_sigaction(SIGPIPE, {SIG_IGN}, {SIG_DFL}, 8) = 0
poll([{fd=6, events=POLLOUT, revents=POLLOUT}], 1, 0) = 1
write(6, "\0", 1)                       = 1
write(6, "AUTH EXTERNAL 30\r\n", 18)    = 18
poll([{fd=6, events=POLLIN, revents=POLLIN}], 1, -1) = 1
read(6, "OK 313d49349d85e80c88c7990046fb1"..., 2048) = 37
poll([{fd=6, events=POLLOUT, revents=POLLOUT}], 1, -1) = 1
write(6, "BEGIN\r\n", 7)                = 7
poll([{fd=6, events=POLLIN|POLLOUT, revents=POLLOUT}], 1, -1) = 1
writev(6, [{"l\1\0\1\0\0\0\0\1\0\0\0n\0\0\0\1\1o\0\25\0\0\0/org/fre"..., 128}, {"", 0}], 2) = 128
gettimeofday({1190864710, 755004}, NULL) = 0
poll([{fd=6, events=POLLIN, revents=POLLIN}], 1, 25000) = 1
read(6, "l\2\1\1\n\0\0\0\1\0\0\0=\0\0\0\6\1s\0\5\0\0\0:1.21\0\0"..., 2048) = 260
read(6, 0x8091958, 2048)                = -1 EAGAIN (Resource temporarily unavailable)
fstat64(6, {st_mode=S_IFSOCK|0777, st_size=0, ...}) = 0
fcntl64(6, F_GETFL)                     = 0x802 (flags O_RDWR|O_NONBLOCK)
writev(6, [{"l\1\1\1k\0\0\0\2\0\0\0\177\0\0\0\1\1o\0\25\0\0\0/org/f"..., 144}, {"f\0\0\0type=\'signal\',interface=\'org"..., 107}], 2) = 251
open("/dev/urandom", O_RDONLY)          = 7
read(7, "\227\241\21\26\243\t/*R\323", 10) = 10
close(7)                                = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 7
bind(7, {sa_family=AF_FILE, path=@/var/run/hald/dbus-1bRWdJlgUZ}, 32) = 0
listen(7, 30)                           = 0
fcntl64(7, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(7, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
fcntl64(7, F_GETFD)                     = 0
fcntl64(7, F_SETFD, FD_CLOEXEC)         = 0
gettimeofday({1190864710, 757118}, NULL) = 0
open("/dev/urandom", O_RDONLY)          = 8
read(8, ":\356\345\5\265&Sq\200Z{\32", 12) = 12
close(8)                                = 0
fstat64(7, {st_mode=S_IFSOCK|0777, st_size=0, ...}) = 0
fcntl64(7, F_GETFL)                     = 0x802 (flags O_RDWR|O_NONBLOCK)
pipe([8, 9])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7c8e708) = 8577
close(9)                                = 0
read(8, "", 8)                          = 0
close(8)                                = 0
gettimeofday({1190864710, 766024}, {4294966876, 0}) = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=73, ...}) = 0
write(2, "10:45:10.766 [I] hald_runner.c:2"..., 5610:45:10.766 [I] hald_runner.c:299: Runner has pid 8577
) = 56
rt_sigaction(SIGCHLD, {0xb7e6e5c0, [], SA_NOCLDSTOP}, NULL, 8) = 0
waitpid(8577, 0xbfbd9f38, WNOHANG)      = 0
poll([{fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=6, events=POLLIN, revents=POLLIN}, {fd=7, events=POLLIN}], 4, 0) = 1
gettimeofday({1190864710, 766860}, NULL) = 0
writev(6, [{"l\1\0\1\31\0\0\0\3\0\0\0\207\0\0\0\1\1o\0\25\0\0\0/org"..., 152}, {"\24\0\0\0org.freedesktop.DBus\0", 25}], 2) = 177
gettimeofday({1190864710, 767334}, NULL) = 0
poll([{fd=6, events=POLLIN, revents=POLLIN}], 1, 25000) = 1
read(6, "l\2\1\1\0\0\0\0\3\0\0\0005\0\0\0\6\1s\0\5\0\0\0:1.21\0"..., 2048) = 275
read(6, 0x8091958, 2048)                = -1 EAGAIN (Resource temporarily unavailable)
gettimeofday({1190864710, 767801}, {4294966876, 0}) = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=73, ...}) = 0
write(2, "10:45:10.767 [W] ci-tracker.c:20"..., 17410:45:10.767 [W] ci-tracker.c:200: Could not get uid for connection: org.freedesktop.DBus.Error.NameHasNoOwner Could not get UID of name 'org.freedesktop.DBus': no such name
) = 174
gettimeofday({1190864710, 768132}, {4294966876, 0}) = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=73, ...}) = 0
write(2, "10:45:10.768 [E] hald_dbus.c:446"..., 8310:45:10.768 [E] hald_dbus.c:4461: Cannot get caller info for org.freedesktop.DBus
) = 83
read(6, 0x8091958, 2048)                = -1 EAGAIN (Resource temporarily unavailable)
poll([{fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=7, events=POLLIN}, {fd=6, events=POLLIN}], 4, 0) = 0
poll(Runner started - allowed paths are '/usr/lib/hal:/usr/lib/hal/scripts:/usr/bin'
[{fd=3, events=POLLIN}, {fd=5, events=POLLIN}, {fd=7, events=POLLIN, revents=POLLIN}, {fd=6, events=POLLIN}], 4, -1) = 1
accept(7, {sa_family=AF_FILE, path="&#65533;&#65533;&#934;&#65533;&#65533;"}, [2]) = 8
fcntl64(8, F_GETFD)                     = 0
fcntl64(8, F_SETFD, FD_CLOEXEC)         = 0
fcntl64(8, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(8, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
rt_sigaction(SIGPIPE, {SIG_IGN}, {SIG_IGN}, 8) = 0
fstat64(8, {st_mode=S_IFSOCK|0777, st_size=0, ...}) = 0
fcntl64(8, F_GETFL)                     = 0x802 (flags O_RDWR|O_NONBLOCK)
gettimeofday({1190864710, 770897}, {4294966876, 0}) = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=73, ...}) = 0
write(2, "10:45:10.770 [I] hald_runner.c:1"..., 6710:45:10.770 [I] hald_runner.c:180: runner connection is 0x8093570
) = 67
socket(PF_FILE, SOCK_STREAM, 0)         = 9
fcntl64(9, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(9, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
connect(9, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(9)                                = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 9
fcntl64(9, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(9, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
connect(9, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(9)                                = 0
open("/etc/nsswitch.conf", O_RDONLY)    = 9
fstat64(9, {st_mode=S_IFREG|0644, st_size=503, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f3a000
read(9, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 503
read(9, "", 4096)                       = 0
close(9)                                = 0
munmap(0xb7f3a000, 4096)                = 0
open("/etc/ld.so.cache", O_RDONLY)      = 9
fstat64(9, {st_mode=S_IFREG|0644, st_size=91139, ...}) = 0
mmap2(NULL, 91139, PROT_READ, MAP_PRIVATE, 9, 0) = 0xb7c77000
close(9)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_compat.so.2", O_RDONLY) = 9
read(9, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\16\0\000"..., 512) = 512
fstat64(9, {st_mode=S_IFREG|0644, st_size=30436, ...}) = 0
mmap2(NULL, 33348, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 9, 0) = 0xb7f32000
mmap2(0xb7f39000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 9, 0x6) = 0xb7f39000
close(9)                                = 0
munmap(0xb7c77000, 91139)               = 0
open("/etc/ld.so.cache", O_RDONLY)      = 9
fstat64(9, {st_mode=S_IFREG|0644, st_size=91139, ...}) = 0
mmap2(NULL, 91139, PROT_READ, MAP_PRIVATE, 9, 0) = 0xb7c77000
close(9)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_nis.so.2", O_RDONLY) = 9
read(9, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\31\0"..., 512) = 512
fstat64(9, {st_mode=S_IFREG|0644, st_size=34352, ...}) = 0
mmap2(NULL, 37436, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 9, 0) = 0xb7c6d000
mmap2(0xb7c75000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 9, 0x7) = 0xb7c75000
close(9)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/tls/i686/cmov/libnss_files.so.2", O_RDONLY) = 9
read(9, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\0\31\0"..., 512) = 512
fstat64(9, {st_mode=S_IFREG|0644, st_size=38416, ...}) = 0
mmap2(NULL, 41624, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 9, 0) = 0xb7c62000
mmap2(0xb7c6b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 9, 0x8) = 0xb7c6b000
close(9)                                = 0
munmap(0xb7c77000, 91139)               = 0
open("/etc/passwd", O_RDONLY)           = 9
fcntl64(9, F_GETFD)                     = 0
fcntl64(9, F_SETFD, FD_CLOEXEC)         = 0
_llseek(9, 0, [0], SEEK_CUR)            = 0
fstat64(9, {st_mode=S_IFREG|0644, st_size=1613, ...}) = 0
mmap2(NULL, 1613, PROT_READ, MAP_SHARED, 9, 0) = 0xb7f31000
_llseek(9, 1613, [1613], SEEK_SET)      = 0
munmap(0xb7f31000, 1613)                = 0
close(9)                                = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 9
fcntl64(9, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(9, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
connect(9, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(9)                                = 0
socket(PF_FILE, SOCK_STREAM, 0)         = 9
fcntl64(9, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(9, F_SETFL, O_RDWR|O_NONBLOCK)  = 0
connect(9, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(9)                                = 0
open("/etc/group", O_RDONLY)            = 9
fcntl64(9, F_GETFD)                     = 0
fcntl64(9, F_SETFD, FD_CLOEXEC)         = 0
_llseek(9, 0, [0], SEEK_CUR)            = 0
fstat64(9, {st_mode=S_IFREG|0644, st_size=1021, ...}) = 0
mmap2(NULL, 1021, PROT_READ, MAP_SHARED, 9, 0) = 0xb7f31000
_llseek(9, 1021, [1021], SEEK_SET)      = 0
munmap(0xb7f31000, 1021)                = 0
close(9)                                = 0
setgid32(108)                           = 0
setuid32(108)                           = 0
stat64("/usr/share/hal/fdi/preprobe", 0xbfbd8f54) = -1 EACCES (Permission denied)
stat64("/etc/hal/fdi/preprobe", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/etc/hal/fdi/preprobe", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 9
fstat64(9, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(9, F_SETFD, FD_CLOEXEC)         = 0
getdents64(9, /* 2 entries */, 4096)    = 48
getdents64(9, /* 0 entries */, 4096)    = 0
close(9)                                = 0
stat64("/usr/share/hal/fdi/information", 0xbfbd8f54) = -1 EACCES (Permission denied)
stat64("/etc/hal/fdi/information", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/etc/hal/fdi/information", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 9
fstat64(9, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(9, F_SETFD, FD_CLOEXEC)         = 0
getdents64(9, /* 2 entries */, 4096)    = 48
getdents64(9, /* 0 entries */, 4096)    = 0
close(9)                                = 0
stat64("/usr/share/hal/fdi/policy", 0xbfbd8f54) = -1 EACCES (Permission denied)
stat64("/etc/hal/fdi/policy", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
open("/etc/hal/fdi/policy", O_RDONLY|O_NONBLOCK|O_LARGEFILE|O_DIRECTORY) = 9
fstat64(9, {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
fcntl64(9, F_SETFD, FD_CLOEXEC)         = 0
getdents64(9, /* 3 entries */, 4096)    = 88
getdents64(9, /* 0 entries */, 4096)    = 0
close(9)                                = 0
stat64("/etc/hal/fdi/policy/preferences.fdi", {st_mode=S_IFREG|0644, st_size=2237, ...}) = 0
stat64("/var/cache/hald/fdi-cache", {st_mode=S_IFREG|0644, st_size=467064, ...}) = 0
gettimeofday({1190864710, 781864}, {4294966876, 0}) = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=73, ...}) = 0
write(2, "10:45:10.781 [I] mmap_cache.c:25"..., 6110:45:10.781 [I] mmap_cache.c:251: cache mtime is 1190121594
) = 61
socket(PF_FILE, SOCK_DGRAM, 0)          = 9
bind(9, {sa_family=AF_FILE, path=@/org/freedesktop/hal/udev_event}, 34) = 0
setsockopt(9, SOL_SOCKET, SO_PASSCRED, [1], 4) = 0
fstat64(9, {st_mode=S_IFSOCK|0777, st_size=0, ...}) = 0
fcntl64(9, F_GETFL)                     = 0x2 (flags O_RDWR)
open("/proc/mounts", O_RDONLY|O_LARGEFILE) = 10
fstat64(10, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
stat64("/usr/share/misc/pci.ids", 0xbfbd9d30) = -1 EACCES (Permission denied)
gettimeofday({1190864710, 783054}, {4294966876, 0}) = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=73, ...}) = 0
write(2, "10:45:10.783 [W] ids.c:294: Coul"..., 11010:45:10.783 [W] ids.c:294: Couldn't stat pci.ids file '/usr/share/misc/pci.ids', errno=13: Permission denied
) = 110
stat64("/usr/share/misc/usb.ids", 0xbfbd9d40) = -1 EACCES (Permission denied)
gettimeofday({1190864710, 783466}, {4294966876, 0}) = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=73, ...}) = 0
write(2, "10:45:10.783 [W] ids.c:515: Coul"..., 11010:45:10.783 [W] ids.c:515: Couldn't stat usb.ids file '/usr/share/misc/usb.ids', errno=13: Permission denied
) = 110
SYS_291(0x8089384, 0x4148, 0x13, 0xbfbd9dea, 0x1f) = 11
fstat64(11, {st_mode=S_IFDIR|0600, st_size=0, ...}) = 0
fcntl64(11, F_GETFL)                    = 0 (flags O_RDONLY)
SYS_292(0xb, 0x80837d6, 0x302, 0x80952a8, 0xb) = -1 EACCES (Permission denied)
gettimeofday({1190864710, 784154}, {4294966876, 0}) = 0
stat64("/etc/localtime", {st_mode=S_IFREG|0644, st_size=73, ...}) = 0
write(2, "10:45:10.784 [E] osspec.c:310: U"..., 11410:45:10.784 [E] osspec.c:310: Unable to inotify_add_watch() for '/usr/share/hal/fdi/preprobe': Permission denied
) = 114
fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 1), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f31000
write(1, "*** [DIE] osspec.c:watch_fdi_fil"..., 68*** [DIE] osspec.c:watch_fdi_files():389 : Error watching fdi files
) = 68
exit_group(1)                           = ?
Process 8576 detached

[/FONT]

---

### Post by Dardie on 2007-09-27
OK, I am being particularly obtuse today... there were no permissions for world on /usr (among other places). Now HOW that happened is mysterious, and installing squeak seems to be implicated, but that is another matter.

My Hald is now working again, and I have relearned the lesson of making sure one does not overlook the simple and obvious.

I still think that important that error reporting and failover could be way improved when important stuff like hald is not there; I will stew on that and try to contribute some effort on improving that when I have time.

---

