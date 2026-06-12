---
title: "[ubuntu server 14.04.3] kern.log and syslog growing huge!"
date: 2015-10-15
forum: General Help
---

### Post by michel20 on 2015-10-15
kern.log
```
Oct 15 02:06:28 dtc01 kernel: [98560.068703] WARNING: CPU: 8 PID: 80924 at /build/linux-zonD8D/linux-3.13.0/net/core/dst.c:285 dst_release+0x45/0x60()Oct 15 02:06:28 dtc01 kernel: [98560.068705] Modules linked in: ocfs2 quota_tree ocfs2_dlmfs ocfs2_stack_o2cb ocfs2_dlm ocfs2_nodemanager ocfs2_stackglue configfs drbd lru_cache libcrc32c x86_pkg_temp_thermal intel_powerclamp ipmi_devintf coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel gpio_ich aes_x86_64 lrw gf128mul glue_helper dcdbas ablk_helper cryptd ipmi_si wmi mei_me acpi_power_meter shpchp mei lpc_ich mac_hid lp parport tg3 ptp ahci pps_core libahci megaraid_sas
Oct 15 02:06:28 dtc01 kernel: [98560.068743] CPU: 8 PID: 80924 Comm: postgres Tainted: G        W     3.13.0-65-generic #106-Ubuntu
Oct 15 02:06:28 dtc01 kernel: [98560.068745] Hardware name: Dell Inc. PowerEdge R530/0HFG24, BIOS 1.2.6 06/08/2015
Oct 15 02:06:28 dtc01 kernel: [98560.068747]  0000000000000009 ffff880493ba1b18 ffffffff81723f80 0000000000000000
Oct 15 02:06:28 dtc01 kernel: [98560.068751]  ffff880493ba1b50 ffffffff8106785d ffff880465449500 00000000ffffffff
Oct 15 02:06:28 dtc01 kernel: [98560.068754]  ffff88045e040000 0000000000000000 0000000000000000 ffff880493ba1b60
Oct 15 02:06:28 dtc01 kernel: [98560.068757] Call Trace:
Oct 15 02:06:28 dtc01 kernel: [98560.068764]  [<ffffffff81723f80>] dump_stack+0x45/0x56
Oct 15 02:06:28 dtc01 kernel: [98560.068769]  [<ffffffff8106785d>] warn_slowpath_common+0x7d/0xa0
Oct 15 02:06:28 dtc01 kernel: [98560.068772]  [<ffffffff8106793a>] warn_slowpath_null+0x1a/0x20
Oct 15 02:06:28 dtc01 kernel: [98560.068774]  [<ffffffff816302b5>] dst_release+0x45/0x60
Oct 15 02:06:28 dtc01 kernel: [98560.068778]  [<ffffffff81610e89>] sk_dst_check+0xb9/0xe0
Oct 15 02:06:28 dtc01 kernel: [98560.068783]  [<ffffffff816c3fdf>] ip6_sk_dst_lookup_flow+0x2f/0x1b0
Oct 15 02:06:28 dtc01 kernel: [98560.068788]  [<ffffffff816deffe>] udpv6_sendmsg+0x61e/0xb10
Oct 15 02:06:28 dtc01 kernel: [98560.068794]  [<ffffffff810498ae>] ? physflat_send_IPI_mask+0xe/0x10
Oct 15 02:06:28 dtc01 kernel: [98560.068800]  [<ffffffff8109ab6a>] ? try_to_wake_up+0x1fa/0x2c0
Oct 15 02:06:28 dtc01 kernel: [98560.068806]  [<ffffffff81696324>] inet_sendmsg+0x64/0xb0
Oct 15 02:06:28 dtc01 kernel: [98560.068811]  [<ffffffff81314c07>] ? apparmor_socket_sendmsg+0x17/0x20
Oct 15 02:06:28 dtc01 kernel: [98560.068814]  [<ffffffff8160e9db>] sock_sendmsg+0x8b/0xc0
Oct 15 02:06:28 dtc01 kernel: [98560.068817]  [<ffffffff8160ef21>] SYSC_sendto+0x121/0x1c0
Oct 15 02:06:28 dtc01 kernel: [98560.068854]  [<ffffffffa0315048>] ? ocfs2_sync_file+0x118/0x220 [ocfs2]
Oct 15 02:06:28 dtc01 kernel: [98560.068857]  [<ffffffff8160f90e>] SyS_sendto+0xe/0x10
Oct 15 02:06:28 dtc01 kernel: [98560.068861]  [<ffffffff81734b5d>] system_call_fastpath+0x1a/0x1f
Oct 15 02:06:28 dtc01 kernel: [98560.068862] ---[ end trace d1c5e42a12492e8b ]---
```

