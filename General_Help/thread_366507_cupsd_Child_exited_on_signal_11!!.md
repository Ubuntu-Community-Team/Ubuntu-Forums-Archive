---
title: "cupsd: Child exited on signal 11!!?????"
date: 2007-02-20
forum: General Help
---

### Post by GeryonD on 2007-02-20
This seems to be a problem with cups.  I tried to print today (it was working fine prior to this) I was told the cupsd server could not be contacted.  A closer look revealed it was not running.  It tried restarting it and received the error below:

```

# /etc/init.d/cupsys restart
 * Restarting Common Unix Printing System: cupsd 
cupsd: Child exited on signal 11!
```

So I removed everything from '/var/spool/cups' and tried again to no avail.  I did notice that prior to this problem the printer was out of paper and a print job had stopped mid-way through.  I wasn't the last person to use the printer.

Anyway, next I ran an strace against '/usr/sbin/cupsd' and it went something like this, I'll past only the end of it:

```

# strace /usr/sbin/cupsd
execve("/usr/sbin/cupsd", ["/usr/sbin/cupsd"], [/* 16 vars */]) = 0
.
.
.
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7c15000
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7c14000
set_thread_area({entry_number:-1 -> 6, base_addr:0xb7c146b0, limit:1048575, seg_32bit:1, contents:0, read_exec_only:0  imit_in_pages:1, seg_not_present:0, useable:1}) = 0
mprotect(0xb7df3000, 8192, PROT_READ)   = 0
munmap(0xb7f99000, 81020)               = 0
set_tid_address(0xb7c146f8)             = 5506
rt_sigaction(SIGRTMIN, {0xb7e53720, [], SA_SIGINFO}, NULL, 8) = 0
rt_sigaction(SIGRT_1, {0xb7e53640, [], SA_RESTART|SA_SIGINFO}, NULL, 8) = 0
rt_sigprocmask(SIG_UNBLOCK, [RTMIN RT_1], NULL, 8) = 0
getrlimit(RLIMIT_STACK, {rlim_cur=8192*1024, rlim_max=RLIM_INFINITY}) = 0
_sysctl({{CTL_KERN, KERN_VERSION}, 2, 0xbf9cf1c0, 30, (nil), 0}) = 0
brk(0)                                  = 0x809d000
brk(0x80be000)                          = 0x80be000
rt_sigaction(SIGUSR1, {0x8066340, [USR1], 0}, NULL, 8) = 0
rt_sigaction(SIGCHLD, {0x8066340, [USR1], 0}, NULL, 8) = 0
rt_sigaction(SIGHUP, {SIG_IGN}, NULL, 8) = 0
clone(child_stack=0, flags=CLONE_CHILD_CLEARTID|CLONE_CHILD_SETTID|SIGCHLD, child_tidptr=0xb7c146f8) = 5507
rt_sigprocmask(SIG_BLOCK, [CHLD], [], 8) = 0
rt_sigaction(SIGCHLD, NULL, {0x8066340, [USR1], 0}, 8) = 0
rt_sigprocmask(SIG_SETMASK, [], NULL, 8) = 0
nanosleep({1, 0}, 0xbf9caee4)           = ? ERESTART_RESTARTBLOCK (To be restarted)
--- SIGCHLD (Child exited) @ 0 (0) ---
sigreturn()                             = ? (mask now [])
wait4(-1, [{WIFSIGNALED(s) && WTERMSIG(s) == SIGSEGV && WCOREDUMP(s)}], 0, NULL) = 5507
write(2, "cupsd: Child exited on signal 11"..., 34cupsd: Child exited on signal 11!
) = 34
exit_group(3)                           = ?
Process 5506 detached

```

I don't know if it matter but for what it's worth the printer is an HP psc 1210 scanner/printer.  It's connected via USB.

```

# dmesg | grep -i usb.*printer
[17179597.624000] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 1 alt 0 proto 2 vid 0x03F0 pid 0x2F11
[17179597.624000] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver

```

and from '/proc/bus/usb/devices':

```

T:  Bus=01 Lev=01 Prnt=01 Port=00 Cnt=01 Dev#=  2 Spd=12  MxCh= 0
D:  Ver= 2.00 Cls=00(>ifc ) Sub=00 Prot=00 MxPS= 8 #Cfgs=  1
P:  Vendor=03f0 ProdID=2f11 Rev= 1.00
S:  Manufacturer=Hewlett-Packard
S:  Product=psc 1200 series
S:  SerialNumber=MY31H1201Y5H
C:* #Ifs= 3 Cfg#= 1 Atr=c0 MxPwr=  2mA
I:  If#= 0 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=cc Prot=00 Driver=(none)
E:  Ad=01(O) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=81(I) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=82(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 1 Alt= 0 #EPs= 3 Cls=07(print) Sub=01 Prot=02 Driver=usblp
E:  Ad=03(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=83(I) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=84(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 2 Alt= 0 #EPs= 3 Cls=ff(vend.) Sub=ff Prot=ff Driver=(none)
E:  Ad=05(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=85(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=86(I) Atr=03(Int.) MxPS=   8 Ivl=10ms
I:  If#= 2 Alt= 1 #EPs= 3 Cls=ff(vend.) Sub=d4 Prot=00 Driver=(none)
E:  Ad=05(O) Atr=02(Bulk) MxPS=  32 Ivl=0ms
E:  Ad=85(I) Atr=02(Bulk) MxPS=  64 Ivl=0ms
E:  Ad=86(I) Atr=03(Int.) MxPS=   8 Ivl=10ms

```

I am running Ubuntu 6.10 which was upgraded from 6.06.  It worked in 6.06 and in 6.10 for the past few months without a problem.  Does anyone have any ideas/suggestions?  Thanks.

---

### Post by GeryonD on 2007-03-04
Does anyone have any ideas regarding this issue or where else I could possibly go for help?  Thanks!

---

### Post by GeryonD on 2007-03-11
Okay, solved my problem.  If anyone else is interested here's what I found.  Running 'cupsd' with the '-f' runs it in the foreground (as apposed to being ran as a daemon).  From there I got a more accurate strace.  I found this in my strace:

```

open("/etc/hosts", O_RDONLY)            = 4
fcntl64(4, F_GETFD)                     = 0
fcntl64(4, F_SETFD, FD_CLOEXEC)         = 0
fstat64(4, {st_mode=S_IFREG|0644, st_size=24595, ...}) = 0
mmap2(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0xb7f88000
read(4, "## $id$\n127.0.0.1 localhost \nlan"..., 4096) = 4096
read(4, "m www2.burstnet.com www4.trix.ne"..., 4096) = 4096
close(4)                                = 0

```

So it's trying to read my 'hosts' file.  I noticed on the second read line there there is more than one host.  So I checked my hosts file and sure enough my hosts file was completely fubared.  Every host I had in there (1,270 of them) was all appended on a single line, which was, I am guessing too large to read in causing the segfault.  I simply put each host back on it's own line again and viola, cupsd started right up and I am printing again.

---

