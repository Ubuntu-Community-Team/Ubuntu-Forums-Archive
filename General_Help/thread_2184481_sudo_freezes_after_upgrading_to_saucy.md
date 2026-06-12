---
title: "sudo freezes after upgrading to saucy"
date: 2013-10-29
forum: General Help
---

### Post by ulrichard on 2013-10-29
After upgrading my netbook to saucy, I can no longer use sudo. 
The behavior is more or less the same as in this thread : 
[http://ubuntuforums.org/showthread.php?t=2063337](http://ubuntuforums.org/showthread.php?t=2063337)

The strace seems to indicate erroneous access rights, but ls reports them to be ok, and I also set them manually again just to be sure.
```
$ ls -lh /usr/bin/sudo
-rwsr-xr-x 1 root root 121K Feb 28  2013 /usr/bin/sudo
$ id 
uid=1000(richi) gid=1000(richi) groups=1000(richi),4(adm),20(dialout),24(cdrom),27(sudo),29(audio),30(dip),46(plugdev),104(fuse),109(lpadmin),124(sambashare),140(kismet),1001(wireshark)
#id
uid=0(root) gid=0(root) groups=0(root)


$ strace /usr/bin/sudo -i
execve("/usr/bin/sudo", ["/usr/bin/sudo", "-i"], [/* 76 vars */]) = 0
brk(0)                                  = 0xb90dd000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77a1000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=212679, ...}) = 0
mmap2(NULL, 212679, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb776d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libselinux.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0 F\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=133028, ...}) = 0
mmap2(NULL, 138248, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb774b000
mmap2(0xb776b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1f000) = 0xb776b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libutil.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\220\n\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=9816, ...}) = 0
mmap2(NULL, 12428, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7747000
mmap2(0xb7749000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0xb7749000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libdl.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320\n\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=13856, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7746000
mmap2(NULL, 16512, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7741000
mmap2(0xb7744000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0xb7744000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`\232\1\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=1779492, ...}) = 0
mmap2(NULL, 1784604, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb758d000
mmap2(0xb773b000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1ae000) = 0xb773b000
mmap2(0xb773e000, 11036, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb773e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libpcre.so.3", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\240\21\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=263628, ...}) = 0
mmap2(NULL, 262288, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb754c000
mmap2(0xb758b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x3f000) = 0xb758b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libpthread.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\320[\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0755, st_size=125343, ...}) = 0
mmap2(NULL, 107008, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7531000
mmap2(0xb7548000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16000) = 0xb7548000
mmap2(0xb754a000, 4608, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb754a000
close(3)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7530000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb752f000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb752f740, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb773b000, 8192, PROT_READ)   = 0
mprotect(0xb7548000, 4096, PROT_READ)   = 0
mprotect(0xb758b000, 4096, PROT_READ)   = 0
mprotect(0xb7744000, 4096, PROT_READ)   = 0
mprotect(0xb7749000, 4096, PROT_READ)   = 0
mprotect(0xb776b000, 4096, PROT_READ)   = 0
mprotect(0xb77e3000, 4096, PROT_READ)   = 0
mprotect(0xb77c4000, 4096, PROT_READ)   = 0
munmap(0xb776d000, 212679)              = 0
set_tid_address(0xb752f7a8)             = 7465
set_robust_list(0xb752f7b0, 12)         = 0
futex(0xbfc16c94, FUTEX_WAIT_BITSET_PRIVATE|FUTEX_CLOCK_REALTIME, 1, NULL, b752f740) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGRTMIN, {0xb75365f0, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb7536680, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
uname({sys="Linux", node="onenc", ...}) = 0
statfs64("/sys/fs/selinux", 84, 0xbfc16e3c) = -1 ENOENT (No such file or directory)
statfs64("/selinux", 84, 0xbfc16e3c)    = -1 ENOENT (No such file or directory)
brk(0)                                  = 0xb90dd000
brk(0xb90fe000)                         = 0xb90fe000
open("/proc/filesystems", O_RDONLY|O_LARGEFILE) = 3
fstat64(3, {st_mode=S_IFREG|0444, st_size=0, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77a0000
read(3, "nodev\tsysfs\nnodev\trootfs\nnodev\tb"..., 1024) = 328
read(3, "", 1024)                       = 0
close(3)                                = 0
munmap(0xb77a0000, 4096)                = 0
open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=4464144, ...}) = 0
mmap2(NULL, 2097152, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb732f000
mmap2(NULL, 1253376, PROT_READ, MAP_PRIVATE, 3, 0x18a000) = 0xb71fd000
close(3)                                = 0
open("/usr/lib/locale/locale-archive", O_RDONLY|O_LARGEFILE|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=4464144, ...}) = 0
mmap2(NULL, 262144, PROT_READ, MAP_PRIVATE, 3, 0x2bd000) = 0xb71bd000
mmap2(NULL, 4096, PROT_READ, MAP_PRIVATE, 3, 0x43a000) = 0xb77a0000
close(3)                                = 0
geteuid32()                             = 1000
stat64("/usr/bin/sudo", {st_mode=S_IFREG|0755, st_size=123360, ...}) = 0
open("/usr/share/locale/locale.alias", O_RDONLY|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=2570, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb779f000
read(3, "# Locale name alias data base.\n#"..., 4096) = 2570
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb779f000, 4096)                = 0
open("/usr/share/locale/en/LC_MESSAGES/sudo.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
open("/usr/share/locale-langpack/en/LC_MESSAGES/sudo.mo", O_RDONLY) = -1 ENOENT (No such file or directory)
write(2, "sudo", 4sudo)                     = 4
write(2, ": ", 2: )                       = 2[B]
write(2, "/usr/bin/sudo must be owned by u"..., 64/usr/bin/sudo must be owned by uid 0 and have the setuid bit set) = 64[/B]
write(2, "\n", 1
)                       = 1
close(0)                                = 0
access("/var/run/utmpx", F_OK)          = -1 ENOENT (No such file or directory)
open("/var/run/utmp", O_RDONLY|O_LARGEFILE|O_CLOEXEC) = 0
_llseek(0, 0, [0], SEEK_SET)            = 0
alarm(0)                                = 0
rt_sigaction(SIGALRM, {0xb76b6300, [], 0}, {SIG_DFL, [], 0}, 8) = 0
alarm(10)                               = 0
fcntl64(0, F_SETLKW, {type=F_RDLCK, whence=SEEK_SET, start=0, len=0}) = 0
read(0, "\2\0\0\0\0\0\0\0~\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\1\0\0\0002\0\0\0~\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\6\0\0\0\n\4\0\0tty4\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\6\0\0\0\20\4\0\0tty5\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\6\0\0\0%\4\0\0tty2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\6\0\0\0&\4\0\0tty3\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\7\0\0\0\317\t\0\0tty6\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\7\0\0\0\274\10\0\0tty7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\6\0\0\0\240\10\0\0tty1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\7\0\0\0\6\n\0\0pts/0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\10\0\0\0\332\n\0\0pts/12\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\7\0\0\0s\v\0\0pts/6\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\7\0\0\0w\v\0\0pts/4\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\7\0\0\0\177\v\0\0pts/8\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\7\0\0\0\206\v\0\0pts/13\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\7\0\0\0\215\v\0\0pts/14\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\7\0\0\0\221\v\0\0pts/16\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\7\0\0\0\225\v\0\0pts/17\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\7\0\0\0\232\v\0\0pts/18\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "\10\0\0\0\332\n\0\0pts/3\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(0, "", 384)                        = 0
fcntl64(0, F_SETLKW, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0}) = 0
alarm(0)                                = 10
rt_sigaction(SIGALRM, {SIG_DFL, [], 0}, NULL, 8) = 0
exit_group(1)                           = ?
+++ exited with 1 +++
```

---

### Post by ulrichard on 2013-11-12
Now this is strange:

if I try to use sudo, it freezes as stated in the initial post. It doesn't ask for a password, and characters typed are echoed.
Now if I use gksudo instead, a password query dialog pops up, and after entering the password, the requested process starts with root privileges.
After that, as long as the password is in the cache, sudo also works for that terminal window.
So, the problem has to be with the password query somehow.

---

### Post by ulrichard on 2013-12-10
I installed ubuntu freshly on my new ultrabook, and I get the exact same behavior. 
What might have an influence is that I installed it with two factor authenification full disk encryption according to this recipe:
[https://blog.kumina.nl/2010/07/two-factor-luks-using-ubuntu/](https://blog.kumina.nl/2010/07/two-factor-luks-using-ubuntu/)

Although I don't see why this should be the reason, it's the best guess that I have at the moment.

---

