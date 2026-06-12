---
title: "Ssmtp script no longer works"
date: 2019-02-08
forum: General Help
---

### Post by raleigh3 on 2019-02-08
This worked in Aug of 2018. Now it no longer does so. ??

```
#!/bin/bash
# Ubuntu_Mate 18.04 LTS
#
# Send an email using a script
# Make sure there are several blank lines between Subject and the message.!!

#Example of a command substitution to put the date into a variable and put that variable in the body of the mail before or after $CONTENT.
NOW=$(date +%m-%d-%Y_%I:%M%p)
CONTENT="Backup to Maxtor Drive performed on $NOW ."
echo "Sending email."
/usr/sbin/ssmtp -t -v << EOF
To: a7@yahoo.com
From: a7@yahoo.com
Subject: Backups to Maxtor Drive 

$CONTENT

EOF

```

```
andy@7_~/bin$ strace -o script_trace.txt -f ./Send_Email.sh
Sending email.
ssmtp: Cannot open mailhub:25
```

I tried to open ssmtp.conf and post it here and got

```
Geany tried to access the Unix Domain socket of another instance running as another user. This is fatal and Geany will now quit.
```

This is a previous version that worked.

```
# Config file for sSMTP sendmail
#
#  This files goes in /etc/ssmtp/
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=7@yahoo.com

# The place where the mail goes. The actual machine name is required no 
# MX records are consulted. Commonly mailhosts are named mail.domain.com
mailhub=smtp.mail.yahoo.com:465

# Where will the mail seem to come from?
rewriteDomain=yahoo.com

# The full hostname
hostname=7

AuthUser=a7

AuthPass=7

# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=YES
UseTLS=YES



```

---

### Post by dmnur on 2019-02-08
Please show the output of this command:
```
ls -l /etc/ssmtp/ssmtp.conf
```

---

### Post by raleigh3 on 2019-02-08
```
-rw-r----- 1 root mail 706 Feb  5 21:37 /etc/ssmtp/ssmtp.conf
```

After some time after running the script, I was able to open ssmtp.conf.

---

### Post by dmnur on 2019-02-08
Does it work without **strace**? Try each command:
```

~/bin/Send_Email.sh
strace ~/bin/Send_Email.sh
strace -f ~/bin/Send_Email.sh

```
Only the last one should fail.

---

### Post by raleigh3 on 2019-02-08
First command hung at Sending email.

2nd command

```
execve("/home/andy/bin/Send_Email.sh", ["/home/andy/bin/Send_Email.sh"], 0x7fffa8649d80 /* 60 vars */) = 0
brk(NULL)                               = 0x55804396f000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.preload", R_OK)      = 0
openat(AT_FDCWD, "/etc/ld.so.preload", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
close(3)                                = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=142904, ...}) = 0
mmap(NULL, 142904, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f678f310000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libtinfo.so.5", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\311\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=170784, ...}) = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f678f33e000
mmap(NULL, 2267936, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f678eee0000
mprotect(0x7f678ef05000, 2097152, PROT_NONE) = 0
mmap(0x7f678f105000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x25000) = 0x7f678f105000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libdl.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\16\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=14560, ...}) = 0
mmap(NULL, 2109712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f678ecd8000
mprotect(0x7f678ecdb000, 2093056, PROT_NONE) = 0
mmap(0x7f678eeda000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f678eeda000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260\34\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=2030544, ...}) = 0
mmap(NULL, 4131552, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f678e8e0000
mprotect(0x7f678eac7000, 2097152, PROT_NONE) = 0
mmap(0x7f678ecc7000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1e7000) = 0x7f678ecc7000
mmap(0x7f678eccd000, 15072, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f678eccd000
close(3)                                = 0
mmap(NULL, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f678f33b000
arch_prctl(ARCH_SET_FS, 0x7f678f33b740) = 0
mprotect(0x7f678ecc7000, 16384, PROT_READ) = 0
mprotect(0x7f678eeda000, 4096, PROT_READ) = 0
mprotect(0x7f678f105000, 16384, PROT_READ) = 0
mprotect(0x558041e66000, 16384, PROT_READ) = 0
mprotect(0x7f678f337000, 4096, PROT_READ) = 0
munmap(0x7f678f310000, 142904)          = 0
openat(AT_FDCWD, "/dev/tty", O_RDWR|O_NONBLOCK) = 3
close(3)                                = 0
brk(NULL)                               = 0x55804396f000
brk(0x558043990000)                     = 0x558043990000
openat(AT_FDCWD, "/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=10281472, ...}) = 0
mmap(NULL, 10281472, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f678df10000
close(3)                                = 0
getuid()                                = 1000
getgid()                                = 1000
geteuid()                               = 1000
getegid()                               = 1000
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
ioctl(-1, TIOCGPGRP, 0x7ffdd8883034)    = -1 EBADF (Bad file descriptor)
sysinfo({uptime=16560, loads=[32, 3232, 8960], totalram=7249719296, freeram=5050630144, sharedram=36823040, bufferram=170913792, totalswap=0, freeswap=0, procs=445, totalhigh=0, freehigh=0, mem_unit=1}) = 0
rt_sigaction(SIGCHLD, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGCHLD, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f678e91ef20}, 8) = 0
rt_sigaction(SIGINT, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGINT, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, 8) = 0
rt_sigaction(SIGQUIT, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGQUIT, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, 8) = 0
rt_sigaction(SIGTSTP, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGTSTP, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, 8) = 0
rt_sigaction(SIGTTIN, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGTTIN, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, 8) = 0
rt_sigaction(SIGTTOU, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGTTOU, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigaction(SIGQUIT, {sa_handler=SIG_IGN, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, 8) = 0
uname({sysname="Linux", nodename="7", ...}) = 0
stat("/home/andy/Downloads/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/home", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/home/andy", {st_mode=S_IFDIR|0777, st_size=4096, ...}) = 0
stat("/home/andy/Downloads", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
getpid()                                = 16037
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=26376, ...}) = 0
mmap(NULL, 26376, PROT_READ, MAP_SHARED, 3, 0) = 0x7f678f330000
close(3)                                = 0
getppid()                               = 16035
getpid()                                = 16037
getpgrp()                               = 16035
ioctl(2, TIOCGPGRP, [16035])            = 0
rt_sigaction(SIGCHLD, {sa_handler=0x558041bba660, sa_mask=[], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f678e91ef20}, 8) = 0
prlimit64(0, RLIMIT_NPROC, NULL, {rlim_cur=27418, rlim_max=27418}) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
openat(AT_FDCWD, "/home/andy/bin/Send_Email.sh", O_RDONLY) = 3
stat("/home/andy/bin/Send_Email.sh", {st_mode=S_IFREG|0775, st_size=622, ...}) = 0
ioctl(3, TCGETS, 0x7ffdd8882fc0)        = -1 ENOTTY (Inappropriate ioctl for device)
lseek(3, 0, SEEK_CUR)                   = 0
read(3, "#!/bin/bash\n# Ubuntu_Mate 18.04 "..., 80) = 80
lseek(3, 0, SEEK_SET)                   = 0
prlimit64(0, RLIMIT_NOFILE, NULL, {rlim_cur=1024, rlim_max=1024*1024}) = 0
fcntl(255, F_GETFD)                     = -1 EBADF (Bad file descriptor)
dup2(3, 255)                            = 255
close(3)                                = 0
fcntl(255, F_SETFD, FD_CLOEXEC)         = 0
fcntl(255, F_GETFL)                     = 0x8000 (flags O_RDONLY|O_LARGEFILE)
fstat(255, {st_mode=S_IFREG|0775, st_size=622, ...}) = 0
lseek(255, 0, SEEK_CUR)                 = 0
read(255, "#!/bin/bash\n# Ubuntu_Mate 18.04 "..., 622) = 622
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
pipe([3, 4])                            = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
lseek(255, -217, SEEK_CUR)              = 405
clone(child_stack=NULL, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f678f33ba10) = 16038
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigaction(SIGCHLD, {sa_handler=0x558041bba660, sa_mask=[], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f678e91ef20}, {sa_handler=0x558041bba660, sa_mask=[], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f678e91ef20}, 8) = 0
close(4)                                = 0
read(3, "02-08-2019_03:33PM\n", 128)    = 19
--- SIGCHLD {si_signo=SIGCHLD, si_code=CLD_EXITED, si_pid=16038, si_uid=1000, si_status=0, si_utime=0, si_stime=0} ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], WNOHANG, NULL) = 16038
wait4(-1, 0x7ffdd8882310, WNOHANG, NULL) = -1 ECHILD (No child processes)
rt_sigreturn({mask=[]})                 = 19
read(3, "", 128)                        = 0
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {sa_handler=0x558041bb7030, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, 8) = 0
rt_sigaction(SIGINT, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, {sa_handler=0x558041bb7030, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
read(255, "CONTENT=\"Backup to Maxtor Drive "..., 622) = 217
fstat(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 1), ...}) = 0
write(1, "Sending email.\n", 15Sending email.
)        = 15
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [], 8) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [INT CHLD], 8) = 0
rt_sigprocmask(SIG_SETMASK, [INT CHLD], NULL, 8) = 0
lseek(255, -2, SEEK_CUR)                = 620
clone(child_stack=NULL, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0x7f678f33ba10) = 16039
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGINT, {sa_handler=0x558041bb7030, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f678e91ef20}, 8) = 0
wait4(-1, 0x7ffdd8882d80, 0, NULL)      = ? ERESTARTSYS (To be restarted if SA_RESTART is set)
--- SIGWINCH {si_signo=SIGWINCH, si_code=SI_KERNEL} ---
wait4(-1,
```

3rd command

```
execve("/home/andy/bin/Send_Email.sh", ["/home/andy/bin/Send_Email.sh"], 0x7ffe636e4428 /* 60 vars */) = 0
brk(NULL)                               = 0x55ec9e6dd000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.preload", R_OK)      = 0
openat(AT_FDCWD, "/etc/ld.so.preload", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
close(3)                                = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=142904, ...}) = 0
mmap(NULL, 142904, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f5127530000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libtinfo.so.5", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\311\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=170784, ...}) = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f5127555000
mmap(NULL, 2267936, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f5127100000
mprotect(0x7f5127125000, 2097152, PROT_NONE) = 0
mmap(0x7f5127325000, 20480, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x25000) = 0x7f5127325000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libdl.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\16\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=14560, ...}) = 0
mmap(NULL, 2109712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f5126ef8000
mprotect(0x7f5126efb000, 2093056, PROT_NONE) = 0
mmap(0x7f51270fa000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f51270fa000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260\34\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=2030544, ...}) = 0
mmap(NULL, 4131552, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f5126b00000
mprotect(0x7f5126ce7000, 2097152, PROT_NONE) = 0
mmap(0x7f5126ee7000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1e7000) = 0x7f5126ee7000
mmap(0x7f5126eed000, 15072, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f5126eed000
close(3)                                = 0
mmap(NULL, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f512752d000
arch_prctl(ARCH_SET_FS, 0x7f512752d740) = 0
mprotect(0x7f5126ee7000, 16384, PROT_READ) = 0
mprotect(0x7f51270fa000, 4096, PROT_READ) = 0
mprotect(0x7f5127325000, 16384, PROT_READ) = 0
mprotect(0x55ec9d08c000, 16384, PROT_READ) = 0
mprotect(0x7f5127557000, 4096, PROT_READ) = 0
munmap(0x7f5127530000, 142904)          = 0
openat(AT_FDCWD, "/dev/tty", O_RDWR|O_NONBLOCK) = 3
close(3)                                = 0
brk(NULL)                               = 0x55ec9e6dd000
brk(0x55ec9e6fe000)                     = 0x55ec9e6fe000
openat(AT_FDCWD, "/usr/lib/locale/locale-archive", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=10281472, ...}) = 0
mmap(NULL, 10281472, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f5126130000
close(3)                                = 0
getuid()                                = 1000
getgid()                                = 1000
geteuid()                               = 1000
getegid()                               = 1000
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
ioctl(-1, TIOCGPGRP, 0x7fffc5460534)    = -1 EBADF (Bad file descriptor)
sysinfo({uptime=16891, loads=[20992, 12928, 11072], totalram=7249719296, freeram=5053702144, sharedram=37007360, bufferram=171188224, totalswap=0, freeswap=0, procs=444, totalhigh=0, freehigh=0, mem_unit=1}) = 0
rt_sigaction(SIGCHLD, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f5126b3ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGCHLD, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f5126b3ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f5126b3ef20}, 8) = 0
rt_sigaction(SIGINT, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGINT, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, 8) = 0
rt_sigaction(SIGQUIT, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGQUIT, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, 8) = 0
rt_sigaction(SIGTSTP, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGTSTP, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, 8) = 0
rt_sigaction(SIGTTIN, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGTTIN, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, 8) = 0
rt_sigaction(SIGTTOU, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGTTOU, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, 8) = 0
rt_sigprocmask(SIG_BLOCK, NULL, [], 8)  = 0
rt_sigaction(SIGQUIT, {sa_handler=SIG_IGN, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=SA_RESTORER, sa_restorer=0x7f5126b3ef20}, 8) = 0
uname({sysname="Linux", nodename="7", ...}) = 0
stat("/home/andy/Downloads/", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat(".", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/home", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
stat("/home/andy", {st_mode=S_IFDIR|0777, st_size=4096, ...}) = 0
stat("/home/andy/Downloads", {st_mode=S_IFDIR|0755, st_size=4096, ...}) = 0
getpid()                            
```