syslog:
```
Oct 15 06:29:43 dtc01 kernel: [114367.335087] ------------[ cut here ]------------Oct 15 06:29:43 dtc01 kernel: [114367.335090] WARNING: CPU: 4 PID: 81091 at /build/linux-zonD8D/linux-3.13.0/net/core/dst.c:285 dst_release+0x45/0x60()
Oct 15 06:29:43 dtc01 kernel: [114367.335091] Modules linked in: ocfs2 quota_tree ocfs2_dlmfs ocfs2_stack_o2cb ocfs2_dlm ocfs2_nodemanager ocfs2_stackglue configfs drbd lru_cache libcrc32c x86_pkg_temp_thermal intel_powerclamp ipmi_devintf coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel gpio_ich aes_x86_64 lrw gf128mul glue_helper dcdbas ablk_helper cryptd ipmi_si wmi mei_me acpi_power_meter shpchp mei lpc_ich mac_hid lp parport tg3 ptp ahci pps_core libahci megaraid_sas
Oct 15 06:29:43 dtc01 kernel: [114367.335110] CPU: 4 PID: 81091 Comm: postgres Tainted: G        W     3.13.0-65-generic #106-Ubuntu
Oct 15 06:29:43 dtc01 kernel: [114367.335111] Hardware name: Dell Inc. PowerEdge R530/0HFG24, BIOS 1.2.6 06/08/2015
Oct 15 06:29:43 dtc01 kernel: [114367.335112]  0000000000000009 ffff88049d037b18 ffffffff81723f80 0000000000000000
Oct 15 06:29:43 dtc01 kernel: [114367.335115]  ffff88049d037b50 ffffffff8106785d ffff880465449500 00000000fffffffd
Oct 15 06:29:43 dtc01 kernel: [114367.335118]  ffff88045e040000 0000000000000000 0000000000000000 ffff88049d037b60
Oct 15 06:29:43 dtc01 kernel: [114367.335121] Call Trace:
Oct 15 06:29:43 dtc01 kernel: [114367.335124]  [<ffffffff81723f80>] dump_stack+0x45/0x56
Oct 15 06:29:43 dtc01 kernel: [114367.335126]  [<ffffffff8106785d>] warn_slowpath_common+0x7d/0xa0
Oct 15 06:29:43 dtc01 kernel: [114367.335128]  [<ffffffff8106793a>] warn_slowpath_null+0x1a/0x20
Oct 15 06:29:43 dtc01 kernel: [114367.335131]  [<ffffffff816302b5>] dst_release+0x45/0x60
Oct 15 06:29:43 dtc01 kernel: [114367.335134]  [<ffffffff81610e81>] sk_dst_check+0xb1/0xe0
Oct 15 06:29:43 dtc01 kernel: [114367.335137]  [<ffffffff816c3fdf>] ip6_sk_dst_lookup_flow+0x2f/0x1b0
Oct 15 06:29:43 dtc01 kernel: [114367.335140]  [<ffffffff81613728>] ? release_sock+0x118/0x170
Oct 15 06:29:43 dtc01 kernel: [114367.335143]  [<ffffffff816deffe>] udpv6_sendmsg+0x61e/0xb10
Oct 15 06:29:43 dtc01 kernel: [114367.335146]  [<ffffffff811a8d07>] ? migrate_pages+0x397/0x780
Oct 15 06:29:43 dtc01 kernel: [114367.335149]  [<ffffffff81696324>] inet_sendmsg+0x64/0xb0
Oct 15 06:29:43 dtc01 kernel: [114367.335153]  [<ffffffff81314c07>] ? apparmor_socket_sendmsg+0x17/0x20
Oct 15 06:29:43 dtc01 kernel: [114367.335155]  [<ffffffff8160e9db>] sock_sendmsg+0x8b/0xc0
Oct 15 06:29:43 dtc01 kernel: [114367.335158]  [<ffffffff81157ee3>] ? free_pages+0x13/0x20
Oct 15 06:29:43 dtc01 kernel: [114367.335161]  [<ffffffff81730134>] ? __do_page_fault+0x204/0x570
Oct 15 06:29:43 dtc01 kernel: [114367.335163]  [<ffffffff8160ef21>] SYSC_sendto+0x121/0x1c0
Oct 15 06:29:43 dtc01 kernel: [114367.335166]  [<ffffffff81727f11>] ? __schedule+0x381/0x7d0
Oct 15 06:29:43 dtc01 kernel: [114367.335169]  [<ffffffff8160f90e>] SyS_sendto+0xe/0x10
Oct 15 06:29:43 dtc01 kernel: [114367.335171]  [<ffffffff81734b5d>] system_call_fastpath+0x1a/0x1f
Oct 15 06:29:43 dtc01 kernel: [114367.335173] ---[ end trace d1c5e42a128fffdb ]---
Oct 15 06:29:43 dtc01 kernel: [114367.335174] ------------[ cut here ]------------
```

