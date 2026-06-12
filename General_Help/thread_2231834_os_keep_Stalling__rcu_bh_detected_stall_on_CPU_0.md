---
title: "os keep Stalling : rcu_bh detected stall on CPU 0"
date: 2014-06-28
forum: General Help
---

### Post by zylmak on 2014-06-28
Hi i just installed ubuntu 14.04 server on a toshiba nb305 and since the installation the system keep stalling giving the error rcu_bh detected stall on CPU

I dont know if this is relevent or not I found thin in the syslog

Jun 28 07:17:01 nb305 CRON[2459]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jun 28 07:39:14 nb305 kernel: [ 3110.420643] INFO: rcu_sched self-detected stall on CPU { 0}  (t=51524 jiffies g=30673 c=30672 q=0)
Jun 28 07:39:14 nb305 kernel: [ 3110.420873] sending NMI to all CPUs:
Jun 28 07:39:14 nb305 kernel: [ 3110.420890] NMI backtrace for cpu 0
Jun 28 07:39:14 nb305 kernel: [ 3110.420899] CPU: 0 PID: 0 Comm: swapper/0 Not tainted 3.13.0-30-generic #54-Ubuntu
Jun 28 07:39:14 nb305 kernel: [ 3110.420903] Hardware name: TOSHIBA TOSHIBA NB305/NPVAA, BIOS V1.30 01/14/2010
Jun 28 07:39:14 nb305 kernel: [ 3110.420910] task: ffffffff81c15480 ti: ffffffff81c00000 task.ti: ffffffff81c00000
Jun 28 07:39:14 nb305 kernel: [ 3110.420915] RIP: 0010:[<ffffffff8136fe73>]  [<ffffffff8136fe73>] __bitmap_empty+0x3/0x80
Jun 28 07:39:14 nb305 kernel: [ 3110.420934] RSP: 0018:ffff88003f203bb8  EFLAGS: 00000046
Jun 28 07:39:14 nb305 kernel: [ 3110.420939] RAX: 0000000000000000 RBX: 0000000000002710 RCX: 000000000000013f
Jun 28 07:39:14 nb305 kernel: [ 3110.420943] RDX: 0000000000000c00 RSI: 0000000000000100 RDI: ffffffff81d13120
Jun 28 07:39:14 nb305 kernel: [ 3110.420947] RBP: ffff88003f203bc8 R08: 0000000000000082 R09: ffffffff81ecc970
Jun 28 07:39:14 nb305 kernel: [ 3110.420952] R10: 0000000000030c54 R11: 0000000000040000 R12: ffffffff81c4e180
Jun 28 07:39:14 nb305 kernel: [ 3110.420956] R13: ffffffff81d135a0 R14: ffffffff81c4e180 R15: 0000000000000000
Jun 28 07:39:14 nb305 kernel: [ 3110.420963] FS:  0000000000000000(0000) GS:ffff88003f200000(0000) knlGS:0000000000000000
Jun 28 07:39:14 nb305 kernel: [ 3110.420967] CS:  0010 DS: 0000 ES: 0000 CR0: 000000008005003b
Jun 28 07:39:14 nb305 kernel: [ 3110.420972] CR2: 0000000000e19008 CR3: 0000000001c0e000 CR4: 00000000000007f0

OS
Linux 3.13.0-30-generic #54-Ubuntu SMP Mon Jun 9 22:45:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Memory
             total       used       free     shared    buffers     cached
Mem:       1007388     844476     162912      12836       7176     204756
-/+ buffers/cache:     632544     374844
Swap:      1036284        604    1035680

Disk
Filesystem     1K-blocks    Used Available Use% Mounted on
/dev/sda1      239212096 2634932 224402780   2% /
none                   4       0         4   0% /sys/fs/cgroup
udev              492848       4    492844   1% /dev
tmpfs             100740     648    100092   1% /run
none                5120       4      5116   1% /run/lock
none              503692       0    503692   0% /run/shm
none              102400       0    102400   0% /run/user

---