How do I stop ssmtp? Ctrl Break and ctrl c do not work. I have to close my terminal.

---

### Post by dmnur on 2019-02-08
I don't have a Yahoo Mail account to test, but it's probably related to this:
```

$ openssl s_client -connect smtp.mail.yahoo.com:465
...
220 smtp.mail.yahoo.com ESMTP ready
ehlo 7
250-smtp429.mail.ir2.yahoo.com Hello 7 [188.254.110.183])
250-PIPELINING
250-ENHANCEDSTATUSCODES
250-8BITMIME
250-SIZE 41697280
250 AUTH PLAIN LOGIN XOAUTH2 OAUTHBEARER
auth plain
334 UGxhaW46
YTcANw==
535 5.7.0 (#AUTH005) Too many bad auth attempts.
closed
$

```

This is the interesting part:
```
535 5.7.0 (#AUTH005) Too many bad auth attempts.
```

Of course I assume that the credentials you've provided in the config file are not real, but anyway: the server shouldn't answer in this way under normal circumstances.

Try to log in to webmail and/or via a mail client and send messages from there. Maybe your account was blocked or something.

---

### Post by raleigh3 on 2019-02-08
Not sure what you mean by the last statement.

Send an email from my browser?

sendmail does not work either. ??
Does it depend on things that ssmtp depend on?

---

### Post by raleigh3 on 2019-02-08
Trying to get sendmail working. 

This is what I get. 

Not sure how to proceed.

```
andy@7_~/Downloads/$  echo "Subject: hello" | sendmail -v [EMAIL="andrew_kennedy7@yahoo.com"]7@yahoo.com[/EMAIL] < mail.txt
[EMAIL="andrew_kennedy7@yahoo.com"]7@yahoo.com[/EMAIL]... Connecting to [127.0.0.1] via relay...
220 7.netgear.com ESMTP Sendmail 8.15.2/8.15.2/Debian-10; Fri, 8 Feb 2019 18:17:56 -0600; (No UCE/UBE) logging access from: localhost(OK)-localhost [127.0.0.1]
>>> EHLO 7.netgear.com
250-7.netgear.com Hello localhost [127.0.0.1], pleased to meet you
250-ENHANCEDSTATUSCODES
250-PIPELINING
250-EXPN
250-VERB
250-8BITMIME
250-SIZE
250-DSN
250-ETRN
250-AUTH DIGEST-MD5 CRAM-MD5
250-DELIVERBY
250 HELP
>>> VERB
250 2.0.0 Verbose mode
>>> MAIL From:<andy@7.netgear.com> SIZE=11 AUTH=andy@7.netgear.com
250 2.1.0 <andy@7.netgear.com>... Sender ok
>>> RCPT To:<7@yahoo.com>
>>> DATA
250 2.1.5 <7@yahoo.com>... Recipient ok
354 Enter mail, end with "." on a line by itself
>>> .
```

---

### Post by dmnur on 2019-02-09
[quote=raleigh3]Trying to get sendmail working.[/quote]
A separate **sendmail** requires additional setup. **ssmtp** provides its own **sendmail** command for compatibilty, which is just a symlink to **ssmtp**.


Let's try to trace **ssmtp** directly, and that would require using **sudo**: otherwise **ssmtp** fails to read **/etc/ssmtp/ssmtp.conf**, and you get this error:
```
ssmtp: Cannot open mailhub:25
```

First, create the file **mail.txt** with these contents:
```

From: a7@yahoo.com
To: a7@yahoo.com
Subject: Test

Just testing.

```

Now, to trace:
```
sudo strace -o ssmtp.trace ssmtp -t -v < mail.txt &> ssmtp.out
```

After this please show **ssmtp.trace** and **ssmtp.out** contents. Don't worry, **ssmtp** doesn't include your password there. E.g. in my case:
```

[->] AUTH LOGIN
[<-] 334 VXNlcm5hbWU6
[->] bm90cmVhbEBleGFtcGxlLmNvbQ==
[<-] 334 UGFzc3dvcmQ6
[<-] 235 2.7.0 Authentication successful.

```

Only the username line is shown. You can decipher these lines with some base64 decoder to double-check. For example:
```

$ base64 -d <<< bm90cmVhbEBleGFtcGxlLmNvbQ==
notreal@example.com

```

Actually I think that something's wrong with your local DNS resolver. That would explain **ssmtp** ignoring Ctrl+C; by the way, _you probably need to wait a minute or two for it to unfreeze_.
We'll see soon.

---

### Post by raleigh3 on 2019-02-09
ssmtp.out

```
ssmtp: Cannot open smtp.mail.yahoo.com:587
```

ssmtp.trace

