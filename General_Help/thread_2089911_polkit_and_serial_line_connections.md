---
title: "polkit and serial line connections"
date: 2012-11-30
forum: General Help
---

### Post by ummelum on 2012-11-30
i have a plain vanilla default install of xubuntu. i need to access a terminal, which is directly connected...
```
$ ls /dev/ttyS0
crw-rw---- 1 root dialout 4, 64 Nov 30 19:59 /dev/ttyS0
```

i did...
```
$ sudo apt-get install cu
```
which went fine and dropped cu in /usr/bin. i used apt-get because cu isn't available in the software center.

as a user, part of the groups 'dialout', 'adm' and 'sudo', i tried...
```
$ cu -l /dev/ttyS0 -s 115200
```
which didn't work. the serial port is the correct one, as well as the baudrate, parity, ...

so i tried...
```
$ sudo cu -l /dev/ttyS0 -s 115200
/usr/bin/cu: open (/dev/ttyS0): Permission denied
/usr/bin/cu: /dev/ttyS0: Line in use
```

then i did..
```
$ sudo su -
```
which gave me a root prompt, where i tried...
```
# cu -l /dev/ttyS0 -s 115200
/usr/bin/cu: open (/dev/ttyS1): Permission denied
/usr/bin/cu: /dev/ttyS1: Line in use
```

is this is a polkit thing? an udev thing? if i boot this box in openbsd or netbsd, cu will connect just fine.

we're in the year 2012, and a modern unix apparently can't connect to a serial line?

---

### Post by ummelum on 2012-11-30
i retried the above scenarios with policykit's pkexec, with the same results...

---

### Post by ummelum on 2012-12-01
to make sure this wasn't a polkit thing, i made an action definition for this, and dropped it in /etc/polkit-1/actions

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE policyconfig PUBLIC "-//freedesktop//DTD PolicyKit Policy Configuration 1.0//EN""http://www.freedesktop.org/standards/PolicyKit/1.0/policyconfig.dtd">
<policyconfig>
<action id="org.freedesktop.policykit.exec">
    <defaults>
      <allow_active>yes</allow_active>
    </defaults>
    <annotate key="org.freedesktop.policykit.exec.path">/usr/bin/cu</annotate>
    <annotate key="org.freedesktop.policykit.exec.argv1">-l /dev/ttyS0 -s 115200</annotate>
    <annotate key="org.freedesktop.policykit.imply >true</annotate>
    <annotate key="org.freedesktop.policykit.owner>unix-user:ummelum</annotate>
  </action>
</policyconfig>
```


i ran it...
```
exec /usr/bin/pkexec --user ummelum /usr/bin/cu -l /dev/ttyS0 -s 115200
```

but results were similar as in my posts above.

according to /var/log/auth.log, the policy worked...
```
Dec  1 22:51:54 iugo polkitd(authority=local): Operator of unix-session:/org/freedesktop/ConsoleKit/Session1 successfully authenticated as unix-user:ummelum to gain ONE-SHOT authorization for action org.freedesktop.policykit.exec for unix-process:5798:3872562 [bash] (owned by unix-user:ummelum)
Dec  1 22:51:54 iugo pkexec: pam_unix(polkit-1:session): session opened for user root by ummelum(uid=1000)
Dec  1 22:51:54 iugo pkexec: pam_ck_connector(polkit-1:session): cannot determine display-device
Dec  1 22:51:54 iugo pkexec[6047]: ummelum: Executing command [USER=root] [TTY=/dev/pts/0] [CWD=/home/ummelum] [COMMAND=/usr/bin/cu -l /dev/ttyS0 -s 115200]
```

so this isn't a polkit thing. ***i'd love to have someone shine some light on this...***

---

### Post by ummelum on 2012-12-01
i suspect this is restricted by pam's capabilities...

so i added a line to /etc/security/group.conf
```
cu;*;ummelum;Al0000-2400;dialout
```

and created /etc/pam.d/cu
```
session	optional	pam_permit.so

```

i used a login-shell and tried my serial console, but alas..

if i try with pkexec, from a login-shell, i get the following in /var/log/auth.log:
```
Dec  1 23:49:02 iugo polkitd(authority=local): Unregistered Authentication Agent for unix-process:914:1133 (system bus name :1.73, object path /org/freedesktop/PolicyKit1/AuthenticationAgent, locale en_US.UTF-8) (disconnected from bus)
```

can anyone tell me if the above pam-policy is correct, or give me a solution to my problem?

---

### Post by ummelum on 2012-12-03
and apparently i'm not the only one with this problem:

[http://ubuntuforums.org/showthread.php?p=12345518](http://ubuntuforums.org/showthread.php?p=12345518)

---

### Post by ummelum on 2012-12-04
and even more people with the same problem, all during the last weeks...

[http://ubuntuforums.org/showthread.php?t=2087953](http://ubuntuforums.org/showthread.php?t=2087953)
[http://ubuntuforums.org/showthread.php?t=2082610](http://ubuntuforums.org/showthread.php?t=2082610)

---

### Post by ummelum on 2012-12-06
***can someone clue me in why this isn't working as it should? i find it hard to believe i'm the only ubuntu-user that needs a working serial port.***

---

### Post by ummelum on 2012-12-07
silent bump, and link to the launchpad bug:
[https://bugs.launchpad.net/ubuntu/+bug/1087519](https://bugs.launchpad.net/ubuntu/+bug/1087519)

---

### Post by ummelum on 2012-12-09
let's try as a user with sufficient rights:
$ strace -f -ff -o STRACE_CU cu -l /dev/ttyS0 -s 115200
```
Connected.
```
but it doesn't relay the serial console. i can abort this with the usual "~." if i have enough patience and if i break (^C) it a few times.

$ cat STRACE_CU.*|grep EPERM
```
ioctl(3, TIOCSCTTY)                     = -1 EPERM (Operation not permitted)
```
why isn't the actual terminal allowed to take control?

$ excerpt from STRACE_CU.*:
```
open("/dev/ttyS0", O_RDWR|O_NONBLOCK)   = 3
geteuid32()                             = 1000
getuid32()                              = 1000
getegid32()                             = 1000
getgid32()                              = 1000
setregid32(1000, 1000)                  = 0
setreuid32(1000, 1000)                  = 0
fcntl64(3, F_GETFD)                     = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
access("/dev/ttyS0", R_OK|W_OK)         = 0
fcntl64(3, F_GETFL)                     = 0x802 (flags O_RDWR|O_NONBLOCK)
fcntl64(3, F_SETFL, O_RDWR)             = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, TCFLSH, 0)                     = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_START or TCSETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, TIOCSCTTY)                     = -1 EPERM (Operation not permitted)
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_START or TCSETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_STOP or TCSETSW, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
access("/dev/ttyS0", R_OK|W_OK)         = 0
fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb77ca000
write(1, "\7Connected.\n", 12)          = 12
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(0, SNDCTL_TMR_START or TCSETS, {B38400 -opost -isig -icanon -echo ...}) = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 -opost -isig -icanon -echo ...}) = 0
pipe([4, 5])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb760e968) = 2670
close(5)
```




let's try with elevated rights:
$ sudo strace -f -ff -o SUDO_STRACE_CU cu -l /dev/ttyS0 -s 115200
```
cu: open (/dev/ttyS0): Permission denied
cu: /dev/ttyS0: Line in use
```
and it exits cleanly...

$ cat SUDO_STRACE_CU.*|grep "open"|grep "ttyS0"
```
open("/dev/ttyS0", O_RDWR|O_NONBLOCK)   = -1 EACCES (Permission denied)
write(2, "cu: open (/dev/ttyS0): Permissio"..., 41) = 41
```

$ excerpt from SUDO_STRACE_CU.*
```
open("/dev/ttyS0", O_RDWR|O_NONBLOCK)   = -1 EACCES (Permission denied)
geteuid32()                             = 10
getuid32()                              = 10
getegid32()                             = 0
getgid32()                              = 0
setregid32(0, 0)                        = 0
setreuid32(10, 10)                      = 0
write(2, "cu: open (/dev/ttyS0): Permissio"..., 41) = 41
unlink("/var/lock/LCK..ttyS0")          = 0
write(2, "cu: /dev/ttyS0: Line in use\n", 28) = 28
exit_group(1)                           = ?
```

if anyone is interested in the full traces, just ask...

---

### Post by ummelum on 2012-12-09
i just made user 'root' part of the groups tty, dialout and uucp. using sudo, or the root account, gives me the same behavior as using a normal user now...

---

### Post by ummelum on 2012-12-10
$ sudo ls -al /dev/ttyS?
```
crw-rw---- 1 root dialout 4, 64 Dec 8 10:05 /dev/ttyS0
crw-rw---- 1 root dialout 4, 65 Dec 8 10:05 /dev/ttyS1
crw-rw---- 1 root dialout 4, 66 Dec 8 10:05 /dev/ttyS2
crw-rw---- 1 root dialout 4, 67 Dec 8 10:05 /dev/ttyS3
crw-rw---- 1 root dialout 4, 68 Dec 8 10:05 /dev/ttyS4
crw-rw---- 1 root dialout 4, 69 Dec 8 10:05 /dev/ttyS5
crw-rw---- 1 root dialout 4, 70 Dec 8 10:05 /dev/ttyS6
crw-rw---- 1 root dialout 4, 71 Dec 8 10:05 /dev/ttyS7
crw-rw---- 1 root dialout 4, 72 Dec 8 10:05 /dev/ttyS8
crw-rw---- 1 root dialout 4, 73 Dec 8 10:05 /dev/ttyS9
```
$ sudo cat /proc/tty/driver/serial
```
serinfo:1.0 driver revision:
0: uart:16550A port:000003F8 irq:4 tx:0 rx:0 DSR
1: uart:16550A port:000002F8 irq:3 tx:0 rx:0
```
$ sudo stty -F /dev/ttyS0 speed
```
115200
```
this is interesting! apparently baudrate was set by cu (default is 9600 after a cold boot; cu does set this at 115200 and it stays that way)

serial tty's are actually allocated, so that's not it either:
$ sudo cat /proc/tty/drivers|grep ttyS
```
serial               /dev/ttyS       4 64-111 serial
```
$ sudo dmesg|grep tty
```
[ 0.000000] console [tty0] enabled
[ 0.663436] 00:06: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[ 0.683785] 00:07: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
```

$ sudo cat /boot/config-3.*|grep 16550 && sudo modprobe -l|grep 16550
```
CONFIG_SND_SERIAL_U16550=m
CONFIG_SND_SERIAL_U16550=m
CONFIG_SND_SERIAL_U16550=m
CONFIG_SND_SERIAL_U16550=m
kernel/sound/drivers/snd-serial-u16550.ko
```the only 16550 serial steering i can find in CONFIG is for a serial sound card. i am assuming a standard 16550 uart buffer is handled by the main kernel, and hardware support is not at issue here.

since i made user 'root' part of the mandatory group 'dialout', it doesn't make any difference whether i try this with an uid of 0 or not.


so let's bump this thread shamelessly with a full strace:

$ strace -f -ff -o STRACE_CU cu -l /dev/ttyS0 -s 115200
```
Connected.
~.