**1 day of log ( log rotate ok ):**
```
-rw-r----- 1 syslog adm  23G Out 15 08:27 kern.log
-rw-r----- 1 syslog adm 7,2G Out 15 09:02 syslog

```


My configuration:

[B]Dell Poweredge R530
Intel(R) Xeon(R) CPU E5-2609 v3 @ 1.90GHz[/B]
[B]32G
[/B]
**Ubuntu 14.04.3**
[B]PostgreSQL 9.4.5
RAID10 ( SAS 10k )
[/B]**Drbd 8.4.4**


```
cat /proc/cpuinfo
processor    : 11vendor_id    : GenuineIntel
cpu family    : 6
model        : 63
model name    : Intel(R) Xeon(R) CPU E5-2609 v3 @ 1.90GHz
stepping    : 2
microcode    : 0x31
cpu MHz        : 1897.912
cache size    : 15360 KB
physical id    : 1
siblings    : 6
core id        : 5
cpu cores    : 6
apicid        : 26
initial apicid    : 26
fpu        : yes
fpu_exception    : yes
cpuid level    : 15
wp        : yes
flags        : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf eagerfpu pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 fma cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid
bogomips    : 3796.97
clflush size    : 64
cache_alignment    : 64
address sizes    : 46 bits physical, 48 bits virtual
power management:
```


```
cat /proc/meminfo
MemTotal:       32704472 kB
MemFree:        16145988 kB
Buffers:          102420 kB
Cached:         12457880 kB
SwapCached:            0 kB
Active:          7900928 kB
Inactive:        8058144 kB
Active(anon):    6981012 kB
Inactive(anon):   558512 kB
Active(file):     919916 kB
Inactive(file):  7499632 kB
Unevictable:           0 kB
Mlocked:               0 kB
SwapTotal:      39062524 kB
SwapFree:       39062524 kB
Dirty:               400 kB
Writeback:             0 kB
AnonPages:       3398704 kB
Mapped:          1726724 kB
Shmem:           4140756 kB
Slab:             209316 kB
SReclaimable:     116000 kB
SUnreclaim:        93316 kB
KernelStack:        5936 kB
PageTables:        47080 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:    55414760 kB
Committed_AS:   18272468 kB
VmallocTotal:   34359738367 kB
VmallocUsed:      351236 kB
VmallocChunk:   34342622892 kB
HardwareCorrupted:     0 kB
AnonHugePages:   2908160 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:       93868 kB
DirectMap2M:     3870720 kB
DirectMap1G:    31457280 kB
```