```
execve("/usr/sbin/ssmtp", ["ssmtp", "-t", "-v"], 0x7ffc7e8b2f00 /* 18 vars */) = 0
access("/etc/suid-debug", F_OK)         = -1 ENOENT (No such file or directory)
brk(NULL)                               = 0x55f638394000
fcntl(0, F_GETFD)                       = 0
fcntl(1, F_GETFD)                       = 0
fcntl(2, F_GETFD)                       = 0
access("/etc/suid-debug", F_OK)         = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.preload", R_OK)      = 0
openat(AT_FDCWD, "/etc/ld.so.preload", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
close(3)                                = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=143012, ...}) = 0
mmap(NULL, 143012, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f8933e48000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libgnutls-openssl.so.27", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P-\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=34656, ...}) = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f8933e6d000
mmap(NULL, 2129936, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8933a38000
mprotect(0x7f8933a40000, 2093056, PROT_NONE) = 0
mmap(0x7f8933c3f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7000) = 0x7f8933c3f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260\34\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=2030544, ...}) = 0
mmap(NULL, 4131552, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8933640000
mprotect(0x7f8933827000, 2097152, PROT_NONE) = 0
mmap(0x7f8933a27000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1e7000) = 0x7f8933a27000
mmap(0x7f8933a2d000, 15072, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f8933a2d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libgnutls.so.30", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\207\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1457760, ...}) = 0
mmap(NULL, 3558216, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f89332d8000
mprotect(0x7f893342f000, 2097152, PROT_NONE) = 0
mmap(0x7f893362f000, 53248, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x157000) = 0x7f893362f000
mmap(0x7f893363c000, 2888, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f893363c000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libz.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\37\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=116960, ...}) = 0
mmap(NULL, 2212016, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f89330b8000
mprotect(0x7f89330d4000, 2093056, PROT_NONE) = 0
mmap(0x7f89332d3000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1b000) = 0x7f89332d3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libp11-kit.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\263\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1237640, ...}) = 0
mmap(NULL, 3334512, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8932d88000
mprotect(0x7f8932ea2000, 2097152, PROT_NONE) = 0
mmap(0x7f89330a2000, 81920, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x11a000) = 0x7f89330a2000
mmap(0x7f89330b6000, 368, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f89330b6000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libidn2.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\25\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=116656, ...}) = 0
mmap(NULL, 2211864, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8932b68000
mprotect(0x7f8932b84000, 2093056, PROT_NONE) = 0
mmap(0x7f8932d83000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1b000) = 0x7f8932d83000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libunistring.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\365\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1562664, ...}) = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f8933e6b000
mmap(NULL, 3660040, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f89327e8000
mprotect(0x7f8932962000, 2097152, PROT_NONE) = 0
mmap(0x7f8932b62000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x17a000) = 0x7f8932b62000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libtasn1.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220)\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=75776, ...}) = 0
mmap(NULL, 2171592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f89325d0000
mprotect(0x7f89325e1000, 2097152, PROT_NONE) = 0
mmap(0x7f89327e1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x11000) = 0x7f89327e1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libnettle.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\200\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=219304, ...}) = 0
mmap(NULL, 2314384, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8932398000
mprotect(0x7f89323cc000, 2093056, PROT_NONE) = 0
mmap(0x7f89325cb000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x33000) = 0x7f89325cb000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libhogweed.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 j\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=211704, ...}) = 0
mmap(NULL, 2306760, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8932160000
mprotect(0x7f8932193000, 2093056, PROT_NONE) = 0
mmap(0x7f8932392000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x32000) = 0x7f8932392000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libgmp.so.10", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\223\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=526688, ...}) = 0
mmap(NULL, 2621888, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8931ed8000
mprotect(0x7f8931f57000, 2097152, PROT_NONE) = 0
mmap(0x7f8932157000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7f000) = 0x7f8932157000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libffi.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\27\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=31032, ...}) = 0
mmap(NULL, 2127368, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8931cd0000
mprotect(0x7f8931cd7000, 2093056, PROT_NONE) = 0
mmap(0x7f8931ed6000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7f8931ed6000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libdl.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\16\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=14560, ...}) = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f8933e46000
mmap(NULL, 2109712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8931ac8000
mprotect(0x7f8931acb000, 2093056, PROT_NONE) = 0
mmap(0x7f8931cca000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f8931cca000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libpthread.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000b\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=144976, ...}) = 0
mmap(NULL, 2221184, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f89318a8000
mprotect(0x7f89318c2000, 2093056, PROT_NONE) = 0
mmap(0x7f8931ac1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x19000) = 0x7f8931ac1000
mmap(0x7f8931ac3000, 13440, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f8931ac3000
close(3)                                = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f8933e44000
arch_prctl(ARCH_SET_FS, 0x7f8933e44b80) = 0
mprotect(0x7f8933a27000, 16384, PROT_READ) = 0
mprotect(0x7f8931ac1000, 4096, PROT_READ) = 0
mprotect(0x7f8931cca000, 4096, PROT_READ) = 0
mprotect(0x7f8931ed6000, 4096, PROT_READ) = 0
mprotect(0x7f8932157000, 4096, PROT_READ) = 0
mprotect(0x7f89325cb000, 8192, PROT_READ) = 0
mprotect(0x7f8932392000, 4096, PROT_READ) = 0
mprotect(0x7f89327e1000, 4096, PROT_READ) = 0
mprotect(0x7f8932b62000, 12288, PROT_READ) = 0
mprotect(0x7f8932d83000, 4096, PROT_READ) = 0
mprotect(0x7f89330a2000, 40960, PROT_READ) = 0
mprotect(0x7f89332d3000, 4096, PROT_READ) = 0
mprotect(0x7f893362f000, 49152, PROT_READ) = 0
mprotect(0x7f8933c3f000, 4096, PROT_READ) = 0
mprotect(0x55f638228000, 4096, PROT_READ) = 0
mprotect(0x7f8933e6f000, 4096, PROT_READ) = 0
munmap(0x7f8933e48000, 143012)          = 0
set_tid_address(0x7f8933e44e50)         = 4256
set_robust_list(0x7f8933e44e60, 24)     = 0
rt_sigaction(SIGRTMIN, {sa_handler=0x7f89318adcb0, sa_mask=[], sa_flags=SA_RESTORER|SA_SIGINFO, sa_restorer=0x7f89318ba890}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {sa_handler=0x7f89318add50, sa_mask=[], sa_flags=SA_RESTORER|SA_RESTART|SA_SIGINFO, sa_restorer=0x7f89318ba890}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
prlimit64(0, RLIMIT_STACK, NULL, {rlim_cur=8192*1024, rlim_max=RLIM64_INFINITY}) = 0
futex(0x7f89330b60e0, FUTEX_WAKE_PRIVATE, 2147483647) = 0
brk(NULL)                               = 0x55f638394000
brk(0x55f6383b5000)                     = 0x55f6383b5000
getrandom("\x8f", 1, GRND_NONBLOCK)     = 1
stat("/etc/gnutls/default-priorities", 0x7ffed9c95120) = -1 ENOENT (No such file or directory)
rt_sigaction(SIGHUP, {sa_handler=SIG_IGN, sa_mask=[HUP], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f893367ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGINT, {sa_handler=SIG_IGN, sa_mask=[INT], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f893367ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGTTIN, {sa_handler=SIG_IGN, sa_mask=[TTIN], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f893367ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGTTOU, {sa_handler=SIG_IGN, sa_mask=[TTOU], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f893367ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
uname({sysname="Linux", nodename="7", ...}) = 0
getuid()                                = 0
socket(AF_UNIX, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_UNIX, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
socket(AF_UNIX, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_UNIX, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
openat(AT_FDCWD, "/etc/nsswitch.conf", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=556, ...}) = 0
read(3, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 556
read(3, "", 4096)                       = 0
close(3)                                = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=143012, ...}) = 0
mmap(NULL, 143012, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f8933e20000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_compat.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\22\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=39744, ...}) = 0
mmap(NULL, 2136256, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8931698000
mprotect(0x7f89316a0000, 2097152, PROT_NONE) = 0
mmap(0x7f89318a0000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8000) = 0x7f89318a0000
close(3)                                = 0
mprotect(0x7f89318a0000, 4096, PROT_READ) = 0
munmap(0x7f8933e20000, 143012)          = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=143012, ...}) = 0
mmap(NULL, 143012, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f8933e20000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_nis.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p \0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=47576, ...}) = 0
mmap(NULL, 2143624, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8931488000
mprotect(0x7f8931493000, 2093056, PROT_NONE) = 0
mmap(0x7f8931692000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa000) = 0x7f8931692000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnsl.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220@\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=97176, ...}) = 0
mmap(NULL, 2202200, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8931268000
mprotect(0x7f893127f000, 2093056, PROT_NONE) = 0
mmap(0x7f893147e000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16000) = 0x7f893147e000
mmap(0x7f8931480000, 6744, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f8931480000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_files.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P#\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=47568, ...}) = 0
mmap(NULL, 2168632, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8931050000
mprotect(0x7f893105b000, 2093056, PROT_NONE) = 0
mmap(0x7f893125a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa000) = 0x7f893125a000
mmap(0x7f893125c000, 22328, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f893125c000
close(3)                                = 0
mprotect(0x7f893125a000, 4096, PROT_READ) = 0
mprotect(0x7f893147e000, 4096, PROT_READ) = 0
mprotect(0x7f8931692000, 4096, PROT_READ) = 0
munmap(0x7f8933e20000, 143012)          = 0
openat(AT_FDCWD, "/etc/passwd", O_RDONLY|O_CLOEXEC) = 3
lseek(3, 0, SEEK_CUR)                   = 0
fstat(3, {st_mode=S_IFREG|0644, st_size=2637, ...}) = 0
mmap(NULL, 2637, PROT_READ, MAP_SHARED, 3, 0) = 0x7f8933e68000
lseek(3, 2637, SEEK_SET)                = 2637
munmap(0x7f8933e68000, 2637)            = 0
close(3)                                = 0
openat(AT_FDCWD, "/etc/localtime", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=3585, ...}) = 0
fstat(3, {st_mode=S_IFREG|0644, st_size=3585, ...}) = 0
read(3, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\7\0\0\0\7\0\0\0\0"..., 4096) = 3585
lseek(3, -2281, SEEK_CUR)               = 1304
read(3, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\7\0\0\0\7\0\0\0\0"..., 4096) = 2281
brk(0x55f6383d6000)                     = 0x55f6383d6000
close(3)                                = 0
openat(AT_FDCWD, "/etc/ssmtp/ssmtp.conf", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0640, st_size=707, ...}) = 0
read(3, "#\n# Config file for sSMTP sendma"..., 4096) = 707
read(3, "", 4096)                       = 0
close(3)                                = 0
openat(AT_FDCWD, "/etc/ssmtp/revaliases", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0640, st_size=256, ...}) = 0
read(3, "# sSMTP aliases\n# \n# Format:\tloc"..., 4096) = 256
read(3, "", 4096)                       = 0
close(3)                                = 0
fstat(0, {st_mode=S_IFREG|0664, st_size=75, ...}) = 0
read(0, "From: a7@yahoo.com\nTo: a7@yahoo."..., 4096) = 75
rt_sigaction(SIGALRM, {sa_handler=0x55f638022560, sa_mask=[ALRM], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f893367ef20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
alarm(600)                              = 0
socket(AF_UNIX, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_UNIX, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
socket(AF_UNIX, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_UNIX, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
stat("/etc/resolv.conf", {st_mode=S_IFREG|0644, st_size=720, ...}) = 0
openat(AT_FDCWD, "/etc/host.conf", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=92, ...}) = 0
read(3, "# The \"order\" line is only used "..., 4096) = 92
read(3, "", 4096)                       = 0
close(3)                                = 0
futex(0x7f8933a2fba4, FUTEX_WAKE_PRIVATE, 2147483647) = 0
openat(AT_FDCWD, "/etc/resolv.conf", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=720, ...}) = 0
read(3, "# This file is managed by man:sy"..., 4096) = 720
read(3, "", 4096)                       = 0
close(3)                                = 0
openat(AT_FDCWD, "/etc/hosts", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0664, st_size=470467, ...}) = 0
read(3, "# This MVPS HOSTS file is a free"..., 4096) = 4096
read(3, "0.0 admarket.cz\r\n0.0.0.0 www.adm"..., 4096) = 4096
read(3, ".0.0 banners.affiliatefuture.com"..., 4096) = 4096
read(3, "\r\n0.0.0.0 www.bettertextads.com\r"..., 4096) = 4096
read(3, "0.0 www.contaxe.com\r\n0.0.0.0 www"..., 4096) = 4096
read(3, "es\r\n0.0.0.0 s1415903351.t.eloqua"..., 4096) = 4096
read(3, ".0.0 getrank.net\r\n0.0.0.0 getroc"..., 4096) = 4096
read(3, "rmatm.com\r\n0.0.0.0 pcbutts1.soft"..., 4096) = 4096
read(3, "tingware.com\r\n0.0.0.0 s1.listrak"..., 4096) = 4096
read(3, "rking Service]\r\n0.0.0.0 www.ndpa"..., 4096) = 4096
read(3, "0 viewer.peer39.com\r\n0.0.0.0 ban"..., 4096) = 4096
read(3, ".0.0 mct.rkdms.com\r\n0.0.0.0 ei.r"..., 4096) = 4096
read(3, "l.com\r\n0.0.0.0 www.start-page.or"..., 4096) = 4096
read(3, "r.truehits.net\r\n0.0.0.0 origin-t"..., 4096) = 4096
read(3, "www.webhits.de\r\n0.0.0.0 ads.webk"..., 4096) = 4096
read(3, ".3conline.com\r\n0.0.0.0 imgad2.3c"..., 4096) = 4096
read(3, "04.45.255.255]\r\n0.0.0.0 hitslap."..., 4096) = 4096
read(3, "0.0 stx0.sextracker.com\r\n0.0.0.0"..., 4096) = 4096
read(3, "0 indexhu.adocean.pl\r\n0.0.0.0 in"..., 4096) = 4096
read(3, "\r\n0.0.0.0 tag.aticdn.net\r\n0.0.0."..., 4096) = 4096
read(3, "0.0 fast.everydayhealth.demdex.n"..., 4096) = 4096
read(3, ".analytics.edgesuite.net #[Akama"..., 4096) = 4096
read(3, "0.0 stream1.marketwatch.fyre.co\r"..., 4096) = 4096
read(3, "-p.mythings.com\r\n0.0.0.0 abandon"..., 4096) = 4096
read(3, "0 ads.mopub.com\r\n0.0.0.0 papi.my"..., 4096) = 4096
read(3, "0.0 adsys.adk2x.com\r\n0.0.0.0 s.a"..., 4096) = 4096
read(3, ".net\r\n0.0.0.0 d24n15hnbwhuhn.clo"..., 4096) = 4096
read(3, "m\r\n# [Amazon.com][AS16509][54.20"..., 4096) = 4096
read(3, "m\r\n0.0.0.0 cdn.ip.inpwrd.com\r\n0."..., 4096) = 4096
read(3, "com\r\n0.0.0.0 pages-stats.rbl.ms\r"..., 4096) = 4096
read(3, "ww.supersonicads.com\r\n0.0.0.0 ap"..., 4096) = 4096
read(3, "i.com\r\n0.0.0.0 logc8.xiti.com\r\n0"..., 4096) = 4096
read(3, "ifymedia.com\r\n0.0.0.0 x.clickcer"..., 4096) = 4096
read(3, "hit.stat24.com\r\n0.0.0.0 ua4.hit."..., 4096) = 4096
read(3, "er42.bravenet.com\r\n0.0.0.0 count"..., 4096) = 4096
read(3, ".23.132.248 - 217.23.132.255]\r\n0"..., 4096) = 4096
read(3, "bBug]\r\n0.0.0.0 activity.serving-"..., 4096) = 4096
read(3, " - 104.31.255.255]\r\n0.0.0.0 try."..., 4096) = 4096
read(3, " cdn.popmyads.com\r\n0.0.0.0 asset"..., 4096) = 4096
read(3, ".0.0 ua.adriver.ru\r\n0.0.0.0 ua-c"..., 4096) = 4096
read(3, ".com\r\n0.0.0.0 static.criteo.net\r"..., 4096) = 4096
read(3, "pmedownload.com\r\n0.0.0.0 www.mp3"..., 4096) = 4096
read(3, "o.com\r\n0.0.0.0 adsatt.espn.starw"..., 4096) = 4096
read(3, "conviva.com #[affects videos]\r\n0"..., 4096) = 4096
read(3, "bx.com\r\n0.0.0.0 pixel.facebook.c"..., 4096) = 4096
read(3, "2915dc.v.fwmrm.net\r\n0.0.0.0 2912"..., 4096) = 4096
read(3, "ro.hit.gemius.pl\r\n0.0.0.0 axel.h"..., 4096) = 4096
read(3, "it.stat.pl\r\n0.0.0.0 s1.hit.stat."..., 4096) = 4096
read(3, "traffic.com\r\n0.0.0.0 codeads.com"..., 4096) = 4096
read(3, "om\r\n0.0.0.0 speednetwork14.adk2x"..., 4096) = 4096
read(3, "488352.fls.doubleclick.net\r\n0.0."..., 4096) = 4096
read(3, ".com\r\n0.0.0.0 target.e-generator"..., 4096) = 4096
read(3, "chsys.com\r\n0.0.0.0 media.brandre"..., 4096) = 4096
read(3, "Parked.com][AS32592][69.46.224.0"..., 4096) = 4096
read(3, "0 - 212.162.15.255]\r\n0.0.0.0 lin"..., 4096) = 4096
read(3, "[Interland / Web.com][AS36476][2"..., 4096) = 4096
read(3, ".net\r\n# [Internap / Atrinsic][AS"..., 4096) = 4096
read(3, "ebtrekk.net\r\n0.0.0.0 jade01.webt"..., 4096) = 4096
read(3, "0.0 image1.cecash.com\r\n0.0.0.0 c"..., 4096) = 4096
read(3, "wordpress.com #[WebBug]\r\n0.0.0.0"..., 4096) = 4096
read(3, "m\r\n# [Leaseweb][AS16265][AS60781"..., 4096) = 4096
read(3, "m\r\n0.0.0.0 7457.accessaw.bluesee"..., 4096) = 4096
read(3, "content.exoticads.com\r\n0.0.0.0 m"..., 4096) = 4096
read(3, "ru\r\n0.0.0.0 top.list.ru\r\n0.0.0.0"..., 4096) = 4096
read(3, "075][137.116.0.0 - 137.116.255.2"..., 4096) = 4096
read(3, "92.140.47]\r\n0.0.0.0 flashadtools"..., 4096) = 4096
read(3, "0 - 66.29.127.255]\r\n# [Net Acces"..., 4096) = 4096
read(3, "0 - 212.143.22.255]\r\n0.0.0.0 ads"..., 4096) = 4096
read(3, "\n0.0.0.0 mini.activeshopper.com\r"..., 4096) = 4096
read(3, "0.0.0.0 media-6.vpptechnologies."..., 4096) = 4096
read(3, ".0.0.0 daimlerag.d2.sc.omtrdc.ne"..., 4096) = 4096
read(3, "vgtechnologies.112.2o7.net\r\n0.0."..., 4096) = 4096
read(3, "asterglobal.112.2o7.net\r\n0.0.0.0"..., 4096) = 4096
read(3, "112.2o7.net\r\n0.0.0.0 gntbcstkusa"..., 4096) = 4096
read(3, "2.2o7.net\r\n0.0.0.0 mghickoryreco"..., 4096) = 4096
read(3, ".0.0.0 newsquestdigitalmedia.122"..., 4096) = 4096
read(3, ".112.2o7.net\r\n0.0.0.0 rainbowmed"..., 4096) = 4096
read(3, " timeessence.122.2o7.net\r\n0.0.0."..., 4096) = 4096
read(3, "ziffdavisglobal.112.2o7.net\r\n0.0"..., 4096) = 4096
read(3, "ics.fnac.es\r\n0.0.0.0 sc-forbes.f"..., 4096) = 4096
read(3, ".0.0 stats2.vanityfair.com\r\n0.0."..., 4096) = 4096
read(3, "e-adhese.gva.be\r\n0.0.0.0 pebble-"..., 4096) = 4096
read(3, "vedbyopenx.com\r\n0.0.0.0 ox-d.soc"..., 4096) = 4096
read(3, "x-traceur.com\r\n# [Ovh Sas][217.1"..., 4096) = 4096
read(3, "ads.dt.mydas.mobi\r\n0.0.0.0 bank0"..., 4096) = 4096
read(3, ".telemetryverification.net\r\n0.0."..., 4096) = 4096
read(3, "r-203.sv2.biz\r\n0.0.0.0 ktu.sv2.b"..., 4096) = 4096
read(3, "0 users.effectivebrand.com\r\n0.0."..., 4096) = 4096
read(3, ".61.179.95]\r\n0.0.0.0 www.trackin"..., 4096) = 4096
read(3, ".0.0.0 ad.where.com\r\n# [Rambler]"..., 4096) = 4096
read(3, " sa.scorecardresearch.com\r\n# [Sa"..., 4096) = 4096
read(3, ".0.0 - 173.204.255.255]\r\n# [Serv"..., 4096) = 4096
read(3, "\n0.0.0.0 codiceisp.shinystat.it\r"..., 4096) = 4096
read(3, "0.0 eclkspsa.com\r\n0.0.0.0 tags1."..., 4096) = 4096
read(3, "86.255.255]\r\n0.0.0.0 ads.aboveto"..., 4096) = 4096
read(3, "5]\r\n0.0.0.0 www.clixtrac.com\r\n0."..., 4096) = 4096
read(3, "0.0 www.adengage.com\r\n# [TekChan"..., 4096) = 4096
read(3, "m\r\n0.0.0.0 wrap.tradedoubler.com"..., 4096) = 4096
read(3, "unter.yakcash.com\r\n# [Theplanet."..., 4096) = 4096
read(3, "ivatamateure.com #[Sagnet Group]"..., 4096) = 4096
read(3, "34.207.255]\r\n# [ValueClick / Com"..., 4096) = 4096
read(3, "computerwoche.de.intellitxt.com\r"..., 4096) = 4096
read(3, "nology.uk.intellitxt.com\r\n0.0.0."..., 4096) = 4096
read(3, "ritysmackblog.us.intellitxt.com\r"..., 4096) = 4096
read(3, "\r\n0.0.0.0 forbes.us.intellitxt.c"..., 4096) = 4096
read(3, "itxt.com\r\n0.0.0.0 investopedia.u"..., 4096) = 4096
read(3, ".com\r\n0.0.0.0 ninjadude.us.intel"..., 4096) = 4096
read(3, "ntellitxt.com\r\n0.0.0.0 tenmagazi"..., 4096) = 4096
read(3, "l\r\n0.0.0.0 3.googlenews.xorg.pl\r"..., 4096) = 4096
read(3, "com\r\n0.0.0.0 www.professionalcas"..., 4096) = 4096
read(3, "]\r\n0.0.0.0 fttcj.com\r\n0.0.0.0 ad"..., 4096) = 4096
read(3, "oasc12016.247realmedia.com\r\n0.0."..., 4096) = 4096
read(3, "now.com\r\n0.0.0.0 oascentral.onwi"..., 4096) = 4096
read(3, "O Communications][AS2828][65.104"..., 4096) = 4096
read(3, ".0.0.0 sp.analytics.yahoo.com\r\n0"..., 4096) = 3523
read(3, "", 4096)                       = 0
close(3)                                = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=143012, ...}) = 0
mmap(NULL, 143012, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f8933e20000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_mdns4_minimal.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\v\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=10160, ...}) = 0
mmap(NULL, 2105360, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8930e48000
mprotect(0x7f8930e4a000, 2093056, PROT_NONE) = 0
mmap(0x7f8931049000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x7f8931049000
close(3)                                = 0
mprotect(0x7f8931049000, 4096, PROT_READ) = 0
munmap(0x7f8933e20000, 143012)          = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=143012, ...}) = 0
mmap(NULL, 143012, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f8933e20000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_dns.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\17\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=26936, ...}) = 0
mmap(NULL, 2121952, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8930c40000
mprotect(0x7f8930c45000, 2097152, PROT_NONE) = 0
mmap(0x7f8930e45000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x5000) = 0x7f8930e45000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libresolv.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\00008\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=101168, ...}) = 0
mmap(NULL, 2206336, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f8930a20000
mprotect(0x7f8930a37000, 2097152, PROT_NONE) = 0
mmap(0x7f8930c37000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x17000) = 0x7f8930c37000
mmap(0x7f8930c39000, 6784, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f8930c39000
close(3)                                = 0
mprotect(0x7f8930c37000, 4096, PROT_READ) = 0
mprotect(0x7f8930e45000, 4096, PROT_READ) = 0
munmap(0x7f8933e20000, 143012)          = 0
socket(AF_INET, SOCK_DGRAM|SOCK_CLOEXEC|SOCK_NONBLOCK, IPPROTO_IP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("127.0.0.53")}, 16) = 0
poll([{fd=3, events=POLLOUT}], 1, 0)    = 1 ([{fd=3, revents=POLLOUT}])
sendmmsg(3, [{msg_hdr={msg_name=NULL, msg_namelen=0, msg_iov=[{iov_base="+\27\1\0\0\1\0\0\0\0\0\0\4smtp\4mail\5yahoo\3com"..., iov_len=37}], msg_iovlen=1, msg_controllen=0, msg_flags=0}, msg_len=37}, {msg_hdr={msg_name=NULL, msg_namelen=0, msg_iov=[{iov_base="\254)\1\0\0\1\0\0\0\0\0\0\4smtp\4mail\5yahoo\3com"..., iov_len=37}], msg_iovlen=1, msg_controllen=0, msg_flags=MSG_TRUNC|MSG_DONTWAIT|MSG_EOR|MSG_WAITALL|MSG_FIN|MSG_SYN|MSG_CONFIRM|MSG_NOSIGNAL|MSG_WAITFORONE|MSG_FASTOPEN|0x18380010}, msg_len=37}], 2, MSG_NOSIGNAL) = 2
poll([{fd=3, events=POLLIN}], 1, 5000)  = 1 ([{fd=3, revents=POLLIN}])
ioctl(3, FIONREAD, [132])               = 0
recvfrom(3, "+\27\201\200\0\1\0\4\0\0\0\0\4smtp\4mail\5yahoo\3com"..., 2048, 0, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("127.0.0.53")}, [28->16]) = 132
poll([{fd=3, events=POLLIN}], 1, 4980)  = 1 ([{fd=3, revents=POLLIN}])
ioctl(3, FIONREAD, [84])                = 0
recvfrom(3, "\254)\201\200\0\1\0\1\0\0\0\0\4smtp\4mail\5yahoo\3com"..., 65536, 0, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("127.0.0.53")}, [28->16]) = 84
close(3)                                = 0
openat(AT_FDCWD, "/etc/gai.conf", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2584, ...}) = 0
fstat(3, {st_mode=S_IFREG|0644, st_size=2584, ...}) = 0
read(3, "# Configuration for getaddrinfo("..., 4096) = 2584
read(3, "", 4096)                       = 0
close(3)                                = 0
futex(0x7f8933a2e044, FUTEX_WAKE_PRIVATE, 2147483647) = 0
socket(AF_NETLINK, SOCK_RAW, NETLINK_ROUTE) = 3
bind(3, {sa_family=AF_NETLINK, nl_pid=0, nl_groups=00000000}, 12) = 0
getsockname(3, {sa_family=AF_NETLINK, nl_pid=4256, nl_groups=00000000}, [12]) = 0
sendto(3, {{len=20, type=RTM_GETADDR, flags=NLM_F_REQUEST|NLM_F_DUMP, seq=1549743216, pid=0}, {ifa_family=AF_UNSPEC, ...}}, 20, 0, {sa_family=AF_NETLINK, nl_pid=0, nl_groups=00000000}, 12) = 20
recvmsg(3, {msg_name={sa_family=AF_NETLINK, nl_pid=0, nl_groups=00000000}, msg_namelen=12, msg_iov=[{iov_base=[{{len=76, type=RTM_NEWADDR, flags=NLM_F_MULTI, seq=1549743216, pid=4256}, {ifa_family=AF_INET, ifa_prefixlen=8, ifa_flags=IFA_F_PERMANENT, ifa_scope=RT_SCOPE_HOST, ifa_index=if_nametoindex("lo")}, [{{nla_len=8, nla_type=IFA_ADDRESS}, 127.0.0.1}, {{nla_len=8, nla_type=IFA_LOCAL}, 127.0.0.1}, {{nla_len=7, nla_type=IFA_LABEL}, "lo"}, {{nla_len=8, nla_type=IFA_FLAGS}, IFA_F_PERMANENT}, {{nla_len=20, nla_type=IFA_CACHEINFO}, {ifa_prefered=4294967295, ifa_valid=4294967295, cstamp=753, tstamp=753}}]}, {{len=88, type=RTM_NEWADDR, flags=NLM_F_MULTI, seq=1549743216, pid=4256}, {ifa_family=AF_INET, ifa_prefixlen=24, ifa_flags=0, ifa_scope=RT_SCOPE_UNIVERSE, ifa_index=if_nametoindex("enp1s0")}, [{{nla_len=8, nla_type=IFA_ADDRESS}, 192.168.254.31}, {{nla_len=8, nla_type=IFA_LOCAL}, 192.168.254.31}, {{nla_len=8, nla_type=IFA_BROADCAST}, 192.168.254.255}, {{nla_len=11, nla_type=IFA_LABEL}, "enp1s0"}, {{nla_len=8, nla_type=IFA_FLAGS}, IFA_F_NOPREFIXROUTE}, {{nla_len=20, nla_type=IFA_CACHEINFO}, {ifa_prefered=85992, ifa_valid=85992, cstamp=63900, tstamp=63910}}]}], iov_len=4096}], msg_iovlen=1, msg_controllen=0, msg_flags=0}, 0) = 164
recvmsg(3, {msg_name={sa_family=AF_NETLINK, nl_pid=0, nl_groups=00000000}, msg_namelen=12, msg_iov=[{iov_base=[{{len=72, type=RTM_NEWADDR, flags=NLM_F_MULTI, seq=1549743216, pid=4256}, {ifa_family=AF_INET6, ifa_prefixlen=128, ifa_flags=IFA_F_PERMANENT, ifa_scope=RT_SCOPE_HOST, ifa_index=if_nametoindex("lo")}, [{{nla_len=20, nla_type=IFA_ADDRESS}, ::1}, {{nla_len=20, nla_type=IFA_CACHEINFO}, {ifa_prefered=4294967295, ifa_valid=4294967295, cstamp=753, tstamp=753}}, {{nla_len=8, nla_type=IFA_FLAGS}, IFA_F_PERMANENT}]}, {{len=72, type=RTM_NEWADDR, flags=NLM_F_MULTI, seq=1549743216, pid=4256}, {ifa_family=AF_INET6, ifa_prefixlen=64, ifa_flags=IFA_F_PERMANENT, ifa_scope=RT_SCOPE_LINK, ifa_index=if_nametoindex("enp1s0")}, [{{nla_len=20, nla_type=IFA_ADDRESS}, fe80::3340:8121:de10:5e6c}, {{nla_len=20, nla_type=IFA_CACHEINFO}, {ifa_prefered=4294967295, ifa_valid=4294967295, cstamp=62839, tstamp=63036}}, {{nla_len=8, nla_type=IFA_FLAGS}, IFA_F_PERMANENT|IFA_F_NOPREFIXROUTE}]}], iov_len=4096}], msg_iovlen=1, msg_controllen=0, msg_flags=0}, 0) = 144
recvmsg(3, {msg_name={sa_family=AF_NETLINK, nl_pid=0, nl_groups=00000000}, msg_namelen=12, msg_iov=[{iov_base={{len=20, type=NLMSG_DONE, flags=NLM_F_MULTI, seq=1549743216, pid=4256}, 0}, iov_len=4096}], msg_iovlen=1, msg_controllen=0, msg_flags=0}, 0) = 20
close(3)                                = 0
socket(AF_INET, SOCK_DGRAM|SOCK_CLOEXEC, IPPROTO_IP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(587), sin_addr=inet_addr("67.195.228.95")}, 16) = 0
getsockname(3, {sa_family=AF_INET, sin_port=htons(38543), sin_addr=inet_addr("192.168.254.31")}, [28->16]) = 0
connect(3, {sa_family=AF_UNSPEC, sa_data="\0\0\0\0\0\0\0\0\0\0\0\0\0\0"}, 16) = 0
connect(3, {sa_family=AF_INET, sin_port=htons(587), sin_addr=inet_addr("74.6.141.43")}, 16) = 0
getsockname(3, {sa_family=AF_INET, sin_port=htons(57967), sin_addr=inet_addr("192.168.254.31")}, [28->16]) = 0
connect(3, {sa_family=AF_UNSPEC, sa_data="\0\0\0\0\0\0\0\0\0\0\0\0\0\0"}, 16) = 0
connect(3, {sa_family=AF_INET, sin_port=htons(587), sin_addr=inet_addr("98.136.96.80")}, 16) = 0
getsockname(3, {sa_family=AF_INET, sin_port=htons(49852), sin_addr=inet_addr("192.168.254.31")}, [28->16]) = 0
close(3)                                = 0
socket(AF_INET, SOCK_STREAM, IPPROTO_TCP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(587), sin_addr=inet_addr("67.195.228.95")}, 16) = -1 ETIMEDOUT (Connection timed out)
socket(AF_INET, SOCK_STREAM, IPPROTO_TCP) = 4
connect(4, {sa_family=AF_INET, sin_port=htons(587), sin_addr=inet_addr("74.6.141.43")}, 16
```

