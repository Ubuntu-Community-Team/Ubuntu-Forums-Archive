---
title: "[BUG] general protection fault: 0000 [#1] SMP"
date: 2014-07-28
forum: General Help
---

### Post by hfamily15 on 2014-07-28
hi, I have big trouble with my VM. 

please help me.

When I executed a software build on VM, hang occurred with kernel panic.
Why did this Error occurred? 
I really have no Ideas! 

kern.log like this: 
Jul 29 09:34:19 kernel: [2038716.204021] [sched_delayed] sched: RT throttling activated
Jul 29 09:35:21 kernel: [2038778.039998] general protection fault: 0000 [#1] SMP
Jul 29 09:35:21 kernel: [2038778.040008] Modules linked in: arc4 md4 nls_utf8 cifs rfcomm bnep bluetooth parport_pc ppdev nfsd nfs_acl auth_rpcgss nfs fscache lockd sunrpc cirrus ttm drm_kms_helper drm psmouse joydev sysimgblt sysfillrect i2c_piix4 serio_raw syscopyarea virtio_balloon pvpanic mac_hid lp parport hid_generic usbhid hid floppy
Jul 29 09:35:21 kernel: [2038778.040046] task: ffff8814eb19aee0 ti: ffff88150d080000 task.ti: ffff88150d080000
Jul 29 09:35:21 kernel: [2038778.040046] RIP: 0010:[<ffffffff8119c316>]  [<ffffffff8119c316>] kmem_cache_alloc+0x66/0x150
Jul 29 09:35:21 lgescswpbld03v kernel: [2038778.040057] RSP: 0018:ffff88150d081d70  EFLAGS: 00010286
Jul 29 09:35:21 kernel: [2038778.040058] RAX: 0000000000000000 RBX: ffff881793eac650 RCX: 000000000057c98f
Jul 29 09:35:21 kernel: [2038778.040059] RDX: 000000000057c98e RSI: 00000000000000d0 RDI: 00000000000173c0
Jul 29 09:35:21 kernel: [2038778.040061] RBP: ffff88150d081dc0 R08: ffff8817bf3f73c0 R09: 0000000000000000
Jul 29 09:35:21 kernel: [2038778.040062] R10: 0000000000000000 R11: 0000000000017960 R12: ffff8817bec03800
Jul 29 09:35:21 kernel: [2038778.040062] R13: ffff00011576d200 R14: ffffffff8108f636 R15: 00000000000000d0
Jul 29 09:35:21 kernel: [2038778.040064] FS:  00002ac4076dfb40(0000) GS:ffff8817bf3e0000(0000) knlGS:0000000000000000
Jul 29 09:35:21 kernel: [2038778.040065] CS:  0010 DS: 0000 ES: 0000 CR0: 0000000080050033
Jul 29 09:35:21 kernel: [2038778.040066] CR2: 0000000000d54448 CR3: 0000000fb7e09000 CR4: 00000000001407e0
Jul 29 09:35:21 kernel: [2038778.040072] Stack:
Jul 29 09:35:21 kernel: [2038778.040074]  ffff88150d081dd0 ffffffff8119c2e1 00000001003000d0 ffffffff8101ca7e
Jul 29 09:35:21 kernel: [2038778.040078]  0000000000000340 ffff881793eac650 ffff8814eb19aee0 0000000001200011
Jul 29 09:35:21 kernel: [2038778.040081]  0000000000000000 00002ac4076dfe10 ffff88150d081de0 ffffffff8108f636
Jul 29 09:35:21 kernel: [2038778.040085] Call Trace:
Jul 29 09:35:21 kernel: [2038778.040090]  [<ffffffff8119c2e1>] ? kmem_cache_alloc+0x31/0x150
Jul 29 09:35:21 kernel: [2038778.040102]  [<ffffffff8101ca7e>] ? arch_dup_task_struct+0x4e/0x100
Jul 29 09:35:21 kernel: [2038778.040110]  [<ffffffff8108f636>] prepare_creds+0x26/0x1a0
Jul 29 09:35:21 kernel: [2038778.040112]  [<ffffffff8108fc26>] copy_creds+0x36/0x160
Jul 29 09:35:21 kernel: [2038778.040115]  [<ffffffff81062e03>] ? dup_task_struct+0x183/0x1e0
Jul 29 09:35:21 kernel: [2038778.040118]  [<ffffffff810636ef>] copy_process.part.24+0x13f/0xea0
Jul 29 09:35:21 kernel: [2038778.040125]  [<ffffffff812f0e16>] ? security_file_alloc+0x16/0x20


I have 2 VMs on Host machine like bellow:

Hostmachine
    &#9492;---------- VM01
    &#9492;---------- VM02

Hostmachine Spec : 
    # uname -a       Linux 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:13:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
    # processor       : 0 ~ 39
vendor_id       : GenuineIntel
cpu family      : 6
model           : 62
model name      : Intel(R) Xeon(R) CPU E5-2690 v2 @ 3.00GHz
stepping        : 4
microcode       : 0x416
cpu MHz         : 3001.000
cache size      : 25600 KB
physical id     : 1
siblings        : 20
core id         : 12
cpu cores       : 10
apicid          : 57
initial apicid  : 57
fpu             : yes
fpu_exception   : yes
cpuid level     : 13
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm pcid dca sse4_1 sse4_2 x2apic popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm ida arat epb xsaveopt pln pts dtherm tpr_shadow vnmi flexpriority ept vpid fsgsbase smep erms
bogomips        : 5999.84
clflush size    : 64
cache_alignment : 64
address sizes   : 46 bits physical, 48 bits virtual
power management:

VM Spec : 
# uname -a
Linux 3.11.0-15-generic #25~precise1-Ubuntu SMP Thu Jan 30 17:39:31 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux



please help me

---