```
cat /proc/drbd
version: 8.4.3 (api:1/proto:86-101)
srcversion: 6551AD2C98F533733BE558C


 1: cs:Connected ro:Primary/Secondary ds:UpToDate/UpToDate C r-----
    ns:5789290 nr:0 dw:5789282 dr:5504610 al:2123 bm:0 lo:3 pe:2 ua:0 ap:3 ep:1 wo:f oos:0
```


```
uptime
 09:15:56 up 52 min,  8 users,  load average: 4,79, 3,49, 3,07
```

---

### Post by tgalati4 on 2015-10-15
Welcome to the forums.  Those are large log files.  Your BIOS is dated 06/08/15 and 14.04 came out in April 2014.  I would make a 15.10 DVD and boot from that.  Then go through your syslog.

You are showing CPU: 8, but your /proc/cpuinfo shows a 6-core CPU.

It appears to be a *postgres* error.  Turn off *postgres*, rename the error logs, and collect log files for a day at idle.  Then examine and post any errors.

---

### Post by michel20 on 2015-10-19
Thanks.

Ubuntu 14.04.3 is LTS ( Long Time Support ) and the BIOS is updated.

After i stopped postgresql:
```
Oct 19 09:49:27 dtc01 kernel: [347457.448396] ------------[ cut here ]------------Oct 19 09:49:27 dtc01 kernel: [347457.448399] WARNING: CPU: 6 PID: 129533 at /build/linux-zonD8D/linux-3.13.0/net/core/dst.c:285 dst_release+0x45/0x60()
Oct 19 09:49:27 dtc01 kernel: [347457.448400] Modules linked in: ocfs2 quota_tree ocfs2_dlmfs ocfs2_stack_o2cb ocfs2_dlm ocfs2_nodemanager ocfs2_stackglue configfs drbd lru_cache libcrc32c x86_pkg_temp_thermal intel_powerclamp coretemp kvm_intel kvm crct10dif_pclmul crc32_pclmul ghash_clmulni_intel aesni_intel ipmi_devintf aes_x86_64 lrw gpio_ich dcdbas gf128mul glue_helper ablk_helper cryptd ipmi_si mei_me acpi_power_meter wmi mei lpc_ich shpchp mac_hid lp parport tg3 ptp ahci pps_core libahci megaraid_sas
Oct 19 09:49:27 dtc01 kernel: [347457.448420] CPU: 6 PID: 129533 Comm: apache2 Tainted: G        W     3.13.0-65-generic #106-Ubuntu
Oct 19 09:49:27 dtc01 kernel: [347457.448421] Hardware name: Dell Inc. PowerEdge R530/0HFG24, BIOS 1.2.6 06/08/2015
Oct 19 09:49:27 dtc01 kernel: [347457.448422]  0000000000000009 ffff8803ec7d3d40 ffffffff81723f80 0000000000000000
Oct 19 09:49:27 dtc01 kernel: [347457.448425]  ffff8803ec7d3d78 ffffffff8106785d ffff8804652c6100 00000000fffffffd
Oct 19 09:49:27 dtc01 kernel: [347457.448428]  0000000000000007 ffff88084d8ea750 ffff8808691dc7a0 ffff8803ec7d3d88
Oct 19 09:49:27 dtc01 kernel: [347457.448430] Call Trace:
Oct 19 09:49:27 dtc01 kernel: [347457.448433]  [<ffffffff81723f80>] dump_stack+0x45/0x56
Oct 19 09:49:27 dtc01 kernel: [347457.448436]  [<ffffffff8106785d>] warn_slowpath_common+0x7d/0xa0
Oct 19 09:49:27 dtc01 kernel: [347457.448438]  [<ffffffff8106793a>] warn_slowpath_null+0x1a/0x20
Oct 19 09:49:27 dtc01 kernel: [347457.448441]  [<ffffffff816302b5>] dst_release+0x45/0x60
Oct 19 09:49:27 dtc01 kernel: [347457.448445]  [<ffffffff81696215>] inet_sock_destruct+0x135/0x1e0
Oct 19 09:49:27 dtc01 kernel: [347457.448448]  [<ffffffff81612a3f>] __sk_free+0x1f/0x180
Oct 19 09:49:27 dtc01 kernel: [347457.448451]  [<ffffffff81612bb9>] sk_free+0x19/0x20
Oct 19 09:49:27 dtc01 kernel: [347457.448453]  [<ffffffff8166f190>] tcp_close+0x150/0x410
Oct 19 09:49:27 dtc01 kernel: [347457.448456]  [<ffffffff81694de7>] inet_release+0x77/0x80
Oct 19 09:49:27 dtc01 kernel: [347457.448459]  [<ffffffff816c1bc0>] inet6_release+0x30/0x40
Oct 19 09:49:27 dtc01 kernel: [347457.448461]  [<ffffffff8160da7f>] sock_release+0x1f/0x80
Oct 19 09:49:27 dtc01 kernel: [347457.448463]  [<ffffffff8160daf2>] sock_close+0x12/0x20
Oct 19 09:49:27 dtc01 kernel: [347457.448467]  [<ffffffff811bff94>] __fput+0xe4/0x260
Oct 19 09:49:27 dtc01 kernel: [347457.448470]  [<ffffffff811c015e>] ____fput+0xe/0x10
Oct 19 09:49:27 dtc01 kernel: [347457.448473]  [<ffffffff81088557>] task_work_run+0xa7/0xe0
Oct 19 09:49:27 dtc01 kernel: [347457.448477]  [<ffffffff81013ed7>] do_notify_resume+0x97/0xb0
Oct 19 09:49:27 dtc01 kernel: [347457.448480]  [<ffffffff81734e1a>] int_signal+0x12/0x17
Oct 19 09:49:27 dtc01 kernel: [347457.448481] ---[ end trace 7721844c9a12a1bc ]---
Oct 19 09:49:27 dtc01 kernel: [347457.448482] ------------[ cut here ]------------
```

