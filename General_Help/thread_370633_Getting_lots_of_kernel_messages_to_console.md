---
title: "Getting lots of kernel messages to console"
date: 2007-02-25
forum: General Help
---

### Post by BrianK on 2007-02-25
I've installed Ubuntu 6.10 on a couple slightly older P4 machines (2.4 & 2.8 GHz) with nvidia graphics cards, if that matters.

I'm getting a lot of kernel messages spat out to the console.  Most recently it happened when I was tailing a log on an nfs share.  The garbage spat out looks like:

```
Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000] Oops: 0000 [#1]

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000] SMP

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000] CPU:    0

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000] EIP is at kmap_atomic+0x11/0x80

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000] eax: 00000000   ebx: 00000000   ecx: ed334000   edx: 00000003

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000] esi: 00000003   edi: 00000312   ebp: ed31b154   esp: ed335d7c

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000] Process tail (pid: 6228, threadinfo=ed334000 task=c21ed560)

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000] Stack: 00000677 00000cee f8ec7ca8 00000989 f7992500 00001000 ed31b154 f8ec8c42

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000]        00000004 c03707a8 00000206 00000046 ed31b200 00000000 00000000 c01e2560

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000]        00000001 c01e2dfa 00000000 00000000 ed31b200 f4bb2940 00000000 ed31b1fc

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000] Call Trace:

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000]  <f8ec7ca8> nfs_readpage_truncate_uninitialised_page+0xe8/0x130 [nfs]  <f8ec8c42> nfs_readpage+0x272/0x4f0 [nfs]

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000]  <c01e2560> radix_tree_node_alloc+0x10/0x60  <c01e2dfa> radix_tree_insert+0x1ca/0x210

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000]  <c014c698> do_generic_mapping_read+0x508/0x590  <c014d118> __generic_file_aio_read+0xf8/0x270

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000]  <c014b8a0> file_read_actor+0x0/0xf0  <f8ec1975> nfs_sync_mapping+0x55/0x70 [nfs]

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000]  <f8ec215e> nfs_revalidate_mapping+0x9e/0x160 [nfs]  <c014d2d5> generic_file_aio_read+0x45/0x60

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000]  <c016a4b4> do_sync_read+0xc4/0x100  <c0136180> autoremove_wake_function+0x0/0x50

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000]  <c017481e> sys_fstat64+0x1e/0x30  <c016af6c> vfs_read+0xbc/0x180

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000]  <c016a3f0> do_sync_read+0x0/0x100  <c016b4e1> sys_read+0x41/0x70

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000]  <c0102fbb> sysenter_past_esp+0x54/0x79

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000] Code: e0 05 03 05 00 ec 47 c0 c3 0f 0b 98 00 6b 30 2f c0 eb d4 8d b4 26 00 00 00 00 56 b9 00 e0 ff ff 53 89 c3 21 e1 83 41 14 01 89 d6 <8b> 00 c1 e8 1e 8b 14 85 84 a0 3e c0 8b 82 0c 06 00 00 05 80 13

Message from syslogd@aluminum at Sun Feb 25 20:32:22 2007 ...
aluminum kernel: [17291231.600000] EIP: [kmap_atomic+17/128] kmap_atomic+0x11/0x80 SS:ESP 0068:ed335d7c
```

This has happened while tailing a few times.  Other times it happens when scrubbing through images files off an nfs  share.  Don't know if it's related to nfs or what, but it's happened several times on more than one machine, but only after they were upgraded to 6.10.

---

### Post by sylvainm on 2007-03-07
Hello !
I have the same problem (running an nfs client withe a 2.6.17 kernel).
It seems that other ubuntu users have the same problem, especially this one :
[Ubuntu-kernel-2.6.17-bug]("https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/65827")

I solved my problem by recompiling my kernel (hey, dont run away, it easy !) following this howto :
[kernel_compilation_ubuntu]("http://www.howtoforge.com/kernel_compilation_ubuntu") from HowToForge
I used 2.6.18 kernel sources, so that the config file for the compilation is quite the same as the one of my 2.6.17-11 ubuntu kernel

Good luck !

sylvain

---

### Post by BrianK on 2007-04-09
As a followup, I went with sylvainm's suggestion & compiled a new kernel (something I'm vehemently against).  Well, it worked.  No more NFS bugs.  If you do it the way that's outlined on the page sylvainm links, the kernel sources are made into deb packages, so everything falls back into place nicely.  A quick recompile of nvidia drivers & I'm back up & running.  Took about 2.5 hours start to finish, which included a decent amount of time trimming unnecessaries out of the kernel config.

---

