---
title: "aa-notify consumes more than 3/4 of RAM"
date: 2015-03-21
forum: General Help
---

### Post by obake2 on 2015-03-21
Hello everyone. Long time no see~! Wohooo!  Ah, never mind. Just remembered that my account name is different now :( And the ol' pals from 10 years ago are gone.

Anyways. So I'm currently running Ubuntu 14.04 Gnome 64-bit, and every time I boot the laptop becomes extremely slow due to RAM being full. I though the culprit was Firefox but I noticed it was a process called "aa-notify" that is consuming more than 80% of my RAM. Did you guys experience this before? 

Apparently [aa-notify]("http://manpages.ubuntu.com/manpages/trusty/man8/aa-notify.8.html") is a message displayer for AppArmor. I don't know why it is consuming so much ram that I either have to kill the process or restart X. Do you guys know a fix or work around?

Thank you all.

---

### Post by matt_symes on 2015-03-21
Hi

I'm using Xubuntu and not Ubuntu at the moment but nothing is dependent upon apparmor-notify. 

```
matthew-laptop:/home/matthew:1 % apt-file search aa-notify                   
apparmor-notify: /usr/bin/aa-notify
apparmor-notify: /usr/share/man/man8/aa-notify.8.gz
matthew-laptop:/home/matthew:1 % acde apparmor-notify && acrd apparmor-notify
apparmor-notify
  Depends: libapparmor-perl
  Depends: perl
  Suggests: libnotify-bin
apparmor-notify
Reverse Depends:
matthew-laptop:/home/matthew:1 %
```

So you could try removing it. If that then causes problems then you could reinstall it.

Obviously this is a workaround so you could try to ```
strace
``` the aa-notify process to see what it is doing. Also look for bug reports on Launchpad to see if others are having the same problem.

I would also check the logs to see if apparmor is configured correctly.

Kind regards

---

### Post by obake2 on 2015-03-22
Hey. Thank you Matt for the reply. Here is the result of strace.
I have also attached a screenshot of System Monior showing that aa-notify occupies a great amount of RAM.

```
:~$ strace aa-notify
execve("/usr/bin/aa-notify", ["aa-notify"], [/* 54 vars */]) = 0
brk(0)                                  = 0x986000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f93cdfe7000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=162616, ...}) = 0
mmap(NULL, 162616, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f93cdfbf000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/libperl.so.5.18", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 \231\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1608280, ...}) = 0
mmap(NULL, 3703944, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f93cda3e000
mprotect(0x7f93cdbbe000, 2093056, PROT_NONE) = 0
mmap(0x7f93cddbd000, 40960, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x17f000) = 0x7f93cddbd000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\37\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=1840928, ...}) = 0
mmap(NULL, 3949248, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f93cd679000
mprotect(0x7f93cd834000, 2093056, PROT_NONE) = 0
mmap(0x7f93cda33000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1ba000) = 0x7f93cda33000
mmap(0x7f93cda39000, 17088, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f93cda39000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libdl.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\320\16\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=14664, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f93cdfbe000
mmap(NULL, 2109744, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f93cd475000
mprotect(0x7f93cd478000, 2093056, PROT_NONE) = 0
mmap(0x7f93cd677000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f93cd677000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libm.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20V\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1071552, ...}) = 0
mmap(NULL, 3166568, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f93cd16f000
mprotect(0x7f93cd274000, 2093056, PROT_NONE) = 0
mmap(0x7f93cd473000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x104000) = 0x7f93cd473000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libpthread.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0po\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=141574, ...}) = 0
mmap(NULL, 2217264, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f93ccf51000
mprotect(0x7f93ccf6a000, 2093056, PROT_NONE) = 0
mmap(0x7f93cd169000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x18000) = 0x7f93cd169000
mmap(0x7f93cd16b000, 13616, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f93cd16b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libcrypt.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\f\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=43368, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f93cdfbd000
mmap(NULL, 2327072, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f93ccd18000
mprotect(0x7f93ccd21000, 2097152, PROT_NONE) = 0
mmap(0x7f93ccf21000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9000) = 0x7f93ccf21000
mmap(0x7f93ccf23000, 184864, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f93ccf23000
close(3)                                = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f93cdfbc000
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f93cdfba000
arch_prctl(ARCH_SET_FS, 0x7f93cdfba740) = 0
mprotect(0x7f93cda33000, 16384, PROT_READ) = 0
mprotect(0x7f93ccf21000, 4096, PROT_READ) = 0
mprotect(0x7f93cd169000, 4096, PROT_READ) = 0
mprotect(0x7f93cd473000, 4096, PROT_READ) = 0
mprotect(0x7f93cd677000, 4096, PROT_READ) = 0
mprotect(0x7f93cddbd000, 20480, PROT_READ) = 0
mprotect(0x601000, 4096, PROT_READ)     = 0
mprotect(0x7f93cdfe9000, 4096, PROT_READ) = 0
munmap(0x7f93cdfbf000, 162616)          = 0
set_tid_address(0x7f93cdfbaa10)         = 5416
set_robust_list(0x7f93cdfbaa20, 24)     = 0
futex(0x7fff1d768d10, FUTEX_WAIT_BITSET_PRIVATE|FUTEX_CLOCK_REALTIME, 1, NULL, 7f93cdfba740) = -1 EAGAIN (Resource temporarily unavailable)
rt_sigaction(SIGRTMIN, {0x7f93ccf579f0, [], SA_RESTORER|SA_SIGINFO, 0x7f93ccf61340}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0x7f93ccf57a80, [], SA_RESTORER|SA_RESTART|SA_SIGINFO, 0x7f93ccf61340}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM64_INFINITY}) = 0
rt_sigaction(SIGFPE, {SIG_IGN, [FPE], SA_RESTORER|SA_RESTART, 0x7f93cd6afd40}, {SIG_DFL, [], 0}, 8) = 0
brk(0)                                  = 0x986000
brk(0x9a7000)                           = 0x9a7000
getuid()                                = 1000
geteuid()                               = 1000
getgid()                                = 1000
getegid()                               = 1000
open("/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=7216688, ...}) = 0
mmap(NULL, 7216688, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f93cc636000
close(3)                                = 0
open("/dev/urandom", O_RDONLY)          = 3
read(3, "P4n\23", 4)                    = 4
close(3)                                = 0
readlink("/proc/self/exe", "/usr/bin/perl", 4095) = 13
stat("/usr/local/lib/site_perl/5.18.2/x86_64-linux-gnu-thread-multi", 0x7fff1d7688f0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/site_perl/5.18.2", 0x7fff1d7688f0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/site_perl/x86_64-linux-gnu-thread-multi", 0x7fff1d7688f0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.1", 0x7fff1d768b10) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.1", 0x7fff1d768b10) = -1 ENOENT (No such file or directory)
getuid()                                = 1000
geteuid()                               = 1000
getgid()                                = 1000
getegid()                               = 1000
ioctl(0, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
lseek(0, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
ioctl(1, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
lseek(1, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
ioctl(2, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
lseek(2, 0, SEEK_CUR)                   = -1 ESPIPE (Illegal seek)
open("/usr/bin/aa-notify", O_RDONLY)    = 3
ioctl(3, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d7687b0) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(3, 0, SEEK_CUR)                   = 0
fcntl(3, F_SETFD, FD_CLOEXEC)           = 0
fstat(3, {st_mode=S_IFREG|0755, st_size=19771, ...}) = 0
getuid()                                = 1000
geteuid()                               = 1000
getgid()                                = 1000
getegid()                               = 1000
rt_sigaction(SIGCHLD, NULL, {SIG_DFL, [], 0}, 8) = 0
brk(0x9c8000)                           = 0x9c8000
read(3, "#!/usr/bin/perl\n# --------------"..., 8192) = 8192
stat("/etc/perl/strict.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/etc/perl/strict.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/strict.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/strict.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/strict.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/strict.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/strict.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/strict.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/strict.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/strict.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/strict.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/strict.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/strict.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/strict.pm", {st_mode=S_IFREG|0644, st_size=1006, ...}) = 0
open("/usr/share/perl/5.18/strict.pm", O_RDONLY) = 4
ioctl(4, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d7680b0) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(4, 0, SEEK_CUR)                   = 0
read(4, "package strict;\n\n$strict::VERSIO"..., 8192) = 1006
lseek(4, 1005, SEEK_SET)                = 1005
lseek(4, 0, SEEK_CUR)                   = 1005
close(4)                                = 0
stat("/etc/perl/warnings.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/etc/perl/warnings.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/warnings.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/warnings.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/warnings.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/warnings.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/warnings.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/warnings.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/warnings.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/warnings.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/warnings.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/warnings.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/warnings.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/warnings.pm", {st_mode=S_IFREG|0644, st_size=16923, ...}) = 0
open("/usr/share/perl/5.18/warnings.pm", O_RDONLY) = 4
ioctl(4, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d7680b0) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(4, 0, SEEK_CUR)                   = 0
read(4, "# -*- buffer-read-only: t -*-\n# "..., 8192) = 8192
brk(0x9ea000)                           = 0x9ea000
read(4, "\\x00\\x02\\x00\\x00\\x00\\x00\\x00\\x00"..., 8192) = 8192
brk(0xa0b000)                           = 0xa0b000
read(4, "T);\n\t    vec($DeadBits{'all'}, $"..., 8192) = 539
read(4, "", 8192)                       = 0
close(4)                                = 0
stat("/etc/perl/Getopt/Long.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/etc/perl/Getopt/Long.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Getopt/Long.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Getopt/Long.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Getopt/Long.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Getopt/Long.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Getopt/Long.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Getopt/Long.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Getopt/Long.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Getopt/Long.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Getopt/Long.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Getopt/Long.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/Getopt/Long.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/Getopt/Long.pm", {st_mode=S_IFREG|0644, st_size=41332, ...}) = 0
open("/usr/share/perl/5.18/Getopt/Long.pm", O_RDONLY) = 4
ioctl(4, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d7680b0) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(4, 0, SEEK_CUR)                   = 0
read(4, "#! perl\n\n# Getopt::Long.pm -- Un"..., 8192) = 8192
stat("/etc/perl/vars.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/etc/perl/vars.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/vars.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/vars.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/vars.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/vars.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/vars.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/vars.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/vars.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/vars.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/vars.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/vars.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/vars.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/vars.pm", {st_mode=S_IFREG|0644, st_size=1149, ...}) = 0
open("/usr/share/perl/5.18/vars.pm", O_RDONLY) = 5
ioctl(5, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d767a70) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(5, 0, SEEK_CUR)                   = 0
read(5, "package vars;\n\nuse 5.006;\n\nour $"..., 8192) = 1149
stat("/etc/perl/warnings/register.pmc", 0x7fff1d767720) = -1 ENOENT (No such file or directory)
stat("/etc/perl/warnings/register.pm", 0x7fff1d767670) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/warnings/register.pmc", 0x7fff1d767720) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/warnings/register.pm", 0x7fff1d767670) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/warnings/register.pmc", 0x7fff1d767720) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/warnings/register.pm", 0x7fff1d767670) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/warnings/register.pmc", 0x7fff1d767720) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/warnings/register.pm", 0x7fff1d767670) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/warnings/register.pmc", 0x7fff1d767720) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/warnings/register.pm", 0x7fff1d767670) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/warnings/register.pmc", 0x7fff1d767720) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/warnings/register.pm", 0x7fff1d767670) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/warnings/register.pmc", 0x7fff1d767720) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/warnings/register.pm", {st_mode=S_IFREG|0644, st_size=481, ...}) = 0
open("/usr/share/perl/5.18/warnings/register.pm", O_RDONLY) = 6
ioctl(6, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d767430) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(6, 0, SEEK_CUR)                   = 0
read(6, "package warnings::register;\n\nour"..., 8192) = 481
read(6, "", 8192)                       = 0
close(6)                                = 0
lseek(5, 1148, SEEK_SET)                = 1148
lseek(5, 0, SEEK_CUR)                   = 1148
close(5)                                = 0
stat("/etc/perl/Exporter.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/etc/perl/Exporter.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Exporter.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Exporter.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Exporter.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Exporter.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Exporter.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Exporter.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Exporter.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Exporter.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Exporter.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Exporter.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/Exporter.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/Exporter.pm", {st_mode=S_IFREG|0644, st_size=2367, ...}) = 0
open("/usr/share/perl/5.18/Exporter.pm", O_RDONLY) = 5
ioctl(5, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d767a70) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(5, 0, SEEK_CUR)                   = 0
read(5, "package Exporter;\n\nrequire 5.006"..., 8192) = 2367
brk(0xa2c000)                           = 0xa2c000
lseek(5, 2366, SEEK_SET)                = 2366
lseek(5, 0, SEEK_CUR)                   = 2366
close(5)                                = 0
stat("/etc/perl/constant.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/etc/perl/constant.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/constant.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/constant.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/constant.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/constant.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/constant.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/constant.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/constant.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/constant.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/constant.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/constant.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/constant.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/constant.pm", {st_mode=S_IFREG|0644, st_size=4532, ...}) = 0
open("/usr/share/perl/5.18/constant.pm", O_RDONLY) = 5
ioctl(5, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d767a70) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(5, 0, SEEK_CUR)                   = 0
brk(0xa4d000)                           = 0xa4d000
read(5, "package constant;\nuse 5.008;\nuse"..., 8192) = 4532
lseek(5, 4531, SEEK_SET)                = 4531
lseek(5, 0, SEEK_CUR)                   = 4531
close(5)                                = 0
read(4, "t,\",\n\t   \"order=$order,\",\n\t   \"\\"..., 8192) = 8192
brk(0xa6e000)                           = 0xa6e000
read(4, "l $@;\n\t\t\t    local $SIG{__DIE__}"..., 8192) = 8192
brk(0xa92000)                           = 0xa92000
brk(0xab3000)                           = 0xab3000
read(4, "Option lookup.\nsub FindOption ($"..., 8192) = 8192
brk(0xad5000)                           = 0xad5000
read(4, "k.\n\t\tunshift (@$argv, defined $r"..., 8192) = 8192
brk(0xaf7000)                           = 0xaf7000
read(4, "rsion = $_[1];\n    shift->SUPER:"..., 8192) = 372
stat("/etc/perl/overload.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/etc/perl/overload.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/overload.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/overload.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/overload.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/overload.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/overload.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/overload.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/overload.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/overload.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/overload.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/overload.pm", 0x7fff1d767cb0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/overload.pmc", 0x7fff1d767d60) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/overload.pm", {st_mode=S_IFREG|0644, st_size=4462, ...}) = 0
open("/usr/share/perl/5.18/overload.pm", O_RDONLY) = 5
ioctl(5, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d767a70) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(5, 0, SEEK_CUR)                   = 0
read(5, "package overload;\n\nour $VERSION "..., 8192) = 4462
brk(0xb18000)                           = 0xb18000
stat("/etc/perl/overloading.pmc", 0x7fff1d767720) = -1 ENOENT (No such file or directory)
stat("/etc/perl/overloading.pm", 0x7fff1d767670) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/overloading.pmc", 0x7fff1d767720) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/overloading.pm", 0x7fff1d767670) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/overloading.pmc", 0x7fff1d767720) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/overloading.pm", 0x7fff1d767670) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/overloading.pmc", 0x7fff1d767720) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/overloading.pm", 0x7fff1d767670) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/overloading.pmc", 0x7fff1d767720) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/overloading.pm", 0x7fff1d767670) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/overloading.pmc", 0x7fff1d767720) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/overloading.pm", 0x7fff1d767670) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/overloading.pmc", 0x7fff1d767720) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/overloading.pm", {st_mode=S_IFREG|0644, st_size=964, ...}) = 0
open("/usr/share/perl/5.18/overloading.pm", O_RDONLY) = 6
ioctl(6, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d767430) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(6, 0, SEEK_CUR)                   = 0
read(6, "package overloading;\nuse warning"..., 8192) = 964
lseek(6, 963, SEEK_SET)                 = 963
lseek(6, 0, SEEK_CUR)                   = 963
close(6)                                = 0
lseek(5, 4461, SEEK_SET)                = 4461
lseek(5, 0, SEEK_CUR)                   = 4461
close(5)                                = 0
read(4, "", 8192)                       = 0
close(4)                                = 0
getuid()                                = 1000
geteuid()                               = 1000
getgid()                                = 1000
getegid()                               = 1000
stat("/etc/perl/Exporter/Heavy.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/etc/perl/Exporter/Heavy.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Exporter/Heavy.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Exporter/Heavy.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Exporter/Heavy.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Exporter/Heavy.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Exporter/Heavy.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Exporter/Heavy.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Exporter/Heavy.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Exporter/Heavy.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Exporter/Heavy.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Exporter/Heavy.pm", 0x7fff1d7682f0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/Exporter/Heavy.pmc", 0x7fff1d7683a0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/Exporter/Heavy.pm", {st_mode=S_IFREG|0644, st_size=6233, ...}) = 0
open("/usr/share/perl/5.18/Exporter/Heavy.pm", O_RDONLY) = 4
ioctl(4, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d7680b0) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(4, 0, SEEK_CUR)                   = 0
read(4, "package Exporter::Heavy;\n\nuse st"..., 8192) = 6233
brk(0xb3c000)                           = 0xb3c000
read(4, "", 8192)                       = 0
close(4)                                = 0
brk(0xb5f000)                           = 0xb5f000
read(3, " \"Profile: $profile\\n\";\n    defi"..., 8192) = 8192
brk(0xb80000)                           = 0xb80000
brk(0xba2000)                           = 0xba2000
read(3, "al::timelocal($sec, $min, $hour,"..., 8192) = 3387
read(3, "", 8192)                       = 0
close(3)                                = 0
stat("/etc/perl/LibAppArmor.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/etc/perl/LibAppArmor.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/LibAppArmor.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/LibAppArmor.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/LibAppArmor.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/LibAppArmor.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/LibAppArmor.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/LibAppArmor.pm", {st_mode=S_IFREG|0644, st_size=8373, ...}) = 0
open("/usr/lib/perl5/LibAppArmor.pm", O_RDONLY) = 3
ioctl(3, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d768790) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(3, 0, SEEK_CUR)                   = 0
read(3, "# This file was automatically ge"..., 8192) = 8192
stat("/etc/perl/base.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/etc/perl/base.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/base.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/base.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/base.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/base.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/base.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/base.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/base.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/base.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/base.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/base.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/base.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/base.pm", {st_mode=S_IFREG|0644, st_size=4479, ...}) = 0
open("/usr/share/perl/5.18/base.pm", O_RDONLY) = 4
ioctl(4, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d768150) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(4, 0, SEEK_CUR)                   = 0
read(4, "package base;\n\nuse strict 'vars'"..., 8192) = 4479
brk(0xbc3000)                           = 0xbc3000
lseek(4, 4478, SEEK_SET)                = 4478
lseek(4, 0, SEEK_CUR)                   = 4478
close(4)                                = 0
stat("/etc/perl/DynaLoader.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/etc/perl/DynaLoader.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/DynaLoader.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/DynaLoader.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/DynaLoader.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/DynaLoader.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/DynaLoader.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/DynaLoader.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/DynaLoader.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/DynaLoader.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/DynaLoader.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/DynaLoader.pm", {st_mode=S_IFREG|0644, st_size=10643, ...}) = 0
open("/usr/lib/perl/5.18/DynaLoader.pm", O_RDONLY) = 4
ioctl(4, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d768150) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(4, 0, SEEK_CUR)                   = 0
read(4, "# Generated from DynaLoader_pm.P"..., 8192) = 8192
stat("/etc/perl/Config.pmc", 0x7fff1d767e00) = -1 ENOENT (No such file or directory)
stat("/etc/perl/Config.pm", 0x7fff1d767d50) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Config.pmc", 0x7fff1d767e00) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Config.pm", 0x7fff1d767d50) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Config.pmc", 0x7fff1d767e00) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Config.pm", 0x7fff1d767d50) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Config.pmc", 0x7fff1d767e00) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Config.pm", 0x7fff1d767d50) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Config.pmc", 0x7fff1d767e00) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Config.pm", 0x7fff1d767d50) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Config.pmc", 0x7fff1d767e00) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Config.pm", {st_mode=S_IFREG|0644, st_size=3216, ...}) = 0
open("/usr/lib/perl/5.18/Config.pm", O_RDONLY) = 5
ioctl(5, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d767b10) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(5, 0, SEEK_CUR)                   = 0
read(5, "# This file was created by confi"..., 8192) = 3216
brk(0xbe5000)                           = 0xbe5000
read(5, "", 8192)                       = 0
close(5)                                = 0
read(4, "enames to look for\n        if (m"..., 8192) = 2451
brk(0xc06000)                           = 0xc06000
lseek(4, 10642, SEEK_SET)               = 10642
lseek(4, 0, SEEK_CUR)                   = 10642
close(4)                                = 0
read(3, "rc::AA_RECORD_ALLOWED;\n*AA_RECOR"..., 8192) = 181
read(3, "", 8192)                       = 0
close(3)                                = 0
stat("/etc/perl/auto/LibAppArmor", 0x986280) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/auto/LibAppArmor", 0x986280) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/auto/LibAppArmor", 0x986280) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/auto/LibAppArmor", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/usr/lib/perl5/auto/LibAppArmor/LibAppArmor.so", {st_mode=S_IFREG|0644, st_size=114400, ...}) = 0
stat("/usr/lib/perl5/auto/LibAppArmor/LibAppArmor.bs", {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
futex(0x7f93cd6780d0, FUTEX_WAKE_PRIVATE, 2147483647) = 0
open("/usr/lib/perl5/auto/LibAppArmor/LibAppArmor.so", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\360F\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=114400, ...}) = 0
mmap(NULL, 2209672, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f93cc41a000
mprotect(0x7f93cc434000, 2097152, PROT_NONE) = 0
mmap(0x7f93cc634000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1a000) = 0x7f93cc634000
close(3)                                = 0
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=162616, ...}) = 0
mmap(NULL, 162616, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f93cdfbf000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/usr/lib/x86_64-linux-gnu/libapparmor.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\300\30\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=47984, ...}) = 0
mmap(NULL, 2143152, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f93cc20e000
mprotect(0x7f93cc219000, 2093056, PROT_NONE) = 0
mmap(0x7f93cc418000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa000) = 0x7f93cc418000
close(3)                                = 0
mprotect(0x7f93cc418000, 4096, PROT_READ) = 0
mprotect(0x7f93cc634000, 4096, PROT_READ) = 0
munmap(0x7f93cdfbf000, 162616)          = 0
brk(0xc27000)                           = 0xc27000
getuid()                                = 1000
geteuid()                               = 1000
getgid()                                = 1000
getegid()                               = 1000
stat("/etc/perl/POSIX.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/etc/perl/POSIX.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/POSIX.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/POSIX.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/POSIX.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/POSIX.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/POSIX.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/POSIX.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/POSIX.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/POSIX.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/POSIX.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/POSIX.pm", {st_mode=S_IFREG|0644, st_size=16637, ...}) = 0
open("/usr/lib/perl/5.18/POSIX.pm", O_RDONLY) = 3
ioctl(3, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d768790) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(3, 0, SEEK_CUR)                   = 0
read(3, "package POSIX;\nuse strict;\nuse w"..., 8192) = 8192
stat("/etc/perl/Fcntl.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/etc/perl/Fcntl.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Fcntl.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Fcntl.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Fcntl.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Fcntl.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Fcntl.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Fcntl.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Fcntl.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Fcntl.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Fcntl.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Fcntl.pm", {st_mode=S_IFREG|0644, st_size=2036, ...}) = 0
open("/usr/lib/perl/5.18/Fcntl.pm", O_RDONLY) = 4
ioctl(4, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d768150) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(4, 0, SEEK_CUR)                   = 0
read(4, "package Fcntl;\n\nuse strict;\nour("..., 8192) = 2036
read(4, "", 8192)                       = 0
close(4)                                = 0
stat("/etc/perl/XSLoader.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/etc/perl/XSLoader.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/XSLoader.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/XSLoader.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/XSLoader.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/XSLoader.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/XSLoader.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/XSLoader.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/XSLoader.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/XSLoader.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/XSLoader.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/XSLoader.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/XSLoader.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/XSLoader.pm", {st_mode=S_IFREG|0644, st_size=2886, ...}) = 0
open("/usr/share/perl/5.18/XSLoader.pm", O_RDONLY) = 4
ioctl(4, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d768150) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(4, 0, SEEK_CUR)                   = 0
read(4, "# Generated from XSLoader.pm.PL "..., 8192) = 2886
lseek(4, 2885, SEEK_SET)                = 2885
lseek(4, 0, SEEK_CUR)                   = 2885
close(4)                                = 0
getuid()                                = 1000
geteuid()                               = 1000
getgid()                                = 1000
getegid()                               = 1000
stat("/usr/lib/perl/5.18/auto/Fcntl/Fcntl.bs", {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
stat("/usr/lib/perl/5.18/auto/Fcntl/Fcntl.so", {st_mode=S_IFREG|0644, st_size=18632, ...}) = 0
stat("/usr/lib/perl/5.18/auto/Fcntl/Fcntl.bs", {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
open("/usr/lib/perl/5.18/auto/Fcntl/Fcntl.so", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\20\33\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=18632, ...}) = 0
mmap(NULL, 2113800, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7f93cc009000
mprotect(0x7f93cc00c000, 2097152, PROT_NONE) = 0
mmap(0x7f93cc20c000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x3000) = 0x7f93cc20c000
close(4)                                = 0
mprotect(0x7f93cc20c000, 4096, PROT_READ) = 0
brk(0xc49000)                           = 0xc49000
read(3, "\t\tEAGAIN EALREADY EBADF EBUSY EC"..., 8192) = 8192
brk(0xc6c000)                           = 0xc6c000
read(3, "ub DELETE { delete $SIG{ &_check"..., 8192) = 253
read(3, "", 8192)                       = 0
close(3)                                = 0
stat("/usr/lib/perl/5.18/auto/POSIX/POSIX.bs", {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
stat("/usr/lib/perl/5.18/auto/POSIX/POSIX.so", {st_mode=S_IFREG|0644, st_size=85232, ...}) = 0
stat("/usr/lib/perl/5.18/auto/POSIX/POSIX.bs", {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
open("/usr/lib/perl/5.18/auto/POSIX/POSIX.so", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\0Z\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=85232, ...}) = 0
mmap(NULL, 2180400, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f93cbdf4000
mprotect(0x7f93cbe06000, 2093056, PROT_NONE) = 0
mmap(0x7f93cc005000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x11000) = 0x7f93cc005000
close(3)                                = 0
mprotect(0x7f93cc005000, 12288, PROT_READ) = 0
brk(0xc8d000)                           = 0xc8d000
stat("/etc/perl/Tie/Hash.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/etc/perl/Tie/Hash.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Tie/Hash.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Tie/Hash.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Tie/Hash.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Tie/Hash.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Tie/Hash.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Tie/Hash.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Tie/Hash.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Tie/Hash.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Tie/Hash.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Tie/Hash.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/Tie/Hash.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/Tie/Hash.pm", {st_mode=S_IFREG|0644, st_size=2037, ...}) = 0
open("/usr/share/perl/5.18/Tie/Hash.pm", O_RDONLY) = 3
ioctl(3, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d768790) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(3, 0, SEEK_CUR)                   = 0
read(3, "package Tie::Hash;\n\nour $VERSION"..., 8192) = 2037
brk(0xcae000)                           = 0xcae000
stat("/etc/perl/Carp.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/etc/perl/Carp.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Carp.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Carp.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Carp.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Carp.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Carp.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Carp.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Carp.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Carp.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Carp.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Carp.pm", 0x7fff1d768390) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/Carp.pmc", 0x7fff1d768440) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/Carp.pm", {st_mode=S_IFREG|0644, st_size=13752, ...}) = 0
open("/usr/share/perl/5.18/Carp.pm", O_RDONLY) = 4
ioctl(4, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d768150) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(4, 0, SEEK_CUR)                   = 0
read(4, "package Carp;\n\n{ use 5.006; }\nus"..., 8192) = 8192
brk(0xccf000)                           = 0xccf000
read(4, "           # This *shouldn't* ha"..., 8192) = 5560
lseek(4, 13751, SEEK_SET)               = 13751
lseek(4, 0, SEEK_CUR)                   = 13751
close(4)                                = 0
getuid()                                = 1000
geteuid()                               = 1000
getgid()                                = 1000
getegid()                               = 1000
brk(0xcf0000)                           = 0xcf0000
read(3, "", 8192)                       = 0
close(3)                                = 0
getuid()                                = 1000
geteuid()                               = 1000
getgid()                                = 1000
getegid()                               = 1000
stat("/etc/perl/Time/Local.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/etc/perl/Time/Local.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Time/Local.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/Time/Local.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Time/Local.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/Time/Local.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Time/Local.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/Time/Local.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Time/Local.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/Time/Local.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Time/Local.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/Time/Local.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/Time/Local.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/Time/Local.pm", {st_mode=S_IFREG|0644, st_size=12092, ...}) = 0
open("/usr/share/perl/5.18/Time/Local.pm", O_RDONLY) = 3
ioctl(3, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d768790) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(3, 0, SEEK_CUR)                   = 0
read(3, "package Time::Local;\n\nrequire Ex"..., 8192) = 8192
lseek(3, 5199, SEEK_SET)                = 5199
lseek(3, 0, SEEK_CUR)                   = 5199
close(3)                                = 0
getuid()                                = 1000
geteuid()                               = 1000
getgid()                                = 1000
getegid()                               = 1000
open("/etc/localtime", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2819, ...}) = 0
fstat(3, {st_mode=S_IFREG|0644, st_size=2819, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f93cdfe6000
read(3, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\4\0\0\0\4\0\0\0\0"..., 4096) = 2819
lseek(3, -1802, SEEK_CUR)               = 1017
read(3, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\5\0\0\0\5\0\0\0\0"..., 4096) = 1802
close(3)                                = 0
munmap(0x7f93cdfe6000, 4096)            = 0
stat("/etc/perl/File/Basename.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/etc/perl/File/Basename.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/File/Basename.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/local/lib/perl/5.18.2/File/Basename.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/File/Basename.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/local/share/perl/5.18.2/File/Basename.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/File/Basename.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl5/File/Basename.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/File/Basename.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl5/File/Basename.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/File/Basename.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/lib/perl/5.18/File/Basename.pm", 0x7fff1d7689d0) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/File/Basename.pmc", 0x7fff1d768a80) = -1 ENOENT (No such file or directory)
stat("/usr/share/perl/5.18/File/Basename.pm", {st_mode=S_IFREG|0644, st_size=11250, ...}) = 0
open("/usr/share/perl/5.18/File/Basename.pm", O_RDONLY) = 3
ioctl(3, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d768790) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(3, 0, SEEK_CUR)                   = 0
read(3, "=head1 NAME\n\nFile::Basename - Pa"..., 8192) = 8192
brk(0xd12000)                           = 0xd12000
read(3, "urn 'foo/'\n    dirname(\"foo/\");\n"..., 8192) = 3058
read(3, "", 8192)                       = 0
close(3)                                = 0
getuid()                                = 1000
geteuid()                               = 1000
getgid()                                = 1000
getegid()                               = 1000
geteuid()                               = 1000
getuid()                                = 1000
getegid()                               = 1000
getgroups(0, NULL)                      = 9
getgroups(9, [4, 24, 27, 30, 46, 105, 108, 125, 1000]) = 9
getgid()                                = 1000
getgroups(0, NULL)                      = 9
getgroups(9, [4, 24, 27, 30, 46, 105, 108, 125, 1000]) = 9
geteuid()                               = 1000
stat("/var/run/auditd.pid", 0x986280)   = -1 ENOENT (No such file or directory)
stat("/var/log/kern.log", {st_mode=S_IFREG|0640, st_size=60330056998, ...}) = 0
geteuid()                               = 1000
geteuid()                               = 1000
getegid()                               = 1000
getgroups(0, NULL)                      = 9
getgroups(9, [4, 24, 27, 30, 46, 105, 108, 125, 1000]) = 9
stat("/var/log", {st_mode=S_IFDIR|0775, st_size=4096, ...}) = 0
geteuid()                               = 1000
geteuid()                               = 1000
getegid()                               = 1000
getgroups(0, NULL)                      = 9
getgroups(9, [4, 24, 27, 30, 46, 105, 108, 125, 1000]) = 9
stat("/var/log/kern.log", {st_mode=S_IFREG|0640, st_size=60330056998, ...}) = 0
stat("/var/log", {st_mode=S_IFDIR|0775, st_size=4096, ...}) = 0
geteuid()                               = 1000
geteuid()                               = 1000
getegid()                               = 1000
getgroups(0, NULL)                      = 9
getgroups(9, [4, 24, 27, 30, 46, 105, 108, 125, 1000]) = 9
stat("/var/log/kern.log", {st_mode=S_IFREG|0640, st_size=60330056998, ...}) = 0
open("/var/log/kern.log", O_RDONLY)     = 3
ioctl(3, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d768780) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(3, 0, SEEK_CUR)                   = 0
fstat(3, {st_mode=S_IFREG|0640, st_size=60330056998, ...}) = 0
fcntl(3, F_SETFD, FD_CLOEXEC)           = 0
getuid()                                = 1000
open("/proc/self/loginuid", O_RDONLY)   = 4
read(4, "4294967295", 12)               = 10
close(4)                                = 0
socket(PF_LOCAL, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 4
connect(4, {sa_family=AF_LOCAL, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(4)                                = 0
socket(PF_LOCAL, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 4
connect(4, {sa_family=AF_LOCAL, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(4)                                = 0
open("/etc/nsswitch.conf", O_RDONLY|O_CLOEXEC) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=518, ...}) = 0
mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f93cdfe6000
read(4, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 518
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0x7f93cdfe6000, 4096)            = 0
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=162616, ...}) = 0
mmap(NULL, 162616, PROT_READ, MAP_PRIVATE, 4, 0) = 0x7f93cdfbf000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libnss_compat.so.2", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260\23\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=39824, ...}) = 0
mmap(NULL, 2135368, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7f93cbbea000
mprotect(0x7f93cbbf3000, 2093056, PROT_NONE) = 0
mmap(0x7f93cbdf2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x8000) = 0x7f93cbdf2000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libnsl.so.1", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0`A\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=97296, ...}) = 0
mmap(NULL, 2202328, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7f93cb9d0000
mprotect(0x7f93cb9e7000, 2093056, PROT_NONE) = 0
mmap(0x7f93cbbe6000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x16000) = 0x7f93cbbe6000
mmap(0x7f93cbbe8000, 6872, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f93cbbe8000
close(4)                                = 0
mprotect(0x7f93cbbe6000, 4096, PROT_READ) = 0
mprotect(0x7f93cbdf2000, 4096, PROT_READ) = 0
munmap(0x7f93cdfbf000, 162616)          = 0
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 4
fstat(4, {st_mode=S_IFREG|0644, st_size=162616, ...}) = 0
mmap(NULL, 162616, PROT_READ, MAP_PRIVATE, 4, 0) = 0x7f93cdfbf000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libnss_nis.so.2", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240!\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=47760, ...}) = 0
mmap(NULL, 2143784, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7f93cb7c4000
mprotect(0x7f93cb7cf000, 2093056, PROT_NONE) = 0
mmap(0x7f93cb9ce000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xa000) = 0x7f93cb9ce000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/x86_64-linux-gnu/libnss_files.so.2", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\"\0\0\0\0\0\0"..., 832) = 832
fstat(4, {st_mode=S_IFREG|0644, st_size=47712, ...}) = 0
mmap(NULL, 2144392, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0x7f93cb5b8000
mprotect(0x7f93cb5c3000, 2093056, PROT_NONE) = 0
mmap(0x7f93cb7c2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0xa000) = 0x7f93cb7c2000
close(4)                                = 0
mprotect(0x7f93cb7c2000, 4096, PROT_READ) = 0
mprotect(0x7f93cb9ce000, 4096, PROT_READ) = 0
munmap(0x7f93cdfbf000, 162616)          = 0
open("/etc/passwd", O_RDONLY|O_CLOEXEC) = 4
lseek(4, 0, SEEK_CUR)                   = 0
fstat(4, {st_mode=S_IFREG|0644, st_size=2262, ...}) = 0
mmap(NULL, 2262, PROT_READ, MAP_SHARED, 4, 0) = 0x7f93cdfe6000
lseek(4, 2262, SEEK_SET)                = 2262
fstat(4, {st_mode=S_IFREG|0644, st_size=2262, ...}) = 0
munmap(0x7f93cdfe6000, 2262)            = 0
close(4)                                = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
fstat(0, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 7), ...}) = 0
readlink("/proc/self/fd/0", "/dev/pts/7", 511) = 10
stat("/dev/pts/7", {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 7), ...}) = 0
access("/var/run/utmpx", F_OK)          = -1 ENOENT (No such file or directory)
open("/var/run/utmp", O_RDONLY|O_CLOEXEC) = 4
lseek(4, 0, SEEK_SET)                   = 0
alarm(0)                                = 0
rt_sigaction(SIGALRM, {0x7f93cd7ad030, [], SA_RESTORER, 0x7f93cd6afd40}, {SIG_DFL, [], 0}, 8) = 0
alarm(10)                               = 0
fcntl(4, F_SETLKW, {type=F_RDLCK, whence=SEEK_SET, start=0, len=0}) = 0
read(4, "\2\0\0\0\0\0\0\0~\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(4, "\1\0\0\0002\0\0\0~\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(4, "\6\0\0\0\16\5\0\0tty4\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(4, "\6\0\0\0\22\5\0\0tty5\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(4, "\6\0\0\0\31\5\0\0tty2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(4, "\6\0\0\0\32\5\0\0tty3\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(4, "\6\0\0\0\35\5\0\0tty6\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(4, "\7\0\0\0\312\16\0\0:0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(4, "\6\0\0\0\0\n\0\0tty1\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(4, "\7\0\0\0\n\24\0\0pts/4\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
read(4, "\7\0\0\0\n\24\0\0pts/7\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 384) = 384
fcntl(4, F_SETLKW, {type=F_UNLCK, whence=SEEK_SET, start=0, len=0}) = 0
alarm(0)                                = 10
rt_sigaction(SIGALRM, {SIG_DFL, [], SA_RESTORER, 0x7f93cd6afd40}, NULL, 8) = 0
close(4)                                = 0
stat("/etc/apparmor/notify.conf", {st_mode=S_IFREG|0644, st_size=535, ...}) = 0
stat("/etc/apparmor/notify.conf", {st_mode=S_IFREG|0644, st_size=535, ...}) = 0
geteuid()                               = 1000
geteuid()                               = 1000
getegid()                               = 1000
getgroups(0, NULL)                      = 9
getgroups(9, [4, 24, 27, 30, 46, 105, 108, 125, 1000]) = 9
open("/etc/apparmor/notify.conf", O_RDONLY) = 4
ioctl(4, SNDCTL_TMR_TIMEBASE or SNDRV_TIMER_IOCTL_NEXT_DEVICE or TCGETS, 0x7fff1d768780) = -1 ENOTTY (Inappropriate ioctl for device)
lseek(4, 0, SEEK_CUR)                   = 0
fstat(4, {st_mode=S_IFREG|0644, st_size=535, ...}) = 0
fcntl(4, F_SETFD, FD_CLOEXEC)           = 0
read(4, "# ------------------------------"..., 8192) = 535
read(4, "", 8192)                       = 0
close(4)                                = 0
socket(PF_LOCAL, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 4
connect(4, {sa_family=AF_LOCAL, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(4)                                = 0
socket(PF_LOCAL, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 4
connect(4, {sa_family=AF_LOCAL, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(4)                                = 0
open("/etc/group", O_RDONLY|O_CLOEXEC)  = 4
lseek(4, 0, SEEK_CUR)                   = 0
fstat(4, {st_mode=S_IFREG|0644, st_size=1132, ...}) = 0
mmap(NULL, 1132, PROT_READ, MAP_SHARED, 4, 0) = 0x7f93cdfe6000
lseek(4, 1132, SEEK_SET)                = 1132
munmap(0x7f93cdfe6000, 1132)            = 0
close(4)                                = 0
write(1, "USAGE: aa-notify [OPTIONS]\n\nDisp"..., 710USAGE: aa-notify [OPTIONS]

Display AppArmor notifications or messages for DENIED entries.

OPTIONS:
  -p, --poll            poll AppArmor logs and display notifications
  --display $DISPLAY        set the DISPLAY environment variable to $DISPLAY
                (might be needed if sudo resets $DISPLAY)
  -f FILE, --file=FILE        search FILE for AppArmor messages
  -l, --since-last        display stats since last login
  -s NUM, --since-days=NUM    show stats for last NUM days (can be used alone
                or with -p)
  -v, --verbose            show messages with stats
  -h, --help            display this help
  -u USER, --user=USER        user to drop privileges to when not using sudo
  -w NUM, --wait=NUM        wait NUM seconds before displaying
                notifications (with -p)
) = 710
close(3)                                = 0
rt_sigaction(SIGHUP, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGILL, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTRAP, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGABRT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGBUS, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGFPE, NULL, {SIG_IGN, [FPE], SA_RESTORER|SA_RESTART, 0x7f93cd6afd40}, 8) = 0
rt_sigaction(SIGKILL, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGUSR1, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGSEGV, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGUSR2, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGPIPE, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGALRM, NULL, {SIG_DFL, [], SA_RESTORER, 0x7f93cd6afd40}, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGSTKFLT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGCHLD, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGCONT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGSTOP, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTSTP, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTTIN, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTTOU, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGURG, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGXCPU, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGXFSZ, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGVTALRM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGPROF, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGWINCH, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGIO, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGPWR, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGSYS, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_2, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_3, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_4, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_5, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_6, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_7, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_8, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_9, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_10, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_11, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_12, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_13, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_14, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_15, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_16, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_17, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_18, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_19, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_20, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_21, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_22, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_23, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_24, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_25, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_26, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_27, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_28, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_29, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_30, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_31, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGRT_32, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGABRT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGCHLD, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGIO, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGSYS, NULL, {SIG_DFL, [], 0}, 8) = 0
exit_group(1)                           = ?
+++ exited with 1 +++


```

---

### Post by matt_symes on 2015-03-22
Hi

What do your logs say ? Can you post the output of

```
grep apparmor /var/log/syslog
```

Also can you post the output of this command

```
pmap -x $(pgrep aa-notify)
```

You may need to install pmap, i can never remeber. If you do the package is procps.

Kind regards

---

### Post by sammiev on 2015-03-22
aa-notify do not show up in my system monitor using Ubuntu 14.04 Gnome 64-bit.

---

### Post by matt_symes on 2015-03-22
Hi

> **sammiev said:**
> aa-notify do not show up in my system monitor using Ubuntu 14.04 Gnome 64-bit.

I had the same in Xubuntu 14.04. 

It's in the package apparmor-notify. I had installed it on this laptop to check it out.

@OP. When and why did you install it on your PC ?

Kind regards

---