---

### Post by tgalati4 on 2015-10-19
Now *apache* is causing the error.  Turn off your web server and watch the logs.  Disconnect your ethernet cable.  This looks like a kernel issue with the BIOS update.  Was this setup working before and now is not working?

---

### Post by michel20 on 2015-10-22
If i turn off postgresql and apache the error stopped but i need this to work. What can fix it?

---

### Post by tgalati4 on 2015-10-22
The error messages have an inet6 reference.  Perhaps turn off IP6 addressing and use only IP4 addressing.  

[http://askubuntu.com/questions/440649/how-to-disable-ipv6-in-ubuntu-14-04](http://askubuntu.com/questions/440649/how-to-disable-ipv6-in-ubuntu-14-04)

Reboot and check the logs.

---

### Post by Doug S on 2015-10-22
Isn't it a tained kernel? And isn't the problem, potentially, somewhere in the non-standard core/dst.c?

Myself, I think an easier way to disable ipv6 is to do it via the /etc/default/grub GRUB_CMDLINE_LINUX_DEFAULT. Example (with other stuff from mine):```
GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 net.ifnames=1 biosdevname=0"
```

---

### Post by tgalati4 on 2015-10-22
Well, if you look at the[ source code]("http://lxr.free-electrons.com/source/net/core/dst.c?v=3.13"), there are several places that can lead to a race condition.  It's possible that a binary blob is causing this.  These forums are not an efficient way to troubleshoot a stack dump.  Could be a bad network card.

---

### Post by Doug S on 2015-10-22
I'm just saying that if the kernel is [tained]("http://unix.stackexchange.com/questions/118116/linux-what-is-a-tainted-kernel"), we shouldn't waste any time on this. However , if the problem can be reproduced with an untained kernel, then it is time to try to help.

---

### Post by Yellow Pasque on 2015-10-23
Is it possible to try a newer kernel (or at least 3.16.x)?
[https://github.com/torvalds/linux/commit/f88649721268999bdff09777847080a52004f691](https://github.com/torvalds/linux/commit/f88649721268999bdff09777847080a52004f691)

> I'm just saying that if the kernel is tainted, we shouldn't waste any time on this
LOL. This isn't kernel bugzilla. You could at least tell the user how to limit the size of the logs. (I've been using systemd for a while now and I forget how that works in init/upstart.)

---