---

### Post by dmnur on 2019-02-09
[quote=raleigh3]```
smtp.mail.yahoo.com:587
```[/quote]

Why 587? In the first post it's 465 in the config file.

So, with port 465 you need **UseTLS=YES**, and there it was.
But for port 587 this won't work, you need **UseSTARTTLS=YES** instead.

Fix your config file using one of these options and try again.

---

### Post by raleigh3 on 2019-02-09
Ok. I used port 587 and [B]UseSTARTTLS=YES.

Sending email.
ssmtp: Cannot open smtp.mail.yahoo.com:587
[/B]

---

### Post by dmnur on 2019-02-09
Generate **ssmtp.trace** again. Also, please show your config as it is now.

**UPD:** it would also be helpful in troubleshooting if you run this command and show its output:
```
openssl s_client -connect smtp.mail.yahoo.com:587 -starttls smtp
```

---

### Post by raleigh3 on 2019-02-09
Is mail.txt supposed to contain my real email address?

```

execve("/usr/sbin/ssmtp", ["ssmtp", "-t", "-v"], 0x7fff44e90ef0 /* 18 vars */) = 0
access("/etc/suid-debug", F_OK)         = -1 ENOENT (No such file or directory)
brk(NULL)                               = 0x556bbc00f000
fcntl(0, F_GETFD)                       = 0
fcntl(1, F_GETFD)                       = 0
fcntl(2, F_GETFD)                       = 0
access("/etc/suid-debug", F_OK)         = -1 ENOENT (No such file or directory)
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
access("/etc/ld.so.preload", R_OK)      = 0
openat(AT_FDCWD, "/etc/ld.so.preload", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=0, ...}) = 0
close(3)                                = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=143012, ...}) = 0
mmap(NULL, 143012, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f9209340000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libgnutls-openssl.so.27", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P-\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=34656, ...}) = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9209365000
mmap(NULL, 2129936, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9208f30000
mprotect(0x7f9208f38000, 2093056, PROT_NONE) = 0
mmap(0x7f9209137000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7000) = 0x7f9209137000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\3\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\260\34\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=2030544, ...}) = 0
mmap(NULL, 4131552, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9208b38000
mprotect(0x7f9208d1f000, 2097152, PROT_NONE) = 0
mmap(0x7f9208f1f000, 24576, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1e7000) = 0x7f9208f1f000
mmap(0x7f9208f25000, 15072, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f9208f25000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libgnutls.so.30", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\207\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1457760, ...}) = 0
mmap(NULL, 3558216, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f92087d0000
mprotect(0x7f9208927000, 2097152, PROT_NONE) = 0
mmap(0x7f9208b27000, 53248, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x157000) = 0x7f9208b27000
mmap(0x7f9208b34000, 2888, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f9208b34000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libz.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220\37\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=116960, ...}) = 0
mmap(NULL, 2212016, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f92085b0000
mprotect(0x7f92085cc000, 2093056, PROT_NONE) = 0
mmap(0x7f92087cb000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1b000) = 0x7f92087cb000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libp11-kit.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\263\2\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1237640, ...}) = 0
mmap(NULL, 3334512, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9208280000
mprotect(0x7f920839a000, 2097152, PROT_NONE) = 0
mmap(0x7f920859a000, 81920, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x11a000) = 0x7f920859a000
mmap(0x7f92085ae000, 368, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f92085ae000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libidn2.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\25\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=116656, ...}) = 0
mmap(NULL, 2211864, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9208060000
mprotect(0x7f920807c000, 2093056, PROT_NONE) = 0
mmap(0x7f920827b000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1b000) = 0x7f920827b000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libunistring.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\365\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=1562664, ...}) = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f9209363000
mmap(NULL, 3660040, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9207ce0000
mprotect(0x7f9207e5a000, 2097152, PROT_NONE) = 0
mmap(0x7f920805a000, 16384, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x17a000) = 0x7f920805a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libtasn1.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220)\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=75776, ...}) = 0
mmap(NULL, 2171592, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9207ac8000
mprotect(0x7f9207ad9000, 2097152, PROT_NONE) = 0
mmap(0x7f9207cd9000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x11000) = 0x7f9207cd9000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libnettle.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\340\200\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=219304, ...}) = 0
mmap(NULL, 2314384, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9207890000
mprotect(0x7f92078c4000, 2093056, PROT_NONE) = 0
mmap(0x7f9207ac3000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x33000) = 0x7f9207ac3000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libhogweed.so.4", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0 j\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=211704, ...}) = 0
mmap(NULL, 2306760, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9207658000
mprotect(0x7f920768b000, 2093056, PROT_NONE) = 0
mmap(0x7f920788a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x32000) = 0x7f920788a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libgmp.so.10", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\223\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=526688, ...}) = 0
mmap(NULL, 2621888, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f92073d0000
mprotect(0x7f920744f000, 2097152, PROT_NONE) = 0
mmap(0x7f920764f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x7f000) = 0x7f920764f000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/usr/lib/x86_64-linux-gnu/libffi.so.6", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0@\27\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=31032, ...}) = 0
mmap(NULL, 2127368, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f92071c8000
mprotect(0x7f92071cf000, 2093056, PROT_NONE) = 0
mmap(0x7f92073ce000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6000) = 0x7f92073ce000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libdl.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\16\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=14560, ...}) = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f920933e000
mmap(NULL, 2109712, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9206fc0000
mprotect(0x7f9206fc3000, 2093056, PROT_NONE) = 0
mmap(0x7f92071c2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x2000) = 0x7f92071c2000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libpthread.so.0", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0000b\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0755, st_size=144976, ...}) = 0
mmap(NULL, 2221184, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9206da0000
mprotect(0x7f9206dba000, 2093056, PROT_NONE) = 0
mmap(0x7f9206fb9000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x19000) = 0x7f9206fb9000
mmap(0x7f9206fbb000, 13440, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f9206fbb000
close(3)                                = 0
mmap(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x7f920933c000
arch_prctl(ARCH_SET_FS, 0x7f920933cb80) = 0
mprotect(0x7f9208f1f000, 16384, PROT_READ) = 0
mprotect(0x7f9206fb9000, 4096, PROT_READ) = 0
mprotect(0x7f92071c2000, 4096, PROT_READ) = 0
mprotect(0x7f92073ce000, 4096, PROT_READ) = 0
mprotect(0x7f920764f000, 4096, PROT_READ) = 0
mprotect(0x7f9207ac3000, 8192, PROT_READ) = 0
mprotect(0x7f920788a000, 4096, PROT_READ) = 0
mprotect(0x7f9207cd9000, 4096, PROT_READ) = 0
mprotect(0x7f920805a000, 12288, PROT_READ) = 0
mprotect(0x7f920827b000, 4096, PROT_READ) = 0
mprotect(0x7f920859a000, 40960, PROT_READ) = 0
mprotect(0x7f92087cb000, 4096, PROT_READ) = 0
mprotect(0x7f9208b27000, 49152, PROT_READ) = 0
mprotect(0x7f9209137000, 4096, PROT_READ) = 0
mprotect(0x556bbb2d2000, 4096, PROT_READ) = 0
mprotect(0x7f9209367000, 4096, PROT_READ) = 0
munmap(0x7f9209340000, 143012)          = 0
set_tid_address(0x7f920933ce50)         = 5108
set_robust_list(0x7f920933ce60, 24)     = 0
rt_sigaction(SIGRTMIN, {sa_handler=0x7f9206da5cb0, sa_mask=[], sa_flags=SA_RESTORER|SA_SIGINFO, sa_restorer=0x7f9206db2890}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {sa_handler=0x7f9206da5d50, sa_mask=[], sa_flags=SA_RESTORER|SA_RESTART|SA_SIGINFO, sa_restorer=0x7f9206db2890}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
prlimit64(0, RLIMIT_STACK, NULL, {rlim_cur=8192*1024, rlim_max=RLIM64_INFINITY}) = 0
futex(0x7f92085ae0e0, FUTEX_WAKE_PRIVATE, 2147483647) = 0
brk(NULL)                               = 0x556bbc00f000
brk(0x556bbc030000)                     = 0x556bbc030000
getrandom("\x60", 1, GRND_NONBLOCK)     = 1
stat("/etc/gnutls/default-priorities", 0x7ffe060c8950) = -1 ENOENT (No such file or directory)
rt_sigaction(SIGHUP, {sa_handler=SIG_IGN, sa_mask=[HUP], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f9208b76f20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGINT, {sa_handler=SIG_IGN, sa_mask=[INT], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f9208b76f20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGTTIN, {sa_handler=SIG_IGN, sa_mask=[TTIN], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f9208b76f20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
rt_sigaction(SIGTTOU, {sa_handler=SIG_IGN, sa_mask=[TTOU], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f9208b76f20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
uname({sysname="Linux", nodename="7", ...}) = 0
getuid()                                = 0
socket(AF_UNIX, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_UNIX, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
socket(AF_UNIX, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_UNIX, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
openat(AT_FDCWD, "/etc/nsswitch.conf", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=556, ...}) = 0
read(3, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 556
read(3, "", 4096)                       = 0
close(3)                                = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=143012, ...}) = 0
mmap(NULL, 143012, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f9209318000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_compat.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\240\22\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=39744, ...}) = 0
mmap(NULL, 2136256, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9206b90000
mprotect(0x7f9206b98000, 2097152, PROT_NONE) = 0
mmap(0x7f9206d98000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x8000) = 0x7f9206d98000
close(3)                                = 0
mprotect(0x7f9206d98000, 4096, PROT_READ) = 0
munmap(0x7f9209318000, 143012)          = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=143012, ...}) = 0
mmap(NULL, 143012, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f9209318000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_nis.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0p \0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=47576, ...}) = 0
mmap(NULL, 2143624, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9206980000
mprotect(0x7f920698b000, 2093056, PROT_NONE) = 0
mmap(0x7f9206b8a000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa000) = 0x7f9206b8a000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnsl.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\220@\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=97176, ...}) = 0
mmap(NULL, 2202200, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9206760000
mprotect(0x7f9206777000, 2093056, PROT_NONE) = 0
mmap(0x7f9206976000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x16000) = 0x7f9206976000
mmap(0x7f9206978000, 6744, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f9206978000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_files.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P#\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=47568, ...}) = 0
mmap(NULL, 2168632, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9206548000
mprotect(0x7f9206553000, 2093056, PROT_NONE) = 0
mmap(0x7f9206752000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa000) = 0x7f9206752000
mmap(0x7f9206754000, 22328, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f9206754000
close(3)                                = 0
mprotect(0x7f9206752000, 4096, PROT_READ) = 0
mprotect(0x7f9206976000, 4096, PROT_READ) = 0
mprotect(0x7f9206b8a000, 4096, PROT_READ) = 0
munmap(0x7f9209318000, 143012)          = 0
openat(AT_FDCWD, "/etc/passwd", O_RDONLY|O_CLOEXEC) = 3
lseek(3, 0, SEEK_CUR)                   = 0
fstat(3, {st_mode=S_IFREG|0644, st_size=2637, ...}) = 0
mmap(NULL, 2637, PROT_READ, MAP_SHARED, 3, 0) = 0x7f9209360000
lseek(3, 2637, SEEK_SET)                = 2637
munmap(0x7f9209360000, 2637)            = 0
close(3)                                = 0
openat(AT_FDCWD, "/etc/localtime", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=3585, ...}) = 0
fstat(3, {st_mode=S_IFREG|0644, st_size=3585, ...}) = 0
read(3, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\7\0\0\0\7\0\0\0\0"..., 4096) = 3585
lseek(3, -2281, SEEK_CUR)               = 1304
read(3, "TZif2\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\0\7\0\0\0\7\0\0\0\0"..., 4096) = 2281
brk(0x556bbc051000)                     = 0x556bbc051000
close(3)                                = 0
openat(AT_FDCWD, "/etc/ssmtp/ssmtp.conf", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0640, st_size=722, ...}) = 0
read(3, "#\n# Config file for sSMTP sendma"..., 4096) = 722
read(3, "", 4096)                       = 0
close(3)                                = 0
openat(AT_FDCWD, "/etc/ssmtp/revaliases", O_RDONLY) = 3
fstat(3, {st_mode=S_IFREG|0640, st_size=255, ...}) = 0
read(3, "# sSMTP aliases\n# \n# Format:\tloc"..., 4096) = 255
read(3, "", 4096)                       = 0
close(3)                                = 0
fstat(0, {st_mode=S_IFREG|0664, st_size=75, ...}) = 0
read(0, "From: [EMAIL="a7@yahoo.com"]a7@yahoo.com[/EMAIL]\nTo: a7@yahoo."..., 4096) = 75
rt_sigaction(SIGALRM, {sa_handler=0x556bbb0cc560, sa_mask=[ALRM], sa_flags=SA_RESTORER|SA_RESTART, sa_restorer=0x7f9208b76f20}, {sa_handler=SIG_DFL, sa_mask=[], sa_flags=0}, 8) = 0
alarm(600)                              = 0
socket(AF_UNIX, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_UNIX, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
socket(AF_UNIX, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_UNIX, sun_path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
stat("/etc/resolv.conf", {st_mode=S_IFREG|0644, st_size=734, ...}) = 0
openat(AT_FDCWD, "/etc/host.conf", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=92, ...}) = 0
read(3, "# The \"order\" line is only used "..., 4096) = 92
read(3, "", 4096)                       = 0
close(3)                                = 0
futex(0x7f9208f27ba4, FUTEX_WAKE_PRIVATE, 2147483647) = 0
openat(AT_FDCWD, "/etc/resolv.conf", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=734, ...}) = 0
read(3, "# This file is managed by man:sy"..., 4096) = 734
read(3, "", 4096)                       = 0
close(3)                                = 0
openat(AT_FDCWD, "/etc/hosts", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0664, st_size=470467, ...}) = 0
read(3, "# This MVPS HOSTS file is a free"..., 4096) = 4096
read(3, "0.0 admarket.cz\r\n0.0.0.0 www.adm"..., 4096) = 4096
read(3, ".0.0 banners.affiliatefuture.com"..., 4096) = 4096
read(3, "\r\n0.0.0.0 www.bettertextads.com\r"..., 4096) = 4096
read(3, "0.0 [www.contaxe.com\r\n0.0.0.0]("http://www.contaxe.com\r\n0.0.0.0") www"..., 4096) = 4096
read(3, "es\r\n0.0.0.0 s1415903351.t.eloqua"..., 4096) = 4096
read(3, ".0.0 getrank.net\r\n0.0.0.0 getroc"..., 4096) = 4096
read(3, "rmatm.com\r\n0.0.0.0 pcbutts1.soft"..., 4096) = 4096
read(3, "tingware.com\r\n0.0.0.0 s1.listrak"..., 4096) = 4096
read(3, "rking Service]\r\n0.0.0.0 www.ndpa"..., 4096) = 4096
read(3, "0 viewer.peer39.com\r\n0.0.0.0 ban"..., 4096) = 4096
read(3, ".0.0 mct.rkdms.com\r\n0.0.0.0 ei.r"..., 4096) = 4096
read(3, "l.com\r\n0.0.0.0 www.start-page.or"..., 4096) = 4096
read(3, "r.truehits.net\r\n0.0.0.0 origin-t"..., 4096) = 4096
read(3, "www.webhits.de\r\n0.0.0.0 ads.webk"..., 4096) = 4096
read(3, ".3conline.com\r\n0.0.0.0 imgad2.3c"..., 4096) = 4096
read(3, "04.45.255.255]\r\n0.0.0.0 hitslap."..., 4096) = 4096
read(3, "0.0 stx0.sextracker.com\r\n0.0.0.0"..., 4096) = 4096
read(3, "0 indexhu.adocean.pl\r\n0.0.0.0 in"..., 4096) = 4096
read(3, "\r\n0.0.0.0 tag.aticdn.net\r\n0.0.0."..., 4096) = 4096
read(3, "0.0 fast.everydayhealth.demdex.n"..., 4096) = 4096
read(3, ".analytics.edgesuite.net #[Akama"..., 4096) = 4096
read(3, "0.0 stream1.marketwatch.fyre.co\r"..., 4096) = 4096
read(3, "-p.mythings.com\r\n0.0.0.0 abandon"..., 4096) = 4096
read(3, "0 ads.mopub.com\r\n0.0.0.0 papi.my"..., 4096) = 4096
read(3, "0.0 adsys.adk2x.com\r\n0.0.0.0 s.a"..., 4096) = 4096
read(3, ".net\r\n0.0.0.0 d24n15hnbwhuhn.clo"..., 4096) = 4096
read(3, "m\r\n# [Amazon.com][AS16509][54.20"..., 4096) = 4096
read(3, "m\r\n0.0.0.0 cdn.ip.inpwrd.com\r\n0."..., 4096) = 4096
read(3, "com\r\n0.0.0.0 pages-stats.rbl.ms\r"..., 4096) = 4096
read(3, "ww.supersonicads.com\r\n0.0.0.0 ap"..., 4096) = 4096
read(3, "i.com\r\n0.0.0.0 logc8.xiti.com\r\n0"..., 4096) = 4096
read(3, "ifymedia.com\r\n0.0.0.0 x.clickcer"..., 4096) = 4096
read(3, "hit.stat24.com\r\n0.0.0.0 ua4.hit."..., 4096) = 4096
read(3, "er42.bravenet.com\r\n0.0.0.0 count"..., 4096) = 4096
read(3, ".23.132.248 - 217.23.132.255]\r\n0"..., 4096) = 4096
read(3, "bBug]\r\n0.0.0.0 activity.serving-"..., 4096) = 4096
read(3, " - 104.31.255.255]\r\n0.0.0.0 try."..., 4096) = 4096
read(3, " cdn.popmyads.com\r\n0.0.0.0 asset"..., 4096) = 4096
read(3, ".0.0 ua.adriver.ru\r\n0.0.0.0 ua-c"..., 4096) = 4096
read(3, ".com\r\n0.0.0.0 static.criteo.net\r"..., 4096) = 4096
read(3, "pmedownload.com\r\n0.0.0.0 www.mp3"..., 4096) = 4096
read(3, "o.com\r\n0.0.0.0 adsatt.espn.starw"..., 4096) = 4096
read(3, "conviva.com #[affects videos]\r\n0"..., 4096) = 4096
read(3, "bx.com\r\n0.0.0.0 pixel.facebook.c"..., 4096) = 4096
read(3, "2915dc.v.fwmrm.net\r\n0.0.0.0 2912"..., 4096) = 4096
read(3, "ro.hit.gemius.pl\r\n0.0.0.0 axel.h"..., 4096) = 4096
read(3, "it.stat.pl\r\n0.0.0.0 s1.hit.stat."..., 4096) = 4096
read(3, "traffic.com\r\n0.0.0.0 codeads.com"..., 4096) = 4096
read(3, "om\r\n0.0.0.0 speednetwork14.adk2x"..., 4096) = 4096
read(3, "488352.fls.doubleclick.net\r\n0.0."..., 4096) = 4096
read(3, ".com\r\n0.0.0.0 target.e-generator"..., 4096) = 4096
read(3, "chsys.com\r\n0.0.0.0 media.brandre"..., 4096) = 4096
read(3, "Parked.com][AS32592][69.46.224.0"..., 4096) = 4096
read(3, "0 - 212.162.15.255]\r\n0.0.0.0 lin"..., 4096) = 4096
read(3, "[Interland / Web.com][AS36476][2"..., 4096) = 4096
read(3, ".net\r\n# [Internap / Atrinsic][AS"..., 4096) = 4096
read(3, "ebtrekk.net\r\n0.0.0.0 jade01.webt"..., 4096) = 4096
read(3, "0.0 image1.cecash.com\r\n0.0.0.0 c"..., 4096) = 4096
read(3, "wordpress.com #[WebBug]\r\n0.0.0.0"..., 4096) = 4096
read(3, "m\r\n# [Leaseweb][AS16265][AS60781"..., 4096) = 4096
read(3, "m\r\n0.0.0.0 7457.accessaw.bluesee"..., 4096) = 4096
read(3, "content.exoticads.com\r\n0.0.0.0 m"..., 4096) = 4096
read(3, "ru\r\n0.0.0.0 top.list.ru\r\n0.0.0.0"..., 4096) = 4096
read(3, "075][137.116.0.0 - 137.116.255.2"..., 4096) = 4096
read(3, "92.140.47]\r\n0.0.0.0 flashadtools"..., 4096) = 4096
read(3, "0 - 66.29.127.255]\r\n# [Net Acces"..., 4096) = 4096
read(3, "0 - 212.143.22.255]\r\n0.0.0.0 ads"..., 4096) = 4096
read(3, "\n0.0.0.0 mini.activeshopper.com\r"..., 4096) = 4096
read(3, "0.0.0.0 media-6.vpptechnologies."..., 4096) = 4096
read(3, ".0.0.0 daimlerag.d2.sc.omtrdc.ne"..., 4096) = 4096
read(3, "vgtechnologies.112.2o7.net\r\n0.0."..., 4096) = 4096
read(3, "asterglobal.112.2o7.net\r\n0.0.0.0"..., 4096) = 4096
read(3, "112.2o7.net\r\n0.0.0.0 gntbcstkusa"..., 4096) = 4096
read(3, "2.2o7.net\r\n0.0.0.0 mghickoryreco"..., 4096) = 4096
read(3, ".0.0.0 newsquestdigitalmedia.122"..., 4096) = 4096
read(3, ".112.2o7.net\r\n0.0.0.0 rainbowmed"..., 4096) = 4096
read(3, " timeessence.122.2o7.net\r\n0.0.0."..., 4096) = 4096
read(3, "ziffdavisglobal.112.2o7.net\r\n0.0"..., 4096) = 4096
read(3, "ics.fnac.es\r\n0.0.0.0 sc-forbes.f"..., 4096) = 4096
read(3, ".0.0 stats2.vanityfair.com\r\n0.0."..., 4096) = 4096
read(3, "e-adhese.gva.be\r\n0.0.0.0 pebble-"..., 4096) = 4096
read(3, "vedbyopenx.com\r\n0.0.0.0 ox-d.soc"..., 4096) = 4096
read(3, "x-traceur.com\r\n# [Ovh Sas][217.1"..., 4096) = 4096
read(3, "ads.dt.mydas.mobi\r\n0.0.0.0 bank0"..., 4096) = 4096
read(3, ".telemetryverification.net\r\n0.0."..., 4096) = 4096
read(3, "r-203.sv2.biz\r\n0.0.0.0 ktu.sv2.b"..., 4096) = 4096
read(3, "0 users.effectivebrand.com\r\n0.0."..., 4096) = 4096
read(3, ".61.179.95]\r\n0.0.0.0 www.trackin"..., 4096) = 4096
read(3, ".0.0.0 ad.where.com\r\n# [Rambler]"..., 4096) = 4096
read(3, " sa.scorecardresearch.com\r\n# [Sa"..., 4096) = 4096
read(3, ".0.0 - 173.204.255.255]\r\n# [Serv"..., 4096) = 4096
read(3, "\n0.0.0.0 codiceisp.shinystat.it\r"..., 4096) = 4096
read(3, "0.0 eclkspsa.com\r\n0.0.0.0 tags1."..., 4096) = 4096
read(3, "86.255.255]\r\n0.0.0.0 ads.aboveto"..., 4096) = 4096
read(3, "5]\r\n0.0.0.0 www.clixtrac.com\r\n0."..., 4096) = 4096
read(3, "0.0 [www.adengage.com\r\n#]("http://www.adengage.com\r\n#") [TekChan"..., 4096) = 4096
read(3, "m\r\n0.0.0.0 wrap.tradedoubler.com"..., 4096) = 4096
read(3, "unter.yakcash.com\r\n# [Theplanet."..., 4096) = 4096
read(3, "ivatamateure.com #[Sagnet Group]"..., 4096) = 4096
read(3, "34.207.255]\r\n# [ValueClick / Com"..., 4096) = 4096
read(3, "computerwoche.de.intellitxt.com\r"..., 4096) = 4096
read(3, "nology.uk.intellitxt.com\r\n0.0.0."..., 4096) = 4096
read(3, "ritysmackblog.us.intellitxt.com\r"..., 4096) = 4096
read(3, "\r\n0.0.0.0 forbes.us.intellitxt.c"..., 4096) = 4096
read(3, "itxt.com\r\n0.0.0.0 investopedia.u"..., 4096) = 4096
read(3, ".com\r\n0.0.0.0 ninjadude.us.intel"..., 4096) = 4096
read(3, "ntellitxt.com\r\n0.0.0.0 tenmagazi"..., 4096) = 4096
read(3, "l\r\n0.0.0.0 3.googlenews.xorg.pl\r"..., 4096) = 4096
read(3, "com\r\n0.0.0.0 www.professionalcas"..., 4096) = 4096
read(3, "]\r\n0.0.0.0 fttcj.com\r\n0.0.0.0 ad"..., 4096) = 4096
read(3, "oasc12016.247realmedia.com\r\n0.0."..., 4096) = 4096
read(3, "now.com\r\n0.0.0.0 oascentral.onwi"..., 4096) = 4096
read(3, "O Communications][AS2828][65.104"..., 4096) = 4096
read(3, ".0.0.0 sp.analytics.yahoo.com\r\n0"..., 4096) = 3523
read(3, "", 4096)                       = 0
close(3)                                = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=143012, ...}) = 0
mmap(NULL, 143012, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f9209318000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_mdns4_minimal.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0P\v\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=10160, ...}) = 0
mmap(NULL, 2105360, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9206340000
mprotect(0x7f9206342000, 2093056, PROT_NONE) = 0
mmap(0x7f9206541000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x1000) = 0x7f9206541000
close(3)                                = 0
mprotect(0x7f9206541000, 4096, PROT_READ) = 0
munmap(0x7f9209318000, 143012)          = 0
openat(AT_FDCWD, "/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=143012, ...}) = 0
mmap(NULL, 143012, PROT_READ, MAP_PRIVATE, 3, 0) = 0x7f9209318000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libnss_dns.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\0\200\17\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=26936, ...}) = 0
mmap(NULL, 2121952, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9206138000
mprotect(0x7f920613d000, 2097152, PROT_NONE) = 0
mmap(0x7f920633d000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x5000) = 0x7f920633d000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
openat(AT_FDCWD, "/lib/x86_64-linux-gnu/libresolv.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\2\1\1\0\0\0\0\0\0\0\0\0\3\0>\0\1\0\0\00008\0\0\0\0\0\0"..., 832) = 832
fstat(3, {st_mode=S_IFREG|0644, st_size=101168, ...}) = 0
mmap(NULL, 2206336, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0x7f9205f18000
mprotect(0x7f9205f2f000, 2097152, PROT_NONE) = 0
mmap(0x7f920612f000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x17000) = 0x7f920612f000
mmap(0x7f9206131000, 6784, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0x7f9206131000
close(3)                                = 0
mprotect(0x7f920612f000, 4096, PROT_READ) = 0
mprotect(0x7f920633d000, 4096, PROT_READ) = 0
munmap(0x7f9209318000, 143012)          = 0
socket(AF_INET, SOCK_DGRAM|SOCK_CLOEXEC|SOCK_NONBLOCK, IPPROTO_IP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("127.0.0.53")}, 16) = 0
poll([{fd=3, events=POLLOUT}], 1, 0)    = 1 ([{fd=3, revents=POLLOUT}])
sendmmsg(3, [{msg_hdr={msg_name=NULL, msg_namelen=0, msg_iov=[{iov_base="\253T\1\0\0\1\0\0\0\0\0\1\4smtp\4mail\5yahoo\3com"..., iov_len=48}], msg_iovlen=1, msg_controllen=0, msg_flags=MSG_OOB}, msg_len=48}, {msg_hdr={msg_name=NULL, msg_namelen=0, msg_iov=[{iov_base="\327j\1\0\0\1\0\0\0\0\0\1\4smtp\4mail\5yahoo\3com"..., iov_len=48}], msg_iovlen=1, msg_controllen=0, msg_flags=0}, msg_len=48}], 2, MSG_NOSIGNAL) = 2
poll([{fd=3, events=POLLIN}], 1, 5000)  = 1 ([{fd=3, revents=POLLIN}])
ioctl(3, FIONREAD, [143])               = 0
recvfrom(3, "\253T\201\200\0\1\0\4\0\0\0\1\4smtp\4mail\5yahoo\3com"..., 2048, 0, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("127.0.0.53")}, [28->16]) = 143
poll([{fd=3, events=POLLIN}], 1, 4974)  = 1 ([{fd=3, revents=POLLIN}])
ioctl(3, FIONREAD, [95])                = 0
recvfrom(3, "\327j\201\200\0\1\0\1\0\0\0\1\4smtp\4mail\5yahoo\3com"..., 65536, 0, {sa_family=AF_INET, sin_port=htons(53), sin_addr=inet_addr("127.0.0.53")}, [28->16]) = 95
close(3)                                = 0
openat(AT_FDCWD, "/etc/gai.conf", O_RDONLY|O_CLOEXEC) = 3
fstat(3, {st_mode=S_IFREG|0644, st_size=2584, ...}) = 0
fstat(3, {st_mode=S_IFREG|0644, st_size=2584, ...}) = 0
read(3, "# Configuration for getaddrinfo("..., 4096) = 2584
read(3, "", 4096)                       = 0
close(3)                                = 0
futex(0x7f9208f26044, FUTEX_WAKE_PRIVATE, 2147483647) = 0
socket(AF_NETLINK, SOCK_RAW, NETLINK_ROUTE) = 3
bind(3, {sa_family=AF_NETLINK, nl_pid=0, nl_groups=00000000}, 12) = 0
getsockname(3, {sa_family=AF_NETLINK, nl_pid=5108, nl_groups=00000000}, [12]) = 0
sendto(3, {{len=20, type=RTM_GETADDR, flags=NLM_F_REQUEST|NLM_F_DUMP, seq=1549753411, pid=0}, {ifa_family=AF_UNSPEC, ...}}, 20, 0, {sa_family=AF_NETLINK, nl_pid=0, nl_groups=00000000}, 12) = 20
recvmsg(3, {msg_name={sa_family=AF_NETLINK, nl_pid=0, nl_groups=00000000}, msg_namelen=12, msg_iov=[{iov_base=[{{len=76, type=RTM_NEWADDR, flags=NLM_F_MULTI, seq=1549753411, pid=5108}, {ifa_family=AF_INET, ifa_prefixlen=8, ifa_flags=IFA_F_PERMANENT, ifa_scope=RT_SCOPE_HOST, ifa_index=if_nametoindex("lo")}, [{{nla_len=8, nla_type=IFA_ADDRESS}, 127.0.0.1}, {{nla_len=8, nla_type=IFA_LOCAL}, 127.0.0.1}, {{nla_len=7, nla_type=IFA_LABEL}, "lo"}, {{nla_len=8, nla_type=IFA_FLAGS}, IFA_F_PERMANENT}, {{nla_len=20, nla_type=IFA_CACHEINFO}, {ifa_prefered=4294967295, ifa_valid=4294967295, cstamp=753, tstamp=753}}]}, {{len=88, type=RTM_NEWADDR, flags=NLM_F_MULTI, seq=1549753411, pid=5108}, {ifa_family=AF_INET, ifa_prefixlen=24, ifa_flags=0, ifa_scope=RT_SCOPE_UNIVERSE, ifa_index=if_nametoindex("enp1s0")}, [{{nla_len=8, nla_type=IFA_ADDRESS}, 192.168.254.31}, {{nla_len=8, nla_type=IFA_LOCAL}, 192.168.254.31}, {{nla_len=8, nla_type=IFA_BROADCAST}, 192.168.254.255}, {{nla_len=11, nla_type=IFA_LABEL}, "enp1s0"}, {{nla_len=8, nla_type=IFA_FLAGS}, IFA_F_NOPREFIXROUTE}, {{nla_len=20, nla_type=IFA_CACHEINFO}, {ifa_prefered=86173, ifa_valid=86173, cstamp=1001067, tstamp=1001076}}]}], iov_len=4096}], msg_iovlen=1, msg_controllen=0, msg_flags=0}, 0) = 164
recvmsg(3, {msg_name={sa_family=AF_NETLINK, nl_pid=0, nl_groups=00000000}, msg_namelen=12, msg_iov=[{iov_base=[{{len=72, type=RTM_NEWADDR, flags=NLM_F_MULTI, seq=1549753411, pid=5108}, {ifa_family=AF_INET6, ifa_prefixlen=128, ifa_flags=IFA_F_PERMANENT, ifa_scope=RT_SCOPE_HOST, ifa_index=if_nametoindex("lo")}, [{{nla_len=20, nla_type=IFA_ADDRESS}, ::1}, {{nla_len=20, nla_type=IFA_CACHEINFO}, {ifa_prefered=4294967295, ifa_valid=4294967295, cstamp=753, tstamp=753}}, {{nla_len=8, nla_type=IFA_FLAGS}, IFA_F_PERMANENT}]}, {{len=72, type=RTM_NEWADDR, flags=NLM_F_MULTI, seq=1549753411, pid=5108}, {ifa_family=AF_INET6, ifa_prefixlen=64, ifa_flags=IFA_F_PERMANENT, ifa_scope=RT_SCOPE_LINK, ifa_index=if_nametoindex("enp1s0")}, [{{nla_len=20, nla_type=IFA_ADDRESS}, fe80::3340:8121:de10:5e6c}, {{nla_len=20, nla_type=IFA_CACHEINFO}, {ifa_prefered=4294967295, ifa_valid=4294967295, cstamp=999413, tstamp=999593}}, {{nla_len=8, nla_type=IFA_FLAGS}, IFA_F_PERMANENT|IFA_F_NOPREFIXROUTE}]}], iov_len=4096}], msg_iovlen=1, msg_controllen=0, msg_flags=0}, 0) = 144
recvmsg(3, {msg_name={sa_family=AF_NETLINK, nl_pid=0, nl_groups=00000000}, msg_namelen=12, msg_iov=[{iov_base={{len=20, type=NLMSG_DONE, flags=NLM_F_MULTI, seq=1549753411, pid=5108}, 0}, iov_len=4096}], msg_iovlen=1, msg_controllen=0, msg_flags=0}, 0) = 20
close(3)                                = 0
socket(AF_INET, SOCK_DGRAM|SOCK_CLOEXEC, IPPROTO_IP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(587), sin_addr=inet_addr("67.195.228.95")}, 16) = 0
getsockname(3, {sa_family=AF_INET, sin_port=htons(40719), sin_addr=inet_addr("192.168.254.31")}, [28->16]) = 0
connect(3, {sa_family=AF_UNSPEC, sa_data="\0\0\0\0\0\0\0\0\0\0\0\0\0\0"}, 16) = 0
connect(3, {sa_family=AF_INET, sin_port=htons(587), sin_addr=inet_addr("98.136.96.80")}, 16) = 0
getsockname(3, {sa_family=AF_INET, sin_port=htons(37172), sin_addr=inet_addr("192.168.254.31")}, [28->16]) = 0
connect(3, {sa_family=AF_UNSPEC, sa_data="\0\0\0\0\0\0\0\0\0\0\0\0\0\0"}, 16) = 0
connect(3, {sa_family=AF_INET, sin_port=htons(587), sin_addr=inet_addr("74.6.141.43")}, 16) = 0
getsockname(3, {sa_family=AF_INET, sin_port=htons(50521), sin_addr=inet_addr("192.168.254.31")}, [28->16]) = 0
close(3)                                = 0
socket(AF_INET, SOCK_STREAM, IPPROTO_TCP) = 3
connect(3, {sa_family=AF_INET, sin_port=htons(587), sin_addr=inet_addr("67.195.228.95")}, 16) = -1 ETIMEDOUT (Connection timed out)
socket(AF_INET, SOCK_STREAM, IPPROTO_TCP) = 4
connect(4, {sa_family=AF_INET, sin_port=htons(587), sin_addr=inet_addr("98.136.96.80")}, 16) = -1 ETIMEDOUT (Connection timed out)
socket(AF_INET, SOCK_STREAM, IPPROTO_TCP) = 5
connect(5, {sa_family=AF_INET, sin_port=htons(587), sin_addr=inet_addr("74.6.141.43")}, 16) = -1 ETIMEDOUT (Connection timed out)
getpid()                                = 5108
socket(AF_UNIX, SOCK_DGRAM|SOCK_CLOEXEC, 0) = 6
connect(6, {sa_family=AF_UNIX, sun_path="/dev/log"}, 110) = 0
sendto(6, "<19>Feb  9 17:10:03 sSMTP[5108]:"..., 86, MSG_NOSIGNAL, NULL, 0) = 86
close(6)                                = 0
write(2, "ssmtp: Cannot open smtp.mail.yah"..., 43) = 43
getpid()                                = 5108
socket(AF_UNIX, SOCK_DGRAM|SOCK_CLOEXEC, 0) = 6
connect(6, {sa_family=AF_UNIX, sun_path="/dev/log"}, 110) = 0
sendto(6, "<19>Feb  9 17:10:03 sSMTP[5108]:"..., 68, MSG_NOSIGNAL, NULL, 0) = 68
close(6)                                = 0
getuid()                                = 0
openat(AT_FDCWD, "/etc/passwd", O_RDONLY|O_CLOEXEC) = 6
lseek(6, 0, SEEK_CUR)                   = 0
fstat(6, {st_mode=S_IFREG|0644, st_size=2637, ...}) = 0
mmap(NULL, 2637, PROT_READ, MAP_SHARED, 6, 0) = 0x7f9209360000
lseek(6, 2637, SEEK_SET)                = 2637
munmap(0x7f9209360000, 2637)            = 0
close(6)                                = 0
ioctl(0, TCGETS, 0x7ffe060c6740)        = -1 ENOTTY (Inappropriate ioctl for device)
openat(AT_FDCWD, "/root/dead.letter", O_WRONLY|O_CREAT|O_APPEND, 0666) = 6
lseek(6, 0, SEEK_END)                   = 146
fstat(6, {st_mode=S_IFREG|0644, st_size=146, ...}) = 0
read(0, "", 4096)                       = 0
write(6, "\n\nJust testing.test email\n", 26) = 26
close(6)                                = 0
exit_group(1)                           = ?
+++ exited with 1 +++
```


