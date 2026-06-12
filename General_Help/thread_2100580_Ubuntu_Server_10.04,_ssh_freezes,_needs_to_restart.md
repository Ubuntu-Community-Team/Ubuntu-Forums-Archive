---
title: "Ubuntu Server 10.04, ssh freezes, needs to restart server"
date: 2013-01-02
forum: General Help
---

### Post by dnotivol on 2013-01-02
Hello all,

We're using a bunch of servers ( Dell PowerEdge R310 ) running Ubuntu 10.04.4 server edition. We're having some problems with them that force us to restart them to recover the system. The problem is idientified because we try to log into the servers via SSH, but after typing the password, and the access is granted, anything can be done in the cli. The ssh session is not finished, but the server doesn't reply to any command (it doesn't show even the echo of what we type).

In the logs, we found some ssh and kernel messages at the time of the problem (memory dumps?).

The servers are remote-located so we can't login through console to see what's happening, we can only restart the servers physically to recover the access. This problem happens in some of the servers in a random time pattern. 

Does this sounds familiar to anyone? Any clue about it?
Thanks in advance.


Below you can find some information about ht server (OS, kernel), and some log excerpts for the time when we found the problem.


root@localhost:~# cat /etc/issue
Ubuntu 10.04.4 LTS \n \l

root@localhost:~# uname -a
Linux localhost 2.6.32-41-server #91-Ubuntu SMP Wed Jun 13 11:58:56 UTC 2012 x86_64 GNU/Linux

root@localhost:~# sshd -v
sshd: illegal option -- v
OpenSSH_5.3p1 Debian-3ubuntu7, OpenSSL 0.9.8k 25 Mar 2009

Dec 21 10:48:39 localhost kernel: [11193617.447443] sshd          D 00000000ffffffff     0 12162    955 0x00000000
Dec 21 10:48:39 localhost kernel: [11193617.447447]  ffff8800abc5f758 0000000000000082 0000000000015e00 0000000000015e00
Dec 21 10:48:39 localhost kernel: [11193617.447451]  ffff8801152103d0 ffff8800abc5ffd8 0000000000015e00 ffff880115210000
Dec 21 10:48:39 localhost kernel: [11193617.447454]  0000000000015e00 ffff8800abc5ffd8 0000000000015e00 ffff8801152103d0
Dec 21 10:48:39 localhost kernel: [11193617.447457] Call Trace:
Dec 21 10:48:39 localhost kernel: [11193617.447465]  [<ffffffff8155f08d>] schedule_timeout+0x22d/0x300
Dec 21 10:48:39 localhost kernel: [11193617.447469]  [<ffffffff8105a156>] ? update_curr+0xe6/0x1e0
Dec 21 10:48:39 localhost kernel: [11193617.447472]  [<ffffffff81060980>] ? load_balance_next_fair+0x0/0x80
Dec 21 10:48:39 localhost kernel: [11193617.447476]  [<ffffffff8101a113>] ? native_sched_clock+0x13/0x80
Dec 21 10:48:39 localhost kernel: [11193617.447479]  [<ffffffff810631b1>] ? dequeue_entity+0x1a1/0x1e0
Dec 21 10:48:39 localhost kernel: [11193617.447482]  [<ffffffff8155e206>] wait_for_common+0xd6/0x180
Dec 21 10:48:39 localhost kernel: [11193617.447485]  [<ffffffff8105deb0>] ? default_wake_function+0x0/0x20
Dec 21 10:48:39 localhost kernel: [11193617.447487]  [<ffffffff8155e36d>] wait_for_completion+0x1d/0x20
Dec 21 10:48:39 localhost kernel: [11193617.447490]  [<ffffffff81081e93>] flush_work+0x73/0xc0
Dec 21 10:48:39 localhost kernel: [11193617.447493]  [<ffffffff81081ee0>] ? wq_barrier_func+0x0/0x20
Dec 21 10:48:39 localhost kernel: [11193617.447495]  [<ffffffff81082154>] flush_delayed_work+0x54/0x70
Dec 21 10:48:39 localhost kernel: [11193617.447500]  [<ffffffff81339ba5>] tty_flush_to_ldisc+0x15/0x20
Dec 21 10:48:39 localhost kernel: [11193617.447502]  [<ffffffff813348c7>] n_tty_poll+0x67/0x1e0
Dec 21 10:48:39 localhost kernel: [11193617.447505]  [<ffffffff8133009a>] tty_poll+0x8a/0xa0
Dec 21 10:48:39 localhost kernel: [11193617.447509]  [<ffffffff81158ea2>] do_select+0x3a2/0x6d0
Dec 21 10:48:39 localhost kernel: [11193617.447512]  [<ffffffff811591d0>] ? __pollwait+0x0/0xf0
Dec 21 10:48:39 localhost kernel: [11193617.447515]  [<ffffffff811592c0>] ? pollwake+0x0/0x60
Dec 21 10:48:39 localhost kernel: [11193617.447518]  [<ffffffff811592c0>] ? pollwake+0x0/0x60
Dec 21 10:48:39 localhost kernel: [11193617.447521]  [<ffffffff811592c0>] ? pollwake+0x0/0x60
Dec 21 10:48:39 localhost kernel: [11193617.447523]  [<ffffffff811592c0>] ? pollwake+0x0/0x60
Dec 21 10:48:39 localhost kernel: [11193617.447526]  [<ffffffff8105a156>] ? update_curr+0xe6/0x1e0
Dec 21 10:48:39 localhost kernel: [11193617.447529]  [<ffffffff81064251>] ? check_preempt_wakeup+0x41/0x3c0
Dec 21 10:48:39 localhost kernel: [11193617.447531]  [<ffffffff8105dd2b>] ? try_to_wake_up+0x2fb/0x480
Dec 21 10:48:39 localhost kernel: [11193617.447534]  [<ffffffff81337a6a>] ? copy_termios+0x6a/0x80
Dec 21 10:48:39 localhost kernel: [11193617.447537]  [<ffffffff81338085>] ? tty_mode_ioctl+0xc5/0x4b0
Dec 21 10:48:39 localhost kernel: [11193617.447539]  [<ffffffff811599aa>] core_sys_select+0x18a/0x2c0
Dec 21 10:48:39 localhost kernel: [11193617.447542]  [<ffffffff810539f3>] ? __wake_up+0x53/0x70
Dec 21 10:48:39 localhost kernel: [11193617.447545]  [<ffffffff81338c7e>] ? tty_ldisc_deref+0xe/0x10
Dec 21 10:48:39 localhost kernel: [11193617.447547]  [<ffffffff81331d3d>] ? tty_ioctl+0xfd/0x7b0
Dec 21 10:48:39 localhost kernel: [11193617.447550]  [<ffffffff810539f3>] ? __wake_up+0x53/0x70
Dec 21 10:48:39 localhost kernel: [11193617.447553]  [<ffffffff81338b7b>] ? put_ldisc+0x5b/0xc0
Dec 21 10:48:39 localhost kernel: [11193617.447555]  [<ffffffff81157442>] ? vfs_ioctl+0x22/0xa0
Dec 21 10:48:39 localhost kernel: [11193617.447558]  [<ffffffff81159d37>] sys_select+0x47/0x110
Dec 21 10:48:39 localhost kernel: [11193617.447560]  [<ffffffff811579f1>] ? sys_ioctl+0x81/0xa0
Dec 21 10:48:39 localhost kernel: [11193617.447565]  [<ffffffff81013172>] system_call_fastpath+0x16/0x1b
Dec 21 10:50:39 localhost kernel: [11193737.242293] sshd          D 00000000ffffffff     0 12162    955 0x00000000

---