Disconnected.
```
i was able to abort the terminal normally, with "~."...

$ ls STRACE_CU.*
```
STRACE_CU.3139
STRACE_CU.3140
```

$ cat STRACE_CU.3139
```
[SIZE="1"]execve("/usr/bin/cu", ["cu", "-l", "/dev/ttyS0", "-s", "115200"], [/* 50 vars */]) = 0
brk(0)                                  = 0x88ca000
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
mmap2(NULL, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7790000
access("/etc/ld.so.preload", R_OK)      = -1 ENOENT (No such file or directory)
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=72636, ...}) = 0
mmap2(NULL, 72636, PROT_READ, MAP_PRIVATE, 4, 0) = 0xb777e000
close(4)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libc.so.6", O_RDONLY|O_CLOEXEC) = 4
read(4, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0000\226\1\0004\0\0\0"..., 512) = 512
fstat64(4, {st_mode=S_IFREG|0755, st_size=1730024, ...}) = 0
mmap2(NULL, 1743580, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 4, 0) = 0xb75d4000
mprotect(0xb7777000, 4096, PROT_NONE)   = 0
mmap2(0xb7778000, 12288, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 4, 0x1a3) = 0xb7778000
mmap2(0xb777b000, 10972, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb777b000
close(4)                                = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb75d3000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb75d3900, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0, limit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7778000, 8192, PROT_READ)   = 0
mprotect(0x806e000, 4096, PROT_READ)    = 0
mprotect(0xb77b3000, 4096, PROT_READ)   = 0
munmap(0xb777e000, 72636)               = 0
brk(0)                                  = 0x88ca000
brk(0x88eb000)                          = 0x88eb000
open("/etc/uucp/config", O_RDONLY)      = 4
fstat64(4, {st_mode=S_IFREG|0644, st_size=461, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb778f000
read(4, "#\n# config\tThis is the configura"..., 4096) = 461
read(4, "", 4096)                       = 0
close(4)                                = 0
munmap(0xb778f000, 4096)                = 0
open("/etc/uucp/Sysfiles", O_RDONLY)    = -1 ENOENT (No such file or directory)
getpid()                                = 3139
getrlimit(RLIMIT_NOFILE, {rlim_cur=1024, rlim_max=4*1024}) = 0
close(3)                                = 0
close(4)                                = -1 EBADF (Bad file descriptor)
close(5)                                = -1 EBADF (Bad file descriptor)
close(6)                                = -1 EBADF (Bad file descriptor)
close(7)                                = -1 EBADF (Bad file descriptor)
close(8)                                = -1 EBADF (Bad file descriptor)
close(9)                                = -1 EBADF (Bad file descriptor)
close(10)                               = -1 EBADF (Bad file descriptor)
close(11)                               = -1 EBADF (Bad file descriptor)
close(12)                               = -1 EBADF (Bad file descriptor)
close(13)                               = -1 EBADF (Bad file descriptor)
close(14)                               = -1 EBADF (Bad file descriptor)
close(15)                               = -1 EBADF (Bad file descriptor)
close(16)                               = -1 EBADF (Bad file descriptor)
close(17)                               = -1 EBADF (Bad file descriptor)
close(18)                               = -1 EBADF (Bad file descriptor)
close(19)                               = -1 EBADF (Bad file descriptor)
close(20)                               = -1 EBADF (Bad file descriptor)
close(21)                               = -1 EBADF (Bad file descriptor)
close(22)                               = -1 EBADF (Bad file descriptor)
close(23)                               = -1 EBADF (Bad file descriptor)
close(24)                               = -1 EBADF (Bad file descriptor)
close(25)                               = -1 EBADF (Bad file descriptor)
close(26)                               = -1 EBADF (Bad file descriptor)
close(27)                               = -1 EBADF (Bad file descriptor)
close(28)                               = -1 EBADF (Bad file descriptor)
close(29)                               = -1 EBADF (Bad file descriptor)
close(30)                               = -1 EBADF (Bad file descriptor)
close(31)                               = -1 EBADF (Bad file descriptor)
close(32)                               = -1 EBADF (Bad file descriptor)
close(33)                               = -1 EBADF (Bad file descriptor)
close(34)                               = -1 EBADF (Bad file descriptor)
close(35)                               = -1 EBADF (Bad file descriptor)
close(36)                               = -1 EBADF (Bad file descriptor)
close(37)                               = -1 EBADF (Bad file descriptor)
close(38)                               = -1 EBADF (Bad file descriptor)
close(39)                               = -1 EBADF (Bad file descriptor)
close(40)                               = -1 EBADF (Bad file descriptor)
close(41)                               = -1 EBADF (Bad file descriptor)
close(42)                               = -1 EBADF (Bad file descriptor)
close(43)                               = -1 EBADF (Bad file descriptor)
close(44)                               = -1 EBADF (Bad file descriptor)
close(45)                               = -1 EBADF (Bad file descriptor)
close(46)                               = -1 EBADF (Bad file descriptor)
close(47)                               = -1 EBADF (Bad file descriptor)
close(48)                               = -1 EBADF (Bad file descriptor)
close(49)                               = -1 EBADF (Bad file descriptor)
close(50)                               = -1 EBADF (Bad file descriptor)
close(51)                               = -1 EBADF (Bad file descriptor)
close(52)                               = -1 EBADF (Bad file descriptor)
close(53)                               = -1 EBADF (Bad file descriptor)
close(54)                               = -1 EBADF (Bad file descriptor)
close(55)                               = -1 EBADF (Bad file descriptor)
close(56)                               = -1 EBADF (Bad file descriptor)
close(57)                               = -1 EBADF (Bad file descriptor)
close(58)                               = -1 EBADF (Bad file descriptor)
close(59)                               = -1 EBADF (Bad file descriptor)
close(60)                               = -1 EBADF (Bad file descriptor)
close(61)                               = -1 EBADF (Bad file descriptor)
close(62)                               = -1 EBADF (Bad file descriptor)
close(63)                               = -1 EBADF (Bad file descriptor)
close(64)                               = -1 EBADF (Bad file descriptor)
close(65)                               = -1 EBADF (Bad file descriptor)
close(66)                               = -1 EBADF (Bad file descriptor)
close(67)                               = -1 EBADF (Bad file descriptor)
close(68)                               = -1 EBADF (Bad file descriptor)
close(69)                               = -1 EBADF (Bad file descriptor)
close(70)                               = -1 EBADF (Bad file descriptor)
close(71)                               = -1 EBADF (Bad file descriptor)
close(72)                               = -1 EBADF (Bad file descriptor)
close(73)                               = -1 EBADF (Bad file descriptor)
close(74)                               = -1 EBADF (Bad file descriptor)
close(75)                               = -1 EBADF (Bad file descriptor)
close(76)                               = -1 EBADF (Bad file descriptor)
close(77)                               = -1 EBADF (Bad file descriptor)
close(78)                               = -1 EBADF (Bad file descriptor)
close(79)                               = -1 EBADF (Bad file descriptor)
close(80)                               = -1 EBADF (Bad file descriptor)
close(81)                               = -1 EBADF (Bad file descriptor)
close(82)                               = -1 EBADF (Bad file descriptor)
close(83)                               = -1 EBADF (Bad file descriptor)
close(84)                               = -1 EBADF (Bad file descriptor)
close(85)                               = -1 EBADF (Bad file descriptor)
close(86)                               = -1 EBADF (Bad file descriptor)
close(87)                               = -1 EBADF (Bad file descriptor)
close(88)                               = -1 EBADF (Bad file descriptor)
close(89)                               = -1 EBADF (Bad file descriptor)
close(90)                               = -1 EBADF (Bad file descriptor)
close(91)                               = -1 EBADF (Bad file descriptor)
close(92)                               = -1 EBADF (Bad file descriptor)
close(93)                               = -1 EBADF (Bad file descriptor)
close(94)                               = -1 EBADF (Bad file descriptor)
close(95)                               = -1 EBADF (Bad file descriptor)
close(96)                               = -1 EBADF (Bad file descriptor)
close(97)                               = -1 EBADF (Bad file descriptor)
close(98)                               = -1 EBADF (Bad file descriptor)
close(99)                               = -1 EBADF (Bad file descriptor)
close(100)                              = -1 EBADF (Bad file descriptor)
close(101)                              = -1 EBADF (Bad file descriptor)
close(102)                              = -1 EBADF (Bad file descriptor)
close(103)                              = -1 EBADF (Bad file descriptor)
close(104)                              = -1 EBADF (Bad file descriptor)
close(105)                              = -1 EBADF (Bad file descriptor)
close(106)                              = -1 EBADF (Bad file descriptor)
close(107)                              = -1 EBADF (Bad file descriptor)
close(108)                              = -1 EBADF (Bad file descriptor)
close(109)                              = -1 EBADF (Bad file descriptor)
close(110)                              = -1 EBADF (Bad file descriptor)
close(111)                              = -1 EBADF (Bad file descriptor)
close(112)                              = -1 EBADF (Bad file descriptor)
close(113)                              = -1 EBADF (Bad file descriptor)
close(114)                              = -1 EBADF (Bad file descriptor)
close(115)                              = -1 EBADF (Bad file descriptor)
close(116)                              = -1 EBADF (Bad file descriptor)
close(117)                              = -1 EBADF (Bad file descriptor)
close(118)                              = -1 EBADF (Bad file descriptor)
close(119)                              = -1 EBADF (Bad file descriptor)
close(120)                              = -1 EBADF (Bad file descriptor)
close(121)                              = -1 EBADF (Bad file descriptor)
close(122)                              = -1 EBADF (Bad file descriptor)
close(123)                              = -1 EBADF (Bad file descriptor)
close(124)                              = -1 EBADF (Bad file descriptor)
close(125)                              = -1 EBADF (Bad file descriptor)
close(126)                              = -1 EBADF (Bad file descriptor)
close(127)                              = -1 EBADF (Bad file descriptor)
close(128)                              = -1 EBADF (Bad file descriptor)
close(129)                              = -1 EBADF (Bad file descriptor)
close(130)                              = -1 EBADF (Bad file descriptor)
close(131)                              = -1 EBADF (Bad file descriptor)
close(132)                              = -1 EBADF (Bad file descriptor)
close(133)                              = -1 EBADF (Bad file descriptor)
close(134)                              = -1 EBADF (Bad file descriptor)
close(135)                              = -1 EBADF (Bad file descriptor)
close(136)                              = -1 EBADF (Bad file descriptor)
close(137)                              = -1 EBADF (Bad file descriptor)
close(138)                              = -1 EBADF (Bad file descriptor)
close(139)                              = -1 EBADF (Bad file descriptor)
close(140)                              = -1 EBADF (Bad file descriptor)
close(141)                              = -1 EBADF (Bad file descriptor)
close(142)                              = -1 EBADF (Bad file descriptor)
close(143)                              = -1 EBADF (Bad file descriptor)
close(144)                              = -1 EBADF (Bad file descriptor)
close(145)                              = -1 EBADF (Bad file descriptor)
close(146)                              = -1 EBADF (Bad file descriptor)
close(147)                              = -1 EBADF (Bad file descriptor)
close(148)                              = -1 EBADF (Bad file descriptor)
close(149)                              = -1 EBADF (Bad file descriptor)
close(150)                              = -1 EBADF (Bad file descriptor)
close(151)                              = -1 EBADF (Bad file descriptor)
close(152)                              = -1 EBADF (Bad file descriptor)
close(153)                              = -1 EBADF (Bad file descriptor)
close(154)                              = -1 EBADF (Bad file descriptor)
close(155)                              = -1 EBADF (Bad file descriptor)
close(156)                              = -1 EBADF (Bad file descriptor)
close(157)                              = -1 EBADF (Bad file descriptor)
close(158)                              = -1 EBADF (Bad file descriptor)
close(159)                              = -1 EBADF (Bad file descriptor)
close(160)                              = -1 EBADF (Bad file descriptor)
close(161)                              = -1 EBADF (Bad file descriptor)
close(162)                              = -1 EBADF (Bad file descriptor)
close(163)                              = -1 EBADF (Bad file descriptor)
close(164)                              = -1 EBADF (Bad file descriptor)
close(165)                              = -1 EBADF (Bad file descriptor)
close(166)                              = -1 EBADF (Bad file descriptor)
close(167)                              = -1 EBADF (Bad file descriptor)
close(168)                              = -1 EBADF (Bad file descriptor)
close(169)                              = -1 EBADF (Bad file descriptor)
close(170)                              = -1 EBADF (Bad file descriptor)
close(171)                              = -1 EBADF (Bad file descriptor)
close(172)                              = -1 EBADF (Bad file descriptor)
close(173)                              = -1 EBADF (Bad file descriptor)
close(174)                              = -1 EBADF (Bad file descriptor)
close(175)                              = -1 EBADF (Bad file descriptor)
close(176)                              = -1 EBADF (Bad file descriptor)
close(177)                              = -1 EBADF (Bad file descriptor)
close(178)                              = -1 EBADF (Bad file descriptor)
close(179)                              = -1 EBADF (Bad file descriptor)
close(180)                              = -1 EBADF (Bad file descriptor)
close(181)                              = -1 EBADF (Bad file descriptor)
close(182)                              = -1 EBADF (Bad file descriptor)
close(183)                              = -1 EBADF (Bad file descriptor)
close(184)                              = -1 EBADF (Bad file descriptor)
close(185)                              = -1 EBADF (Bad file descriptor)
close(186)                              = -1 EBADF (Bad file descriptor)
close(187)                              = -1 EBADF (Bad file descriptor)
close(188)                              = -1 EBADF (Bad file descriptor)
close(189)                              = -1 EBADF (Bad file descriptor)
close(190)                              = -1 EBADF (Bad file descriptor)
close(191)                              = -1 EBADF (Bad file descriptor)
close(192)                              = -1 EBADF (Bad file descriptor)
close(193)                              = -1 EBADF (Bad file descriptor)
close(194)                              = -1 EBADF (Bad file descriptor)
close(195)                              = -1 EBADF (Bad file descriptor)
close(196)                              = -1 EBADF (Bad file descriptor)
close(197)                              = -1 EBADF (Bad file descriptor)
close(198)                              = -1 EBADF (Bad file descriptor)
close(199)                              = -1 EBADF (Bad file descriptor)
close(200)                              = -1 EBADF (Bad file descriptor)
close(201)                              = -1 EBADF (Bad file descriptor)
close(202)                              = -1 EBADF (Bad file descriptor)
close(203)                              = -1 EBADF (Bad file descriptor)
close(204)                              = -1 EBADF (Bad file descriptor)
close(205)                              = -1 EBADF (Bad file descriptor)
close(206)                              = -1 EBADF (Bad file descriptor)
close(207)                              = -1 EBADF (Bad file descriptor)
close(208)                              = -1 EBADF (Bad file descriptor)
close(209)                              = -1 EBADF (Bad file descriptor)
close(210)                              = -1 EBADF (Bad file descriptor)
close(211)                              = -1 EBADF (Bad file descriptor)
close(212)                              = -1 EBADF (Bad file descriptor)
close(213)                              = -1 EBADF (Bad file descriptor)
close(214)                              = -1 EBADF (Bad file descriptor)
close(215)                              = -1 EBADF (Bad file descriptor)
close(216)                              = -1 EBADF (Bad file descriptor)
close(217)                              = -1 EBADF (Bad file descriptor)
close(218)                              = -1 EBADF (Bad file descriptor)
close(219)                              = -1 EBADF (Bad file descriptor)
close(220)                              = -1 EBADF (Bad file descriptor)
close(221)                              = -1 EBADF (Bad file descriptor)
close(222)                              = -1 EBADF (Bad file descriptor)
close(223)                              = -1 EBADF (Bad file descriptor)
close(224)                              = -1 EBADF (Bad file descriptor)
close(225)                              = -1 EBADF (Bad file descriptor)
close(226)                              = -1 EBADF (Bad file descriptor)
close(227)                              = -1 EBADF (Bad file descriptor)
close(228)                              = -1 EBADF (Bad file descriptor)
close(229)                              = -1 EBADF (Bad file descriptor)
close(230)                              = -1 EBADF (Bad file descriptor)
close(231)                              = -1 EBADF (Bad file descriptor)
close(232)                              = -1 EBADF (Bad file descriptor)
close(233)                              = -1 EBADF (Bad file descriptor)
close(234)                              = -1 EBADF (Bad file descriptor)
close(235)                              = -1 EBADF (Bad file descriptor)
close(236)                              = -1 EBADF (Bad file descriptor)
close(237)                              = -1 EBADF (Bad file descriptor)
close(238)                              = -1 EBADF (Bad file descriptor)
close(239)                              = -1 EBADF (Bad file descriptor)
close(240)                              = -1 EBADF (Bad file descriptor)
close(241)                              = -1 EBADF (Bad file descriptor)
close(242)                              = -1 EBADF (Bad file descriptor)
close(243)                              = -1 EBADF (Bad file descriptor)
close(244)                              = -1 EBADF (Bad file descriptor)
close(245)                              = -1 EBADF (Bad file descriptor)
close(246)                              = -1 EBADF (Bad file descriptor)
close(247)                              = -1 EBADF (Bad file descriptor)
close(248)                              = -1 EBADF (Bad file descriptor)
close(249)                              = -1 EBADF (Bad file descriptor)
close(250)                              = -1 EBADF (Bad file descriptor)
close(251)                              = -1 EBADF (Bad file descriptor)
close(252)                              = -1 EBADF (Bad file descriptor)
close(253)                              = -1 EBADF (Bad file descriptor)
close(254)                              = -1 EBADF (Bad file descriptor)
close(255)                              = -1 EBADF (Bad file descriptor)
close(256)                              = -1 EBADF (Bad file descriptor)
close(257)                              = -1 EBADF (Bad file descriptor)
close(258)                              = -1 EBADF (Bad file descriptor)
close(259)                              = -1 EBADF (Bad file descriptor)
close(260)                              = -1 EBADF (Bad file descriptor)
close(261)                              = -1 EBADF (Bad file descriptor)
close(262)                              = -1 EBADF (Bad file descriptor)
close(263)                              = -1 EBADF (Bad file descriptor)
close(264)                              = -1 EBADF (Bad file descriptor)
close(265)                              = -1 EBADF (Bad file descriptor)
close(266)                              = -1 EBADF (Bad file descriptor)
close(267)                              = -1 EBADF (Bad file descriptor)
close(268)                              = -1 EBADF (Bad file descriptor)
close(269)                              = -1 EBADF (Bad file descriptor)
close(270)                              = -1 EBADF (Bad file descriptor)
close(271)                              = -1 EBADF (Bad file descriptor)
close(272)                              = -1 EBADF (Bad file descriptor)
close(273)                              = -1 EBADF (Bad file descriptor)
close(274)                              = -1 EBADF (Bad file descriptor)
close(275)                              = -1 EBADF (Bad file descriptor)
close(276)                              = -1 EBADF (Bad file descriptor)
close(277)                              = -1 EBADF (Bad file descriptor)
close(278)                              = -1 EBADF (Bad file descriptor)
close(279)                              = -1 EBADF (Bad file descriptor)
close(280)                              = -1 EBADF (Bad file descriptor)
close(281)                              = -1 EBADF (Bad file descriptor)
close(282)                              = -1 EBADF (Bad file descriptor)
close(283)                              = -1 EBADF (Bad file descriptor)
close(284)                              = -1 EBADF (Bad file descriptor)
close(285)                              = -1 EBADF (Bad file descriptor)
close(286)                              = -1 EBADF (Bad file descriptor)
close(287)                              = -1 EBADF (Bad file descriptor)
close(288)                              = -1 EBADF (Bad file descriptor)
close(289)                              = -1 EBADF (Bad file descriptor)
close(290)                              = -1 EBADF (Bad file descriptor)
close(291)                              = -1 EBADF (Bad file descriptor)
close(292)                              = -1 EBADF (Bad file descriptor)
close(293)                              = -1 EBADF (Bad file descriptor)
close(294)                              = -1 EBADF (Bad file descriptor)
close(295)                              = -1 EBADF (Bad file descriptor)
close(296)                              = -1 EBADF (Bad file descriptor)
close(297)                              = -1 EBADF (Bad file descriptor)
close(298)                              = -1 EBADF (Bad file descriptor)
close(299)                              = -1 EBADF (Bad file descriptor)
close(300)                              = -1 EBADF (Bad file descriptor)
close(301)                              = -1 EBADF (Bad file descriptor)
close(302)                              = -1 EBADF (Bad file descriptor)
close(303)                              = -1 EBADF (Bad file descriptor)
close(304)                              = -1 EBADF (Bad file descriptor)
close(305)                              = -1 EBADF (Bad file descriptor)
close(306)                              = -1 EBADF (Bad file descriptor)
close(307)                              = -1 EBADF (Bad file descriptor)
close(308)                              = -1 EBADF (Bad file descriptor)
close(309)                              = -1 EBADF (Bad file descriptor)
close(310)                              = -1 EBADF (Bad file descriptor)
close(311)                              = -1 EBADF (Bad file descriptor)
close(312)                              = -1 EBADF (Bad file descriptor)
close(313)                              = -1 EBADF (Bad file descriptor)
close(314)                              = -1 EBADF (Bad file descriptor)
close(315)                              = -1 EBADF (Bad file descriptor)
close(316)                              = -1 EBADF (Bad file descriptor)
close(317)                              = -1 EBADF (Bad file descriptor)
close(318)                              = -1 EBADF (Bad file descriptor)
close(319)                              = -1 EBADF (Bad file descriptor)
close(320)                              = -1 EBADF (Bad file descriptor)
close(321)                              = -1 EBADF (Bad file descriptor)
close(322)                              = -1 EBADF (Bad file descriptor)
close(323)                              = -1 EBADF (Bad file descriptor)
close(324)                              = -1 EBADF (Bad file descriptor)
close(325)                              = -1 EBADF (Bad file descriptor)
close(326)                              = -1 EBADF (Bad file descriptor)
close(327)                              = -1 EBADF (Bad file descriptor)
close(328)                              = -1 EBADF (Bad file descriptor)
close(329)                              = -1 EBADF (Bad file descriptor)
close(330)                              = -1 EBADF (Bad file descriptor)
close(331)                              = -1 EBADF (Bad file descriptor)
close(332)                              = -1 EBADF (Bad file descriptor)
close(333)                              = -1 EBADF (Bad file descriptor)
close(334)                              = -1 EBADF (Bad file descriptor)
close(335)                              = -1 EBADF (Bad file descriptor)
close(336)                              = -1 EBADF (Bad file descriptor)
close(337)                              = -1 EBADF (Bad file descriptor)
close(338)                              = -1 EBADF (Bad file descriptor)
close(339)                              = -1 EBADF (Bad file descriptor)
close(340)                              = -1 EBADF (Bad file descriptor)
close(341)                              = -1 EBADF (Bad file descriptor)
close(342)                              = -1 EBADF (Bad file descriptor)
close(343)                              = -1 EBADF (Bad file descriptor)
close(344)                              = -1 EBADF (Bad file descriptor)
close(345)                              = -1 EBADF (Bad file descriptor)
close(346)                              = -1 EBADF (Bad file descriptor)
close(347)                              = -1 EBADF (Bad file descriptor)
close(348)                              = -1 EBADF (Bad file descriptor)
close(349)                              = -1 EBADF (Bad file descriptor)
close(350)                              = -1 EBADF (Bad file descriptor)
close(351)                              = -1 EBADF (Bad file descriptor)
close(352)                              = -1 EBADF (Bad file descriptor)
close(353)                              = -1 EBADF (Bad file descriptor)
close(354)                              = -1 EBADF (Bad file descriptor)
close(355)                              = -1 EBADF (Bad file descriptor)
close(356)                              = -1 EBADF (Bad file descriptor)
close(357)                              = -1 EBADF (Bad file descriptor)
close(358)                              = -1 EBADF (Bad file descriptor)
close(359)                              = -1 EBADF (Bad file descriptor)
close(360)                              = -1 EBADF (Bad file descriptor)
close(361)                              = -1 EBADF (Bad file descriptor)
close(362)                              = -1 EBADF (Bad file descriptor)
close(363)                              = -1 EBADF (Bad file descriptor)
close(364)                              = -1 EBADF (Bad file descriptor)
close(365)                              = -1 EBADF (Bad file descriptor)
close(366)                              = -1 EBADF (Bad file descriptor)
close(367)                              = -1 EBADF (Bad file descriptor)
close(368)                              = -1 EBADF (Bad file descriptor)
close(369)                              = -1 EBADF (Bad file descriptor)
close(370)                              = -1 EBADF (Bad file descriptor)
close(371)                              = -1 EBADF (Bad file descriptor)
close(372)                              = -1 EBADF (Bad file descriptor)
close(373)                              = -1 EBADF (Bad file descriptor)
close(374)                              = -1 EBADF (Bad file descriptor)
close(375)                              = -1 EBADF (Bad file descriptor)
close(376)                              = -1 EBADF (Bad file descriptor)
close(377)                              = -1 EBADF (Bad file descriptor)
close(378)                              = -1 EBADF (Bad file descriptor)
close(379)                              = -1 EBADF (Bad file descriptor)
close(380)                              = -1 EBADF (Bad file descriptor)
close(381)                              = -1 EBADF (Bad file descriptor)
close(382)                              = -1 EBADF (Bad file descriptor)
close(383)                              = -1 EBADF (Bad file descriptor)
close(384)                              = -1 EBADF (Bad file descriptor)
close(385)                              = -1 EBADF (Bad file descriptor)
close(386)                              = -1 EBADF (Bad file descriptor)
close(387)                              = -1 EBADF (Bad file descriptor)
close(388)                              = -1 EBADF (Bad file descriptor)
close(389)                              = -1 EBADF (Bad file descriptor)
close(390)                              = -1 EBADF (Bad file descriptor)
close(391)                              = -1 EBADF (Bad file descriptor)
close(392)                              = -1 EBADF (Bad file descriptor)
close(393)                              = -1 EBADF (Bad file descriptor)
close(394)                              = -1 EBADF (Bad file descriptor)
close(395)                              = -1 EBADF (Bad file descriptor)
close(396)                              = -1 EBADF (Bad file descriptor)
close(397)                              = -1 EBADF (Bad file descriptor)
close(398)                              = -1 EBADF (Bad file descriptor)
close(399)                              = -1 EBADF (Bad file descriptor)
close(400)                              = -1 EBADF (Bad file descriptor)
close(401)                              = -1 EBADF (Bad file descriptor)
close(402)                              = -1 EBADF (Bad file descriptor)
close(403)                              = -1 EBADF (Bad file descriptor)
close(404)                              = -1 EBADF (Bad file descriptor)
close(405)                              = -1 EBADF (Bad file descriptor)
close(406)                              = -1 EBADF (Bad file descriptor)
close(407)                              = -1 EBADF (Bad file descriptor)
close(408)                              = -1 EBADF (Bad file descriptor)
close(409)                              = -1 EBADF (Bad file descriptor)
close(410)                              = -1 EBADF (Bad file descriptor)
close(411)                              = -1 EBADF (Bad file descriptor)
close(412)                              = -1 EBADF (Bad file descriptor)
close(413)                              = -1 EBADF (Bad file descriptor)
close(414)                              = -1 EBADF (Bad file descriptor)
close(415)                              = -1 EBADF (Bad file descriptor)
close(416)                              = -1 EBADF (Bad file descriptor)
close(417)                              = -1 EBADF (Bad file descriptor)
close(418)                              = -1 EBADF (Bad file descriptor)
close(419)                              = -1 EBADF (Bad file descriptor)
close(420)                              = -1 EBADF (Bad file descriptor)
close(421)                              = -1 EBADF (Bad file descriptor)
close(422)                              = -1 EBADF (Bad file descriptor)
close(423)                              = -1 EBADF (Bad file descriptor)
close(424)                              = -1 EBADF (Bad file descriptor)
close(425)                              = -1 EBADF (Bad file descriptor)
close(426)                              = -1 EBADF (Bad file descriptor)
close(427)                              = -1 EBADF (Bad file descriptor)
close(428)                              = -1 EBADF (Bad file descriptor)
close(429)                              = -1 EBADF (Bad file descriptor)
close(430)                              = -1 EBADF (Bad file descriptor)
close(431)                              = -1 EBADF (Bad file descriptor)
close(432)                              = -1 EBADF (Bad file descriptor)
close(433)                              = -1 EBADF (Bad file descriptor)
close(434)                              = -1 EBADF (Bad file descriptor)
close(435)                              = -1 EBADF (Bad file descriptor)
close(436)                              = -1 EBADF (Bad file descriptor)
close(437)                              = -1 EBADF (Bad file descriptor)
close(438)                              = -1 EBADF (Bad file descriptor)
close(439)                              = -1 EBADF (Bad file descriptor)
close(440)                              = -1 EBADF (Bad file descriptor)
close(441)                              = -1 EBADF (Bad file descriptor)
close(442)                              = -1 EBADF (Bad file descriptor)
close(443)                              = -1 EBADF (Bad file descriptor)
close(444)                              = -1 EBADF (Bad file descriptor)
close(445)                              = -1 EBADF (Bad file descriptor)
close(446)                              = -1 EBADF (Bad file descriptor)
close(447)                              = -1 EBADF (Bad file descriptor)
close(448)                              = -1 EBADF (Bad file descriptor)
close(449)                              = -1 EBADF (Bad file descriptor)
close(450)                              = -1 EBADF (Bad file descriptor)
close(451)                              = -1 EBADF (Bad file descriptor)
close(452)                              = -1 EBADF (Bad file descriptor)
close(453)                              = -1 EBADF (Bad file descriptor)
close(454)                              = -1 EBADF (Bad file descriptor)
close(455)                              = -1 EBADF (Bad file descriptor)
close(456)                              = -1 EBADF (Bad file descriptor)
close(457)                              = -1 EBADF (Bad file descriptor)
close(458)                              = -1 EBADF (Bad file descriptor)
close(459)                              = -1 EBADF (Bad file descriptor)
close(460)                              = -1 EBADF (Bad file descriptor)
close(461)                              = -1 EBADF (Bad file descriptor)
close(462)                              = -1 EBADF (Bad file descriptor)
close(463)                              = -1 EBADF (Bad file descriptor)
close(464)                              = -1 EBADF (Bad file descriptor)
close(465)                              = -1 EBADF (Bad file descriptor)
close(466)                              = -1 EBADF (Bad file descriptor)
close(467)                              = -1 EBADF (Bad file descriptor)
close(468)                              = -1 EBADF (Bad file descriptor)
close(469)                              = -1 EBADF (Bad file descriptor)
close(470)                              = -1 EBADF (Bad file descriptor)
close(471)                              = -1 EBADF (Bad file descriptor)
close(472)                              = -1 EBADF (Bad file descriptor)
close(473)                              = -1 EBADF (Bad file descriptor)
close(474)                              = -1 EBADF (Bad file descriptor)
close(475)                              = -1 EBADF (Bad file descriptor)
close(476)                              = -1 EBADF (Bad file descriptor)
close(477)                              = -1 EBADF (Bad file descriptor)
close(478)                              = -1 EBADF (Bad file descriptor)
close(479)                              = -1 EBADF (Bad file descriptor)
close(480)                              = -1 EBADF (Bad file descriptor)
close(481)                              = -1 EBADF (Bad file descriptor)
close(482)                              = -1 EBADF (Bad file descriptor)
close(483)                              = -1 EBADF (Bad file descriptor)
close(484)                              = -1 EBADF (Bad file descriptor)
close(485)                              = -1 EBADF (Bad file descriptor)
close(486)                              = -1 EBADF (Bad file descriptor)
close(487)                              = -1 EBADF (Bad file descriptor)
close(488)                              = -1 EBADF (Bad file descriptor)
close(489)                              = -1 EBADF (Bad file descriptor)
close(490)                              = -1 EBADF (Bad file descriptor)
close(491)                              = -1 EBADF (Bad file descriptor)
close(492)                              = -1 EBADF (Bad file descriptor)
close(493)                              = -1 EBADF (Bad file descriptor)
close(494)                              = -1 EBADF (Bad file descriptor)
close(495)                              = -1 EBADF (Bad file descriptor)
close(496)                              = -1 EBADF (Bad file descriptor)
close(497)                              = -1 EBADF (Bad file descriptor)
close(498)                              = -1 EBADF (Bad file descriptor)
close(499)                              = -1 EBADF (Bad file descriptor)
close(500)                              = -1 EBADF (Bad file descriptor)
close(501)                              = -1 EBADF (Bad file descriptor)
close(502)                              = -1 EBADF (Bad file descriptor)
close(503)                              = -1 EBADF (Bad file descriptor)
close(504)                              = -1 EBADF (Bad file descriptor)
close(505)                              = -1 EBADF (Bad file descriptor)
close(506)                              = -1 EBADF (Bad file descriptor)
close(507)                              = -1 EBADF (Bad file descriptor)
close(508)                              = -1 EBADF (Bad file descriptor)
close(509)                              = -1 EBADF (Bad file descriptor)
close(510)                              = -1 EBADF (Bad file descriptor)
close(511)                              = -1 EBADF (Bad file descriptor)
close(512)                              = -1 EBADF (Bad file descriptor)
close(513)                              = -1 EBADF (Bad file descriptor)
close(514)                              = -1 EBADF (Bad file descriptor)
close(515)                              = -1 EBADF (Bad file descriptor)
close(516)                              = -1 EBADF (Bad file descriptor)
close(517)                              = -1 EBADF (Bad file descriptor)
close(518)                              = -1 EBADF (Bad file descriptor)
close(519)                              = -1 EBADF (Bad file descriptor)
close(520)                              = -1 EBADF (Bad file descriptor)
close(521)                              = -1 EBADF (Bad file descriptor)
close(522)                              = -1 EBADF (Bad file descriptor)
close(523)                              = -1 EBADF (Bad file descriptor)
close(524)                              = -1 EBADF (Bad file descriptor)
close(525)                              = -1 EBADF (Bad file descriptor)
close(526)                              = -1 EBADF (Bad file descriptor)
close(527)                              = -1 EBADF (Bad file descriptor)
close(528)                              = -1 EBADF (Bad file descriptor)
close(529)                              = -1 EBADF (Bad file descriptor)
close(530)                              = -1 EBADF (Bad file descriptor)
close(531)                              = -1 EBADF (Bad file descriptor)
close(532)                              = -1 EBADF (Bad file descriptor)
close(533)                              = -1 EBADF (Bad file descriptor)
close(534)                              = -1 EBADF (Bad file descriptor)
close(535)                              = -1 EBADF (Bad file descriptor)
close(536)                              = -1 EBADF (Bad file descriptor)
close(537)                              = -1 EBADF (Bad file descriptor)
close(538)                              = -1 EBADF (Bad file descriptor)
close(539)                              = -1 EBADF (Bad file descriptor)
close(540)                              = -1 EBADF (Bad file descriptor)
close(541)                              = -1 EBADF (Bad file descriptor)
close(542)                              = -1 EBADF (Bad file descriptor)
close(543)                              = -1 EBADF (Bad file descriptor)
close(544)                              = -1 EBADF (Bad file descriptor)
close(545)                              = -1 EBADF (Bad file descriptor)
close(546)                              = -1 EBADF (Bad file descriptor)
close(547)                              = -1 EBADF (Bad file descriptor)
close(548)                              = -1 EBADF (Bad file descriptor)
close(549)                              = -1 EBADF (Bad file descriptor)
close(550)                              = -1 EBADF (Bad file descriptor)
close(551)                              = -1 EBADF (Bad file descriptor)
close(552)                              = -1 EBADF (Bad file descriptor)
close(553)                              = -1 EBADF (Bad file descriptor)
close(554)                              = -1 EBADF (Bad file descriptor)
close(555)                              = -1 EBADF (Bad file descriptor)
close(556)                              = -1 EBADF (Bad file descriptor)
close(557)                              = -1 EBADF (Bad file descriptor)
close(558)                              = -1 EBADF (Bad file descriptor)
close(559)                              = -1 EBADF (Bad file descriptor)
close(560)                              = -1 EBADF (Bad file descriptor)
close(561)                              = -1 EBADF (Bad file descriptor)
close(562)                              = -1 EBADF (Bad file descriptor)
close(563)                              = -1 EBADF (Bad file descriptor)
close(564)                              = -1 EBADF (Bad file descriptor)
close(565)                              = -1 EBADF (Bad file descriptor)
close(566)                              = -1 EBADF (Bad file descriptor)
close(567)                              = -1 EBADF (Bad file descriptor)
close(568)                              = -1 EBADF (Bad file descriptor)
close(569)                              = -1 EBADF (Bad file descriptor)
close(570)                              = -1 EBADF (Bad file descriptor)
close(571)                              = -1 EBADF (Bad file descriptor)
close(572)                              = -1 EBADF (Bad file descriptor)
close(573)                              = -1 EBADF (Bad file descriptor)
close(574)                              = -1 EBADF (Bad file descriptor)
close(575)                              = -1 EBADF (Bad file descriptor)
close(576)                              = -1 EBADF (Bad file descriptor)
close(577)                              = -1 EBADF (Bad file descriptor)
close(578)                              = -1 EBADF (Bad file descriptor)
close(579)                              = -1 EBADF (Bad file descriptor)
close(580)                              = -1 EBADF (Bad file descriptor)
close(581)                              = -1 EBADF (Bad file descriptor)
close(582)                              = -1 EBADF (Bad file descriptor)
close(583)                              = -1 EBADF (Bad file descriptor)
close(584)                              = -1 EBADF (Bad file descriptor)
close(585)                              = -1 EBADF (Bad file descriptor)
close(586)                              = -1 EBADF (Bad file descriptor)
close(587)                              = -1 EBADF (Bad file descriptor)
close(588)                              = -1 EBADF (Bad file descriptor)
close(589)                              = -1 EBADF (Bad file descriptor)
close(590)                              = -1 EBADF (Bad file descriptor)
close(591)                              = -1 EBADF (Bad file descriptor)
close(592)                              = -1 EBADF (Bad file descriptor)
close(593)                              = -1 EBADF (Bad file descriptor)
close(594)                              = -1 EBADF (Bad file descriptor)
close(595)                              = -1 EBADF (Bad file descriptor)
close(596)                              = -1 EBADF (Bad file descriptor)
close(597)                              = -1 EBADF (Bad file descriptor)
close(598)                              = -1 EBADF (Bad file descriptor)
close(599)                              = -1 EBADF (Bad file descriptor)
close(600)                              = -1 EBADF (Bad file descriptor)
close(601)                              = -1 EBADF (Bad file descriptor)
close(602)                              = -1 EBADF (Bad file descriptor)
close(603)                              = -1 EBADF (Bad file descriptor)
close(604)                              = -1 EBADF (Bad file descriptor)
close(605)                              = -1 EBADF (Bad file descriptor)
close(606)                              = -1 EBADF (Bad file descriptor)
close(607)                              = -1 EBADF (Bad file descriptor)
close(608)                              = -1 EBADF (Bad file descriptor)
close(609)                              = -1 EBADF (Bad file descriptor)
close(610)                              = -1 EBADF (Bad file descriptor)
close(611)                              = -1 EBADF (Bad file descriptor)
close(612)                              = -1 EBADF (Bad file descriptor)
close(613)                              = -1 EBADF (Bad file descriptor)
close(614)                              = -1 EBADF (Bad file descriptor)
close(615)                              = -1 EBADF (Bad file descriptor)
close(616)                              = -1 EBADF (Bad file descriptor)
close(617)                              = -1 EBADF (Bad file descriptor)
close(618)                              = -1 EBADF (Bad file descriptor)
close(619)                              = -1 EBADF (Bad file descriptor)
close(620)                              = -1 EBADF (Bad file descriptor)
close(621)                              = -1 EBADF (Bad file descriptor)
close(622)                              = -1 EBADF (Bad file descriptor)
close(623)                              = -1 EBADF (Bad file descriptor)
close(624)                              = -1 EBADF (Bad file descriptor)
close(625)                              = -1 EBADF (Bad file descriptor)
close(626)                              = -1 EBADF (Bad file descriptor)
close(627)                              = -1 EBADF (Bad file descriptor)
close(628)                              = -1 EBADF (Bad file descriptor)
close(629)                              = -1 EBADF (Bad file descriptor)
close(630)                              = -1 EBADF (Bad file descriptor)
close(631)                              = -1 EBADF (Bad file descriptor)
close(632)                              = -1 EBADF (Bad file descriptor)
close(633)                              = -1 EBADF (Bad file descriptor)
close(634)                              = -1 EBADF (Bad file descriptor)
close(635)                              = -1 EBADF (Bad file descriptor)
close(636)                              = -1 EBADF (Bad file descriptor)
close(637)                              = -1 EBADF (Bad file descriptor)
close(638)                              = -1 EBADF (Bad file descriptor)
close(639)                              = -1 EBADF (Bad file descriptor)
close(640)                              = -1 EBADF (Bad file descriptor)
close(641)                              = -1 EBADF (Bad file descriptor)
close(642)                              = -1 EBADF (Bad file descriptor)
close(643)                              = -1 EBADF (Bad file descriptor)
close(644)                              = -1 EBADF (Bad file descriptor)
close(645)                              = -1 EBADF (Bad file descriptor)
close(646)                              = -1 EBADF (Bad file descriptor)
close(647)                              = -1 EBADF (Bad file descriptor)
close(648)                              = -1 EBADF (Bad file descriptor)
close(649)                              = -1 EBADF (Bad file descriptor)
close(650)                              = -1 EBADF (Bad file descriptor)
close(651)                              = -1 EBADF (Bad file descriptor)
close(652)                              = -1 EBADF (Bad file descriptor)
close(653)                              = -1 EBADF (Bad file descriptor)
close(654)                              = -1 EBADF (Bad file descriptor)
close(655)                              = -1 EBADF (Bad file descriptor)
close(656)                              = -1 EBADF (Bad file descriptor)
close(657)                              = -1 EBADF (Bad file descriptor)
close(658)                              = -1 EBADF (Bad file descriptor)
close(659)                              = -1 EBADF (Bad file descriptor)
close(660)                              = -1 EBADF (Bad file descriptor)
close(661)                              = -1 EBADF (Bad file descriptor)
close(662)                              = -1 EBADF (Bad file descriptor)
close(663)                              = -1 EBADF (Bad file descriptor)
close(664)                              = -1 EBADF (Bad file descriptor)
close(665)                              = -1 EBADF (Bad file descriptor)
close(666)                              = -1 EBADF (Bad file descriptor)
close(667)                              = -1 EBADF (Bad file descriptor)
close(668)                              = -1 EBADF (Bad file descriptor)
close(669)                              = -1 EBADF (Bad file descriptor)
close(670)                              = -1 EBADF (Bad file descriptor)
close(671)                              = -1 EBADF (Bad file descriptor)
close(672)                              = -1 EBADF (Bad file descriptor)
close(673)                              = -1 EBADF (Bad file descriptor)
close(674)                              = -1 EBADF (Bad file descriptor)
close(675)                              = -1 EBADF (Bad file descriptor)
close(676)                              = -1 EBADF (Bad file descriptor)
close(677)                              = -1 EBADF (Bad file descriptor)
close(678)                              = -1 EBADF (Bad file descriptor)
close(679)                              = -1 EBADF (Bad file descriptor)
close(680)                              = -1 EBADF (Bad file descriptor)
close(681)                              = -1 EBADF (Bad file descriptor)
close(682)                              = -1 EBADF (Bad file descriptor)
close(683)                              = -1 EBADF (Bad file descriptor)
close(684)                              = -1 EBADF (Bad file descriptor)
close(685)                              = -1 EBADF (Bad file descriptor)
close(686)                              = -1 EBADF (Bad file descriptor)
close(687)                              = -1 EBADF (Bad file descriptor)
close(688)                              = -1 EBADF (Bad file descriptor)
close(689)                              = -1 EBADF (Bad file descriptor)
close(690)                              = -1 EBADF (Bad file descriptor)
close(691)                              = -1 EBADF (Bad file descriptor)
close(692)                              = -1 EBADF (Bad file descriptor)
close(693)                              = -1 EBADF (Bad file descriptor)
close(694)                              = -1 EBADF (Bad file descriptor)
close(695)                              = -1 EBADF (Bad file descriptor)
close(696)                              = -1 EBADF (Bad file descriptor)
close(697)                              = -1 EBADF (Bad file descriptor)
close(698)                              = -1 EBADF (Bad file descriptor)
close(699)                              = -1 EBADF (Bad file descriptor)
close(700)                              = -1 EBADF (Bad file descriptor)
close(701)                              = -1 EBADF (Bad file descriptor)
close(702)                              = -1 EBADF (Bad file descriptor)
close(703)                              = -1 EBADF (Bad file descriptor)
close(704)                              = -1 EBADF (Bad file descriptor)
close(705)                              = -1 EBADF (Bad file descriptor)
close(706)                              = -1 EBADF (Bad file descriptor)
close(707)                              = -1 EBADF (Bad file descriptor)
close(708)                              = -1 EBADF (Bad file descriptor)
close(709)                              = -1 EBADF (Bad file descriptor)
close(710)                              = -1 EBADF (Bad file descriptor)
close(711)                              = -1 EBADF (Bad file descriptor)
close(712)                              = -1 EBADF (Bad file descriptor)
close(713)                              = -1 EBADF (Bad file descriptor)
close(714)                              = -1 EBADF (Bad file descriptor)
close(715)                              = -1 EBADF (Bad file descriptor)
close(716)                              = -1 EBADF (Bad file descriptor)
close(717)                              = -1 EBADF (Bad file descriptor)
close(718)                              = -1 EBADF (Bad file descriptor)
close(719)                              = -1 EBADF (Bad file descriptor)
close(720)                              = -1 EBADF (Bad file descriptor)
close(721)                              = -1 EBADF (Bad file descriptor)
close(722)                              = -1 EBADF (Bad file descriptor)
close(723)                              = -1 EBADF (Bad file descriptor)
close(724)                              = -1 EBADF (Bad file descriptor)
close(725)                              = -1 EBADF (Bad file descriptor)
close(726)                              = -1 EBADF (Bad file descriptor)
close(727)                              = -1 EBADF (Bad file descriptor)
close(728)                              = -1 EBADF (Bad file descriptor)
close(729)                              = -1 EBADF (Bad file descriptor)
close(730)                              = -1 EBADF (Bad file descriptor)
close(731)                              = -1 EBADF (Bad file descriptor)
close(732)                              = -1 EBADF (Bad file descriptor)
close(733)                              = -1 EBADF (Bad file descriptor)
close(734)                              = -1 EBADF (Bad file descriptor)
close(735)                              = -1 EBADF (Bad file descriptor)
close(736)                              = -1 EBADF (Bad file descriptor)
close(737)                              = -1 EBADF (Bad file descriptor)
close(738)                              = -1 EBADF (Bad file descriptor)
close(739)                              = -1 EBADF (Bad file descriptor)
close(740)                              = -1 EBADF (Bad file descriptor)
close(741)                              = -1 EBADF (Bad file descriptor)
close(742)                              = -1 EBADF (Bad file descriptor)
close(743)                              = -1 EBADF (Bad file descriptor)
close(744)                              = -1 EBADF (Bad file descriptor)
close(745)                              = -1 EBADF (Bad file descriptor)
close(746)                              = -1 EBADF (Bad file descriptor)
close(747)                              = -1 EBADF (Bad file descriptor)
close(748)                              = -1 EBADF (Bad file descriptor)
close(749)                              = -1 EBADF (Bad file descriptor)
close(750)                              = -1 EBADF (Bad file descriptor)
close(751)                              = -1 EBADF (Bad file descriptor)
close(752)                              = -1 EBADF (Bad file descriptor)
close(753)                              = -1 EBADF (Bad file descriptor)
close(754)                              = -1 EBADF (Bad file descriptor)
close(755)                              = -1 EBADF (Bad file descriptor)
close(756)                              = -1 EBADF (Bad file descriptor)
close(757)                              = -1 EBADF (Bad file descriptor)
close(758)                              = -1 EBADF (Bad file descriptor)
close(759)                              = -1 EBADF (Bad file descriptor)
close(760)                              = -1 EBADF (Bad file descriptor)
close(761)                              = -1 EBADF (Bad file descriptor)
close(762)                              = -1 EBADF (Bad file descriptor)
close(763)                              = -1 EBADF (Bad file descriptor)
close(764)                              = -1 EBADF (Bad file descriptor)
close(765)                              = -1 EBADF (Bad file descriptor)
close(766)                              = -1 EBADF (Bad file descriptor)
close(767)                              = -1 EBADF (Bad file descriptor)
close(768)                              = -1 EBADF (Bad file descriptor)
close(769)                              = -1 EBADF (Bad file descriptor)
close(770)                              = -1 EBADF (Bad file descriptor)
close(771)                              = -1 EBADF (Bad file descriptor)
close(772)                              = -1 EBADF (Bad file descriptor)
close(773)                              = -1 EBADF (Bad file descriptor)
close(774)                              = -1 EBADF (Bad file descriptor)
close(775)                              = -1 EBADF (Bad file descriptor)
close(776)                              = -1 EBADF (Bad file descriptor)
close(777)                              = -1 EBADF (Bad file descriptor)
close(778)                              = -1 EBADF (Bad file descriptor)
close(779)                              = -1 EBADF (Bad file descriptor)
close(780)                              = -1 EBADF (Bad file descriptor)
close(781)                              = -1 EBADF (Bad file descriptor)
close(782)                              = -1 EBADF (Bad file descriptor)
close(783)                              = -1 EBADF (Bad file descriptor)
close(784)                              = -1 EBADF (Bad file descriptor)
close(785)                              = -1 EBADF (Bad file descriptor)
close(786)                              = -1 EBADF (Bad file descriptor)
close(787)                              = -1 EBADF (Bad file descriptor)
close(788)                              = -1 EBADF (Bad file descriptor)
close(789)                              = -1 EBADF (Bad file descriptor)
close(790)                              = -1 EBADF (Bad file descriptor)
close(791)                              = -1 EBADF (Bad file descriptor)
close(792)                              = -1 EBADF (Bad file descriptor)
close(793)                              = -1 EBADF (Bad file descriptor)
close(794)                              = -1 EBADF (Bad file descriptor)
close(795)                              = -1 EBADF (Bad file descriptor)
close(796)                              = -1 EBADF (Bad file descriptor)
close(797)                              = -1 EBADF (Bad file descriptor)
close(798)                              = -1 EBADF (Bad file descriptor)
close(799)                              = -1 EBADF (Bad file descriptor)
close(800)                              = -1 EBADF (Bad file descriptor)
close(801)                              = -1 EBADF (Bad file descriptor)
close(802)                              = -1 EBADF (Bad file descriptor)
close(803)                              = -1 EBADF (Bad file descriptor)
close(804)                              = -1 EBADF (Bad file descriptor)
close(805)                              = -1 EBADF (Bad file descriptor)
close(806)                              = -1 EBADF (Bad file descriptor)
close(807)                              = -1 EBADF (Bad file descriptor)
close(808)                              = -1 EBADF (Bad file descriptor)
close(809)                              = -1 EBADF (Bad file descriptor)
close(810)                              = -1 EBADF (Bad file descriptor)
close(811)                              = -1 EBADF (Bad file descriptor)
close(812)                              = -1 EBADF (Bad file descriptor)
close(813)                              = -1 EBADF (Bad file descriptor)
close(814)                              = -1 EBADF (Bad file descriptor)
close(815)                              = -1 EBADF (Bad file descriptor)
close(816)                              = -1 EBADF (Bad file descriptor)
close(817)                              = -1 EBADF (Bad file descriptor)
close(818)                              = -1 EBADF (Bad file descriptor)
close(819)                              = -1 EBADF (Bad file descriptor)
close(820)                              = -1 EBADF (Bad file descriptor)
close(821)                              = -1 EBADF (Bad file descriptor)
close(822)                              = -1 EBADF (Bad file descriptor)
close(823)                              = -1 EBADF (Bad file descriptor)
close(824)                              = -1 EBADF (Bad file descriptor)
close(825)                              = -1 EBADF (Bad file descriptor)
close(826)                              = -1 EBADF (Bad file descriptor)
close(827)                              = -1 EBADF (Bad file descriptor)
close(828)                              = -1 EBADF (Bad file descriptor)
close(829)                              = -1 EBADF (Bad file descriptor)
close(830)                              = -1 EBADF (Bad file descriptor)
close(831)                              = -1 EBADF (Bad file descriptor)
close(832)                              = -1 EBADF (Bad file descriptor)
close(833)                              = -1 EBADF (Bad file descriptor)
close(834)                              = -1 EBADF (Bad file descriptor)
close(835)                              = -1 EBADF (Bad file descriptor)
close(836)                              = -1 EBADF (Bad file descriptor)
close(837)                              = -1 EBADF (Bad file descriptor)
close(838)                              = -1 EBADF (Bad file descriptor)
close(839)                              = -1 EBADF (Bad file descriptor)
close(840)                              = -1 EBADF (Bad file descriptor)
close(841)                              = -1 EBADF (Bad file descriptor)
close(842)                              = -1 EBADF (Bad file descriptor)
close(843)                              = -1 EBADF (Bad file descriptor)
close(844)                              = -1 EBADF (Bad file descriptor)
close(845)                              = -1 EBADF (Bad file descriptor)
close(846)                              = -1 EBADF (Bad file descriptor)
close(847)                              = -1 EBADF (Bad file descriptor)
close(848)                              = -1 EBADF (Bad file descriptor)
close(849)                              = -1 EBADF (Bad file descriptor)
close(850)                              = -1 EBADF (Bad file descriptor)
close(851)                              = -1 EBADF (Bad file descriptor)
close(852)                              = -1 EBADF (Bad file descriptor)
close(853)                              = -1 EBADF (Bad file descriptor)
close(854)                              = -1 EBADF (Bad file descriptor)
close(855)                              = -1 EBADF (Bad file descriptor)
close(856)                              = -1 EBADF (Bad file descriptor)
close(857)                              = -1 EBADF (Bad file descriptor)
close(858)                              = -1 EBADF (Bad file descriptor)
close(859)                              = -1 EBADF (Bad file descriptor)
close(860)                              = -1 EBADF (Bad file descriptor)
close(861)                              = -1 EBADF (Bad file descriptor)
close(862)                              = -1 EBADF (Bad file descriptor)
close(863)                              = -1 EBADF (Bad file descriptor)
close(864)                              = -1 EBADF (Bad file descriptor)
close(865)                              = -1 EBADF (Bad file descriptor)
close(866)                              = -1 EBADF (Bad file descriptor)
close(867)                              = -1 EBADF (Bad file descriptor)
close(868)                              = -1 EBADF (Bad file descriptor)
close(869)                              = -1 EBADF (Bad file descriptor)
close(870)                              = -1 EBADF (Bad file descriptor)
close(871)                              = -1 EBADF (Bad file descriptor)
close(872)                              = -1 EBADF (Bad file descriptor)
close(873)                              = -1 EBADF (Bad file descriptor)
close(874)                              = -1 EBADF (Bad file descriptor)
close(875)                              = -1 EBADF (Bad file descriptor)
close(876)                              = -1 EBADF (Bad file descriptor)
close(877)                              = -1 EBADF (Bad file descriptor)
close(878)                              = -1 EBADF (Bad file descriptor)
close(879)                              = -1 EBADF (Bad file descriptor)
close(880)                              = -1 EBADF (Bad file descriptor)
close(881)                              = -1 EBADF (Bad file descriptor)
close(882)                              = -1 EBADF (Bad file descriptor)
close(883)                              = -1 EBADF (Bad file descriptor)
close(884)                              = -1 EBADF (Bad file descriptor)
close(885)                              = -1 EBADF (Bad file descriptor)
close(886)                              = -1 EBADF (Bad file descriptor)
close(887)                              = -1 EBADF (Bad file descriptor)
close(888)                              = -1 EBADF (Bad file descriptor)
close(889)                              = -1 EBADF (Bad file descriptor)
close(890)                              = -1 EBADF (Bad file descriptor)
close(891)                              = -1 EBADF (Bad file descriptor)
close(892)                              = -1 EBADF (Bad file descriptor)
close(893)                              = -1 EBADF (Bad file descriptor)
close(894)                              = -1 EBADF (Bad file descriptor)
close(895)                              = -1 EBADF (Bad file descriptor)
close(896)                              = -1 EBADF (Bad file descriptor)
close(897)                              = -1 EBADF (Bad file descriptor)
close(898)                              = -1 EBADF (Bad file descriptor)
close(899)                              = -1 EBADF (Bad file descriptor)
close(900)                              = -1 EBADF (Bad file descriptor)
close(901)                              = -1 EBADF (Bad file descriptor)
close(902)                              = -1 EBADF (Bad file descriptor)
close(903)                              = -1 EBADF (Bad file descriptor)
close(904)                              = -1 EBADF (Bad file descriptor)
close(905)                              = -1 EBADF (Bad file descriptor)
close(906)                              = -1 EBADF (Bad file descriptor)
close(907)                              = -1 EBADF (Bad file descriptor)
close(908)                              = -1 EBADF (Bad file descriptor)
close(909)                              = -1 EBADF (Bad file descriptor)
close(910)                              = -1 EBADF (Bad file descriptor)
close(911)                              = -1 EBADF (Bad file descriptor)
close(912)                              = -1 EBADF (Bad file descriptor)
close(913)                              = -1 EBADF (Bad file descriptor)
close(914)                              = -1 EBADF (Bad file descriptor)
close(915)                              = -1 EBADF (Bad file descriptor)
close(916)                              = -1 EBADF (Bad file descriptor)
close(917)                              = -1 EBADF (Bad file descriptor)
close(918)                              = -1 EBADF (Bad file descriptor)
close(919)                              = -1 EBADF (Bad file descriptor)
close(920)                              = -1 EBADF (Bad file descriptor)
close(921)                              = -1 EBADF (Bad file descriptor)
close(922)                              = -1 EBADF (Bad file descriptor)
close(923)                              = -1 EBADF (Bad file descriptor)
close(924)                              = -1 EBADF (Bad file descriptor)
close(925)                              = -1 EBADF (Bad file descriptor)
close(926)                              = -1 EBADF (Bad file descriptor)
close(927)                              = -1 EBADF (Bad file descriptor)
close(928)                              = -1 EBADF (Bad file descriptor)
close(929)                              = -1 EBADF (Bad file descriptor)
close(930)                              = -1 EBADF (Bad file descriptor)
close(931)                              = -1 EBADF (Bad file descriptor)
close(932)                              = -1 EBADF (Bad file descriptor)
close(933)                              = -1 EBADF (Bad file descriptor)
close(934)                              = -1 EBADF (Bad file descriptor)
close(935)                              = -1 EBADF (Bad file descriptor)
close(936)                              = -1 EBADF (Bad file descriptor)
close(937)                              = -1 EBADF (Bad file descriptor)
close(938)                              = -1 EBADF (Bad file descriptor)
close(939)                              = -1 EBADF (Bad file descriptor)
close(940)                              = -1 EBADF (Bad file descriptor)
close(941)                              = -1 EBADF (Bad file descriptor)
close(942)                              = -1 EBADF (Bad file descriptor)
close(943)                              = -1 EBADF (Bad file descriptor)
close(944)                              = -1 EBADF (Bad file descriptor)
close(945)                              = -1 EBADF (Bad file descriptor)
close(946)                              = -1 EBADF (Bad file descriptor)
close(947)                              = -1 EBADF (Bad file descriptor)
close(948)                              = -1 EBADF (Bad file descriptor)
close(949)                              = -1 EBADF (Bad file descriptor)
close(950)                              = -1 EBADF (Bad file descriptor)
close(951)                              = -1 EBADF (Bad file descriptor)
close(952)                              = -1 EBADF (Bad file descriptor)
close(953)                              = -1 EBADF (Bad file descriptor)
close(954)                              = -1 EBADF (Bad file descriptor)
close(955)                              = -1 EBADF (Bad file descriptor)
close(956)                              = -1 EBADF (Bad file descriptor)
close(957)                              = -1 EBADF (Bad file descriptor)
close(958)                              = -1 EBADF (Bad file descriptor)
close(959)                              = -1 EBADF (Bad file descriptor)
close(960)                              = -1 EBADF (Bad file descriptor)
close(961)                              = -1 EBADF (Bad file descriptor)
close(962)                              = -1 EBADF (Bad file descriptor)
close(963)                              = -1 EBADF (Bad file descriptor)
close(964)                              = -1 EBADF (Bad file descriptor)
close(965)                              = -1 EBADF (Bad file descriptor)
close(966)                              = -1 EBADF (Bad file descriptor)
close(967)                              = -1 EBADF (Bad file descriptor)
close(968)                              = -1 EBADF (Bad file descriptor)
close(969)                              = -1 EBADF (Bad file descriptor)
close(970)                              = -1 EBADF (Bad file descriptor)
close(971)                              = -1 EBADF (Bad file descriptor)
close(972)                              = -1 EBADF (Bad file descriptor)
close(973)                              = -1 EBADF (Bad file descriptor)
close(974)                              = -1 EBADF (Bad file descriptor)
close(975)                              = -1 EBADF (Bad file descriptor)
close(976)                              = -1 EBADF (Bad file descriptor)
close(977)                              = -1 EBADF (Bad file descriptor)
close(978)                              = -1 EBADF (Bad file descriptor)
close(979)                              = -1 EBADF (Bad file descriptor)
close(980)                              = -1 EBADF (Bad file descriptor)
close(981)                              = -1 EBADF (Bad file descriptor)
close(982)                              = -1 EBADF (Bad file descriptor)
close(983)                              = -1 EBADF (Bad file descriptor)
close(984)                              = -1 EBADF (Bad file descriptor)
close(985)                              = -1 EBADF (Bad file descriptor)
close(986)                              = -1 EBADF (Bad file descriptor)
close(987)                              = -1 EBADF (Bad file descriptor)
close(988)                              = -1 EBADF (Bad file descriptor)
close(989)                              = -1 EBADF (Bad file descriptor)
close(990)                              = -1 EBADF (Bad file descriptor)
close(991)                              = -1 EBADF (Bad file descriptor)
close(992)                              = -1 EBADF (Bad file descriptor)
close(993)                              = -1 EBADF (Bad file descriptor)
close(994)                              = -1 EBADF (Bad file descriptor)
close(995)                              = -1 EBADF (Bad file descriptor)
close(996)                              = -1 EBADF (Bad file descriptor)
close(997)                              = -1 EBADF (Bad file descriptor)
close(998)                              = -1 EBADF (Bad file descriptor)
close(999)                              = -1 EBADF (Bad file descriptor)
close(1000)                             = -1 EBADF (Bad file descriptor)
close(1001)                             = -1 EBADF (Bad file descriptor)
close(1002)                             = -1 EBADF (Bad file descriptor)
close(1003)                             = -1 EBADF (Bad file descriptor)
close(1004)                             = -1 EBADF (Bad file descriptor)
close(1005)                             = -1 EBADF (Bad file descriptor)
close(1006)                             = -1 EBADF (Bad file descriptor)
close(1007)                             = -1 EBADF (Bad file descriptor)
close(1008)                             = -1 EBADF (Bad file descriptor)
close(1009)                             = -1 EBADF (Bad file descriptor)
close(1010)                             = -1 EBADF (Bad file descriptor)
close(1011)                             = -1 EBADF (Bad file descriptor)
close(1012)                             = -1 EBADF (Bad file descriptor)
close(1013)                             = -1 EBADF (Bad file descriptor)
close(1014)                             = -1 EBADF (Bad file descriptor)
close(1015)                             = -1 EBADF (Bad file descriptor)
close(1016)                             = -1 EBADF (Bad file descriptor)
close(1017)                             = -1 EBADF (Bad file descriptor)
close(1018)                             = -1 EBADF (Bad file descriptor)
close(1019)                             = -1 EBADF (Bad file descriptor)
close(1020)                             = -1 EBADF (Bad file descriptor)
close(1021)                             = -1 EBADF (Bad file descriptor)
close(1022)                             = -1 EBADF (Bad file descriptor)
close(1023)                             = -1 EBADF (Bad file descriptor)
fcntl64(0, F_GETFD)                     = 0
fcntl64(1, F_GETFD)                     = 0
fcntl64(2, F_GETFD)                     = 0
uname({sys="Linux", node="iugo", ...})  = 0
umask(0)                                = 02
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
socket(PF_FILE, SOCK_STREAM|SOCK_CLOEXEC|SOCK_NONBLOCK, 0) = 3
connect(3, {sa_family=AF_FILE, path="/var/run/nscd/socket"}, 110) = -1 ENOENT (No such file or directory)
close(3)                                = 0
open("/etc/nsswitch.conf", O_RDONLY|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=513, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb778f000
read(3, "# /etc/nsswitch.conf\n#\n# Example"..., 4096) = 513
read(3, "", 4096)                       = 0
close(3)                                = 0
munmap(0xb778f000, 4096)                = 0
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=72636, ...}) = 0
mmap2(NULL, 72636, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb777e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libnss_compat.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\300\r\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=30552, ...}) = 0
mmap2(NULL, 33360, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb75ca000
mmap2(0xb75d1000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x6) = 0xb75d1000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libnsl.so.1", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0`1\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=92028, ...}) = 0
mmap2(NULL, 104424, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb75b0000
mmap2(0xb75c6000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x15) = 0xb75c6000
mmap2(0xb75c8000, 6120, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_ANONYMOUS, -1, 0) = 0xb75c8000
close(3)                                = 0
mprotect(0xb75c6000, 4096, PROT_READ)   = 0
mprotect(0xb75d1000, 4096, PROT_READ)   = 0
munmap(0xb777e000, 72636)               = 0
open("/etc/ld.so.cache", O_RDONLY|O_CLOEXEC) = 3
fstat64(3, {st_mode=S_IFREG|0644, st_size=72636, ...}) = 0
mmap2(NULL, 72636, PROT_READ, MAP_PRIVATE, 3, 0) = 0xb777e000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libnss_nis.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0p\31\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=42664, ...}) = 0
mmap2(NULL, 45640, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb75a4000
mmap2(0xb75ae000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0x9) = 0xb75ae000
close(3)                                = 0
access("/etc/ld.so.nohwcap", F_OK)      = -1 ENOENT (No such file or directory)
open("/lib/i386-linux-gnu/libnss_files.so.2", O_RDONLY|O_CLOEXEC) = 3
read(3, "\177ELF\1\1\1\0\0\0\0\0\0\0\0\0\3\0\3\0\1\0\0\0\20\32\0\0004\0\0\0"..., 512) = 512
fstat64(3, {st_mode=S_IFREG|0644, st_size=47072, ...}) = 0
mmap2(NULL, 50212, PROT_READ|PROT_EXEC, MAP_PRIVATE|MAP_DENYWRITE, 3, 0) = 0xb7597000
mmap2(0xb75a2000, 8192, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_FIXED|MAP_DENYWRITE, 3, 0xa) = 0xb75a2000
close(3)                                = 0
mprotect(0xb75a2000, 4096, PROT_READ)   = 0
mprotect(0xb75ae000, 4096, PROT_READ)   = 0
munmap(0xb777e000, 72636)               = 0
open("/etc/passwd", O_RDONLY|O_CLOEXEC) = 3
_llseek(3, 0, [0], SEEK_CUR)            = 0
fstat64(3, {st_mode=S_IFREG|0644, st_size=1705, ...}) = 0
mmap2(NULL, 1705, PROT_READ, MAP_SHARED, 3, 0) = 0xb778f000
_llseek(3, 1705, [1705], SEEK_SET)      = 0
munmap(0xb778f000, 1705)                = 0
close(3)                                = 0
getuid32()                              = 1000
geteuid32()                             = 1000
rt_sigaction(SIGINT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGINT, {0x80560d0, [], SA_INTERRUPT}, NULL, 8) = 0
rt_sigaction(SIGHUP, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGHUP, {0x80560d0, [], SA_INTERRUPT}, NULL, 8) = 0
rt_sigaction(SIGQUIT, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGQUIT, {0x80560d0, [], SA_INTERRUPT}, NULL, 8) = 0
rt_sigaction(SIGTERM, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGTERM, {0x80560d0, [], SA_INTERRUPT}, NULL, 8) = 0
rt_sigaction(SIGPIPE, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigaction(SIGPIPE, {0x80560d0, [], SA_INTERRUPT}, NULL, 8) = 0
open("/etc/uucp/port", O_RDONLY)        = -1 ENOENT (No such file or directory)
open("/etc/uucp/L-devices", O_RDONLY)   = -1 ENOENT (No such file or directory)
open("/etc/uucp/Devices", O_RDONLY)     = -1 ENOENT (No such file or directory)
creat("/var/lock/TMP0000000c43", 0644)  = 3
write(3, "      3139\n", 11)            = 11
close(3)                                = 0
link("/var/lock/TMP0000000c43", "/var/lock/LCK..ttyS0") = 0
unlink("/var/lock/TMP0000000c43")       = 0
geteuid32()                             = 1000
getuid32()                              = 1000
getegid32()                             = 1000
getgid32()                              = 1000
setregid32(1000, 1000)                  = 0
setreuid32(1000, 1000)                  = 0
open("/dev/ttyS0", O_RDWR|O_NONBLOCK)   = 3
geteuid32()                             = 1000
getuid32()                              = 1000
getegid32()                             = 1000
getgid32()                              = 1000
setregid32(1000, 1000)                  = 0
setreuid32(1000, 1000)                  = 0
fcntl64(3, F_GETFD)                     = 0
fcntl64(3, F_SETFD, FD_CLOEXEC)         = 0
access("/dev/ttyS0", R_OK|W_OK)         = 0
fcntl64(3, F_GETFL)                     = 0x802 (flags O_RDWR|O_NONBLOCK)
fcntl64(3, F_SETFL, O_RDWR)             = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, TCFLSH, 0)                     = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_START or TCSETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, TIOCSCTTY)                     = -1 EPERM (Operation not permitted)
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_START or TCSETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_STOP or TCSETSW, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
access("/dev/ttyS0", R_OK|W_OK)         = 0
fstat64(1, {st_mode=S_IFCHR|0620, st_rdev=makedev(136, 0), ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb778f000
write(1, "\7Connected.\n", 12)          = 12
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(0, SNDCTL_TMR_START or TCSETS, {B38400 -opost -isig -icanon -echo ...}) = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 -opost -isig -icanon -echo ...}) = 0
pipe([4, 5])                            = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb75d3968) = 3140
close(5)                                = 0
read(0, "~", 1)                         = 1
write(1, "~", 1)                        = 1
rt_sigaction(SIGALRM, {0x8051450, [], SA_INTERRUPT}, NULL, 8) = 0
alarm(1)                                = 0
read(0, ".", 1)                         = 1
rt_sigaction(SIGALRM, {SIG_IGN, [], SA_INTERRUPT}, NULL, 8) = 0
alarm(0)                                = 1
write(1, ".", 1)                        = 1
close(4)                                = 0
kill(3140, SIGTERM)                     = 0
rt_sigaction(SIGALRM, {0x8051470, [], SA_INTERRUPT}, NULL, 8) = 0
alarm(2)                                = 0
waitpid(3140, [{WIFEXITED(s) && WEXITSTATUS(s) == 0}], 0) = 3140
--- SIGCHLD (Child exited) @ 0 (0) ---
rt_sigaction(SIGALRM, {SIG_IGN, [], SA_INTERRUPT}, NULL, 8) = 0
alarm(0)                                = 2
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 -opost -isig -icanon -echo ...}) = 0
ioctl(0, SNDCTL_TMR_START or TCSETS, {B38400 opost isig icanon echo ...}) = 0
ioctl(0, SNDCTL_TMR_TIMEBASE or TCGETS, {B38400 opost isig icanon echo ...}) = 0
rt_sigaction(SIGALRM, {0x8053a90, [], SA_INTERRUPT}, NULL, 8) = 0
alarm(30)                               = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_STOP or TCSETSW, {B115200 -opost -isig -icanon -echo ...}) = 0
ioctl(3, SNDCTL_TMR_TIMEBASE or TCGETS, {B115200 -opost -isig -icanon -echo ...}) = 0
rt_sigaction(SIGALRM, {SIG_IGN, [], SA_INTERRUPT}, NULL, 8) = 0
alarm(0)                                = 30
ioctl(3, TIOCNOTTY)                     = -1 ENOTTY (Inappropriate ioctl for device)
close(3)                                = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGCHLD, NULL, {SIG_DFL, [], 0}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
nanosleep({2, 0}, 0xbfd1c1f8)           = 0
unlink("/var/lock/LCK..ttyS0")          = 0
write(1, "\n", 1)                       = 1
write(1, "\7Disconnected.\n", 15)       = 15
exit_group(0)                           = ?[/SIZE]
```

$ cat STRACE_CU.3140
```
[SIZE="1"]close(4)                                = 0
fcntl64(3, F_GETFL)                     = 0x2 (flags O_RDWR)
fcntl64(3, F_SETFL, O_RDWR)             = 0
rt_sigaction(SIGUSR1, {0x8051460, [], SA_INTERRUPT}, NULL, 8) = 0
rt_sigaction(SIGUSR2, {0x8051460, [], SA_INTERRUPT}, NULL, 8) = 0
rt_sigaction(SIGINT, {SIG_IGN, [], SA_INTERRUPT}, NULL, 8) = 0
rt_sigaction(SIGQUIT, {SIG_IGN, [], SA_INTERRUPT}, NULL, 8) = 0
rt_sigaction(SIGPIPE, {SIG_DFL, [], SA_INTERRUPT}, NULL, 8) = 0
rt_sigaction(SIGTERM, {0x8051460, [], SA_INTERRUPT}, NULL, 8) = 0
read(3, 0xbfd1be0c, 1024)               = ? ERESTARTSYS (To be restarted)
--- SIGTERM (Terminated) @ 0 (0) ---
sigreturn()                             = ? (mask now [])
exit_group(0)                           = ?[/SIZE]
```

***i'd love some help on this!***

---

### Post by ummelum on 2012-12-11
let's bump this thread by stating, in bold, **that it has more than five hundred views, and not a single reaction** :)

---

### Post by ummelum on 2012-12-11
$ cu -l /dev/ttyS0 -s 115200 --debug all
```
cu: fconn_open: Opening port /dev/ttyS0 (speed 115200)
cu: fconn_set: Changing setting to 0, 0, 2
Connected.
~.cu: Exit status 0
cu: fconn_close: Closing connection
```

---

### Post by ummelum on 2012-12-13
bump.

later this week, i'm going to boot old live cd's of ubuntu, to pinpoint when this problem exactly cropped up.

if that doesn't bring any enlightenment or solution, ubuntu goes out the door forever. i can't be arsed to set up a desktop with it, when it takes weeks to get a signal across a serial cable.

---

### Post by ummelum on 2012-12-17
final bump & goodbye!

---

### Post by ummelum on 2012-12-31
solved, but not fixed.

cu always sets hardware flow control, and there is no way of controlling this behaviour. this was already a known problem in 1995: [http://web.archiveorange.com/archive/v/iBpRaJf4WODgPva7sywW]("http://web.archiveorange.com/archive/v/iBpRaJf4WODgPva7sywW")

---