```
#
# Config file for sSMTP sendmail
#
#  This files goes in /etc/ssmtp/
#
# The person who gets all mail for userids < 1000
# Make this empty to disable rewriting.
root=7@yahoo.com

# The place where the mail goes. The actual machine name is required no 
# MX records are consulted. Commonly mailhosts are named mail.domain.com

mailhub=smtp.mail.yahoo.com:587
# Where will the mail seem to come from?
rewriteDomain=yahoo.com

# The full hostname
hostname=7

AuthUser=notreal

AuthPass=trumpneedstogrowup
# Are users allowed to set their own From: address?
# YES - Allow the user to specify their own From: address
# NO - Use the system generated From: address
FromLineOverride=YES
#UseTLS=YES
UseSTARTTLS=YES
```

```
andy@7_~/Downloads/$ openssl s_client -connect smtp.mail.yahoo.com:587 -starttls smtp
140145534190016:error:0200206E:system library:connect:Connection timed out:../crypto/bio/b_sock2.c:108:
140145534190016:error:2008A067:BIO routines:BIO_connect:connect error:../crypto/bio/b_sock2.c:109:
140145534190016:error:0200206E:system library:connect:Connection timed out:../crypto/bio/b_sock2.c:108:
140145534190016:error:2008A067:BIO routines:BIO_connect:connect error:../crypto/bio/b_sock2.c:109:
140145534190016:error:0200206E:system library:connect:Connection timed out:../crypto/bio/b_sock2.c:108:
140145534190016:error:2008A067:BIO routines:BIO_connect:connect error:../crypto/bio/b_sock2.c:109:
connect:errno=110
```

---

### Post by raleigh3 on 2019-02-09
Maybe something here that I missed ?

[http://nekhbet.com/ssmtp_yahoo.shtml](http://nekhbet.com/ssmtp_yahoo.shtml)

---

### Post by dmnur on 2019-02-09
> **raleigh3 said:**
> Is mail.txt supposed to contain my real email address?
Yes.

Anyway, **smtp.mail.yahoo.com** seems to unreachable from your side.

You can see that connection times out in both **ssmtp.trace** and the **openssl** command output.

I don't know why, maybe some regional restriction? Or it's your ISP blocking.

You can try pinging the address to make sure that it's really the case:
```
ping -c 3 smtp.mail.yahoo.com
```

But if ping succeeds, try also with port 465. If that fails too, I could only offer you to contact your ISP or use another mail provider.

---

### Post by raleigh3 on 2019-02-09
Ping failed. Thanks for all your help.

I can still send emails with Seamonkey.

---

