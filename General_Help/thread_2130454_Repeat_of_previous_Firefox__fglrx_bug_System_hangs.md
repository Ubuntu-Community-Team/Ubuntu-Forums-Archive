---
title: "Repeat of previous Firefox / fglrx bug? System hangs"
date: 2013-03-29
forum: General Help
---

### Post by Jay_E on 2013-03-29
Hi
One time in 10 starting firefox will hang system.

The symptoms look like those in
ttps://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/938981
but the logs ar different.

Question: Should I use launchpad and register abug? Or, is this a well-known problem?

Context:
I was running BOINC and opened a URL to a project website and the system hanged.
This happened If I also start firefox directly.

Ubuntu system:
I have had this problem on Ubuntu 12.10, and now raring 13.04

CPU hardware:
AMD FX(tm)-8150 Eight-Core Processor × 8 

Graphics:
Radeon HD 7750
VESA: VERDE

Graphic packages
I had the  raring release anf fglrx and had the problem.
Then, installed the update (Beta) version of the driver - and still have the problem.

# aptitude search fglrx | grep ^i
i   fglrx-amdcccle-updates          - Catalyst Control Center for the AMD graphi
i   fglrx-updates                   - Video driver for the AMD graphics accelera

BOINC gives a nice summary:
```

22-Mar-2013 19:04:08 [---] Starting BOINC client version 7.0.27 for x86_64-pc-linux-gnu
22-Mar-2013 19:04:08 [---] Libraries: libcurl/7.26.0 OpenSSL/1.0.1e zlib/1.2.7 libidn/1.25 libssh2/1.4.2 librtmp/2.3
22-Mar-2013 19:04:08 [---] Data directory: /var/lib/boinc-client
22-Mar-2013 19:04:08 [---] Processor: 8 AuthenticAMD AMD FX(tm)-8150 Eight-Core Processor [Family 21 Model 1 Stepping 2]
22-Mar-2013 19:04:08 [---] Processor: 2.00 MB cache
22-Mar-2013 19:04:08 [---] Processor features: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmx
ext fxsr_opt pdpe1gb rdtscp lm constant_tsc rep_good nopl nonstop_tsc extd_apicid aperfmperf pni pclmulqdq monitor ssse3 cx16 sse4_1 sse4_2 popcnt aes xsave avx l
ahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs xop skinit wdt lwp fma4 nodeid_msr topoext perfctr_core arat cpb hw_pstate n
pt lbrv svm_lock nrip_save tsc_scale vmcb_clean flushbyasid decodeassists pausefilter pfthreshold
22-Mar-2013 19:04:08 [---] OS: Linux: 3.2.0-4-amd64
22-Mar-2013 19:04:08 [---] Memory: 7.73 GB physical, 8.04 GB virtual
22-Mar-2013 19:04:08 [---] Disk: 18.33 GB total, 16.15 GB free
22-Mar-2013 19:04:08 [---] Local time is UTC -4 hours
22-Mar-2013 19:04:08 [---] ATI GPU 0: Capeverde (CAL version 1.4.1741, 2048MB, 1864MB available, 2048 GFLOPS peak)
22-Mar-2013 19:04:08 [---] OpenCL: ATI GPU 0: Capeverde (driver version CAL 1.4.1741 (VM), device version OpenCL 1.2 AMD-APP (938.2), 2048MB, 1864MB available)
22-Mar-2013 19:04:08 [---] Config: use all coprocessors

```

CPU was not 100% loaded. Had set BOINC to use 7 of 8 cores.

syslog  (The ASIC Hang looks suspicious to me.)
     [skipping most of startup..]
```

Mar 29 08:35:01 pc-14-large CRON[6599]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 29 08:43:59 pc-14-large kernel: [47688.853517] INFO: task Xorg:1211 blocked for more than 120 seconds.
Mar 29 08:43:59 pc-14-large kernel: [47688.853521] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Mar 29 08:43:59 pc-14-large kernel: [47688.853523] Xorg            D ffff88023ec13f40     0  1211   1185 0x00400004
Mar 29 08:43:59 pc-14-large kernel: [47688.853527]  ffff880230895c58 0000000000000086 ffff880231e82e80 ffff880230895fd8
Mar 29 08:43:59 pc-14-large kernel: [47688.853531]  ffff880230895fd8 ffff880230895fd8 ffff88020c7e2e80 ffff880231e82e80
Mar 29 08:43:59 pc-14-large kernel: [47688.853534]  7fffffffffffffff ffff880231e82e80 ffff88022f88c4e0 0000000000000002
Mar 29 08:43:59 pc-14-large kernel: [47688.853538] Call Trace:
Mar 29 08:43:59 pc-14-large kernel: [47688.853546]  [<ffffffff816c9579>] schedule+0x29/0x70
Mar 29 08:43:59 pc-14-large kernel: [47688.853550]  [<ffffffff816c7a2c>] schedule_timeout+0x1ec/0x2b0
Mar 29 08:43:59 pc-14-large kernel: [47688.853554]  [<ffffffff815b1a9f>] ? sock_aio_write+0x13f/0x160
Mar 29 08:43:59 pc-14-large kernel: [47688.853557]  [<ffffffff816c8813>] __down_common+0xa0/0xf7
Mar 29 08:43:59 pc-14-large kernel: [47688.853566]  [<ffffffff816c88dd>] __down+0x1d/0x1f
Mar 29 08:43:59 pc-14-large kernel: [47688.853569]  [<ffffffff81083701>] down+0x41/0x50
Mar 29 08:43:59 pc-14-large kernel: [47688.853623]  [<ffffffffa00cd54e>] KCL_SEMAPHORE_DownUninterruptible+0xe/0x10 [fglrx]
Mar 29 08:43:59 pc-14-large kernel: [47688.853660]  [<ffffffffa0107fca>] firegl_cmmqs_CWDDE_32+0x16a/0x480 [fglrx]
Mar 29 08:43:59 pc-14-large kernel: [47688.853698]  [<ffffffffa0106a0e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
Mar 29 08:43:59 pc-14-large kernel: [47688.853700]  [<ffffffff81065457>] ? capable+0x17/0x20
Mar 29 08:43:59 pc-14-large kernel: [47688.853737]  [<ffffffffa0106980>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
Mar 29 08:43:59 pc-14-large kernel: [47688.853770]  [<ffffffffa00dbb2d>] ? firegl_ioctl+0x1ed/0x250 [fglrx]
Mar 29 08:43:59 pc-14-large kernel: [47688.853800]  [<ffffffffa00cba6e>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
Mar 29 08:43:59 pc-14-large kernel: [47688.853803]  [<ffffffff811a5809>] ? do_vfs_ioctl+0x99/0x570
Mar 29 08:43:59 pc-14-large kernel: [47688.853806]  [<ffffffff8106bedb>] ? recalc_sigpending+0x1b/0x60
Mar 29 08:43:59 pc-14-large kernel: [47688.853809]  [<ffffffff8106c807>] ? __set_task_blocked+0x37/0x80
Mar 29 08:43:59 pc-14-large kernel: [47688.853811]  [<ffffffff811a5d71>] ? sys_ioctl+0x91/0xb0
Mar 29 08:43:59 pc-14-large kernel: [47688.853814]  [<ffffffff816cb769>] ? do_device_not_available+0x19/0x20
Mar 29 08:43:59 pc-14-large kernel: [47688.853817]  [<ffffffff816d2cdd>] ? system_call_fastpath+0x1a/0x1f
Mar 29 08:44:27 pc-14-large kernel: [47716.563353] <6>[fglrx] ASIC hang happened

Mar 29 08:44:27 pc-14-large kernel: [47716.563357] Pid: 6631, comm: firefox Tainted: PF          O 3.8.0-13-generic #23-Ubuntu
Mar 29 08:44:27 pc-14-large kernel: [47716.563358] Call Trace:
Mar 29 08:44:27 pc-14-large kernel: [47716.563406]  [<ffffffffa00d22ae>] KCL_DEBUG_OsDump+0xe/0x10 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.563445]  [<ffffffffa00e0d3c>] firegl_hardwareHangRecovery+0x1c/0x60 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.563501]  [<ffffffffa016d619>] ? _ZN4Asic9WaitUntil15ResetASICIfHungEv+0x9/0x10 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.563554]  [<ffffffffa016d5a3>] ? _ZN4Asic9WaitUntil15WaitForCompleteEv+0x93/0x100 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.563616]  [<ffffffffa019a61c>] ? _ZN8AsicR60012IO_QuietdownEv+0x2c/0x40 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.563675]  [<ffffffffa017dbed>] ? _ZN15ExecutableUnits10CPRingIdleE15idle_WaitMethod12_QS_CP_RING_+0x13d/0x1f0 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.563679]  [<ffffffff810926ff>] ? __dequeue_entity+0x2f/0x50
Mar 29 08:44:27 pc-14-large kernel: [47716.563715]  [<ffffffffa0102d62>] ? firegl_trace+0x72/0x1e0 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.563773]  [<ffffffffa017e59a>] ? _ZN21ExecutableUnitsCayman14AllCPRingsIdleE15idle_WaitMethod+0x1a/0x90 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.563831]  [<ffffffffa017da5b>] ? _ZN15ExecutableUnits7PM4idleE15idle_WaitMethod+0x4b/0x90 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.563885]  [<ffffffffa01735b1>] ? _ZN15QS_PRIVATE_CORE9QsPM4idleE15idle_WaitMethod+0x31/0x60 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.563938]  [<ffffffffa015a406>] ? _ZN10QS_PRIVATE16unRegisterClientEj+0x116/0x120 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.563942]  [<ffffffff8117d465>] ? __kmalloc+0x55/0x170
Mar 29 08:44:27 pc-14-large kernel: [47716.563994]  [<ffffffffa01677a9>] ? _Z8uCWDDEQCmjjPvjS_+0x3e9/0x1200 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.564031]  [<ffffffffa01081cf>] ? firegl_cmmqs_CWDDE_32+0x36f/0x480 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.564068]  [<ffffffffa0106a0e>] ? firegl_cmmqs_CWDDE32+0x8e/0x140 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.564070]  [<ffffffff81065457>] ? capable+0x17/0x20
Mar 29 08:44:27 pc-14-large kernel: [47716.564107]  [<ffffffffa0106980>] ? firegl_cmmqs_disabledriver+0x120/0x120 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.564139]  [<ffffffffa00dbb2d>] ? firegl_ioctl+0x1ed/0x250 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.564170]  [<ffffffffa00cba6e>] ? ip_firegl_unlocked_ioctl+0xe/0x20 [fglrx]
Mar 29 08:44:27 pc-14-large kernel: [47716.564172]  [<ffffffff811a5809>] ? do_vfs_ioctl+0x99/0x570
Mar 29 08:44:27 pc-14-large kernel: [47716.564175]  [<ffffffff81154045>] ? sys_madvise+0x2a5/0x740
Mar 29 08:44:27 pc-14-large kernel: [47716.564178]  [<ffffffff8107a13c>] ? task_work_run+0xac/0xe0
Mar 29 08:44:27 pc-14-large kernel: [47716.564181]  [<ffffffff811a5d71>] ? sys_ioctl+0x91/0xb0
Mar 29 08:44:27 pc-14-large kernel: [47716.564184]  [<ffffffff816d2cdd>] ? system_call_fastpath+0x1a/0x1f
Mar 29 08:44:27 pc-14-large kernel: [47716.564186] pubdev:0xffffffffa051bac0, num of device:1 , name:fglrx, major 9, minor 1. 
Mar 29 08:44:27 pc-14-large kernel: [47716.564188] device 0 : 0xffff8802325c8000 .
Mar 29 08:44:27 pc-14-large kernel: [47716.564190] Asic ID:0x683f, revision:0x29, MMIOReg:0xffffc90011200000.
Mar 29 08:44:27 pc-14-large kernel: [47716.564192] FB phys addr: 0xc0000000, MC :0xf400000000, Total FB size :0x80000000.
Mar 29 08:44:27 pc-14-large kernel: [47716.564194] gart table MC:0xf40f8fc000, Physical:0xcf8fc000, size:0x403000.
Mar 29 08:44:27 pc-14-large kernel: [47716.564195] mc_node :FB, total 1 zones
Mar 29 08:44:27 pc-14-large kernel: [47716.564197]     MC start:0xf400000000, Physical:0xc0000000, size:0xfd00000.
Mar 29 08:44:27 pc-14-large kernel: [47716.564199]     Mapped heap -- Offset:0x0, size:0xf8fc000, reference count:73, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564200]     Mapped heap -- Offset:0x0, size:0x1000000, reference count:1, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564202]     Mapped heap -- Offset:0xf8fc000, size:0x404000, reference count:1, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564203] mc_node :INV_FB, total 1 zones
Mar 29 08:44:27 pc-14-large kernel: [47716.564205]     MC start:0xf40fd00000, Physical:0xcfd00000, size:0x70300000.
Mar 29 08:44:27 pc-14-large kernel: [47716.564206]     Mapped heap -- Offset:0x702ee000, size:0x12000, reference count:1, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564208] mc_node :GART_USWC, total 3 zones
Mar 29 08:44:27 pc-14-large kernel: [47716.564209]     MC start:0xffa0100000, Physical:0x0, size:0x50000000.
Mar 29 08:44:27 pc-14-large kernel: [47716.564211]     Mapped heap -- Offset:0x2000000, size:0x800000, reference count:3, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564213]     Mapped heap -- Offset:0x0, size:0x2000000, reference count:29, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564214] mc_node :GART_CACHEABLE, total 3 zones
Mar 29 08:44:27 pc-14-large kernel: [47716.564216]     MC start:0xff70400000, Physical:0x0, size:0x2fd00000.
Mar 29 08:44:27 pc-14-large kernel: [47716.564217]     Mapped heap -- Offset:0x6d00000, size:0x700000, reference count:1, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564219]     Mapped heap -- Offset:0x6800000, size:0x500000, reference count:1, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564221]     Mapped heap -- Offset:0x5600000, size:0x500000, reference count:1, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564222]     Mapped heap -- Offset:0x5100000, size:0x500000, reference count:2, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564224]     Mapped heap -- Offset:0x6300000, size:0x500000, reference count:2, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564226]     Mapped heap -- Offset:0x5e00000, size:0x500000, reference count:2, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564227]     Mapped heap -- Offset:0x4d00000, size:0x400000, reference count:4, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564229]     Mapped heap -- Offset:0x4900000, size:0x400000, reference count:19, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564231]     Mapped heap -- Offset:0x4600000, size:0x300000, reference count:3, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564233]     Mapped heap -- Offset:0x3f00000, size:0x700000, reference count:11, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564234]     Mapped heap -- Offset:0x3800000, size:0x700000, reference count:3, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564236]     Mapped heap -- Offset:0x3100000, size:0x700000, reference count:3, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564238]     Mapped heap -- Offset:0x2a00000, size:0x700000, reference count:2, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564239]     Mapped heap -- Offset:0x2300000, size:0x700000, reference count:2, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564241]     Mapped heap -- Offset:0x1c00000, size:0x700000, reference count:20, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564243]     Mapped heap -- Offset:0x1500000, size:0x700000, reference count:5, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564244]     Mapped heap -- Offset:0xe00000, size:0x700000, reference count:3, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564246]     Mapped heap -- Offset:0x200000, size:0xc00000, reference count:6, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564247]     Mapped heap -- Offset:0x0, size:0x200000, reference count:26, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564249]     Mapped heap -- Offset:0xef000, size:0x11000, reference count:1, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564251]     Mapped heap -- Offset:0x0, size:0x9c1000, reference count:1, mapping count:0,
Mar 29 08:44:27 pc-14-large kernel: [47716.564252] mc_node :PEER_FB_GART, total 1 zones
Mar 29 08:44:27 pc-14-large kernel: [47716.564253]     MC start:0xfff0100000, Physical:0x0, size:0x1000.
Mar 29 08:44:27 pc-14-large kernel: [47716.564257] GRBM : 0xa0403028, SRBM : 0x200046c0 .
Mar 29 08:44:27 pc-14-large kernel: [47716.564260] CP_RB_BASE : 0xffa01000, CP_RB_RPTR : 0x3e230 , CP_RB_WPTR :0x3e230.
Mar 29 08:44:27 pc-14-large kernel: [47716.564263] CP_IB1_BUFSZ:0x0, CP_IB1_BASE_HI:0xff, CP_IB1_BASE_LO:0xa0937000.
Mar 29 08:44:27 pc-14-large kernel: [47716.564264] last submit IB buffer -- MC :0xffa0937000,phys:0x2307c7000.
Mar 29 08:44:27 pc-14-large kernel: [47716.564266] Dump the trace queue.
Mar 29 08:44:27 pc-14-large kernel: [47716.564267] End of dump

The log continues and this repeats - but without the ASIC hang

Mar 29 08:45:01 pc-14-large CRON[6659]: (root) CMD (command -v debian-sa1 > /dev/null && debian-sa1 1 1)
Mar 29 08:45:59 pc-14-large kernel: [47808.671597] INFO: task Xorg:1211 blocked for more than 120 seconds.
Mar 29 08:45:59 pc-14-large kernel: [47808.671601] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
Mar 29 08:45:59 pc-14-large kernel: [47808.671603] Xorg            D ffff88023ec13f40     0  1211   1185 0x00400004
Mar 29 08:45:59 pc-14-large kernel: [47808.671607]  ffff880230895c58 0000000000000086 ffff880231e82e80 ffff880230895fd8
Mar 29 08:45:59 pc-14-large kernel: [47808.671611]  ffff880230895fd8 ffff880230895fd8 ffff88020c7e2e80 ffff880231e82e80
Mar 29 08:45:59 pc-14-large kernel: [47808.671615]  7fffffffffffffff ffff880231e82e80 ffff88022f88c4e0 0000000000000002
Mar 29 08:45:59 pc-14-large kernel: [47808.671626] Call Trace:
Mar 29 08:45:59 pc-14-large kernel: [47808.671634]  [<ffffffff816c9579>] schedule+0x29/0x70

```

lspci sees video as:
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Cape Verde PRO [Radeon HD 7700 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cape Verde/Pitcairn HDMI Audio [Radeon HD 7700/7800 Series]

linux headers and image:
```

# aptitude search linux | grep ^i
i   libselinux1                     - SELinux runtime shared libraries          
i A libselinux1:i386                - SELinux runtime shared libraries          
i   linux-firmware                  - Firmware for Linux kernel drivers         
i   linux-headers-3.8.0-13          - Header files related to Linux kernel versi
i   linux-headers-3.8.0-13-generic  - Linux kernel headers for version 3.8.0 on 
i A linux-headers-3.8.0-14          - Header files related to Linux kernel versi
i A linux-headers-3.8.0-14-generic  - Linux kernel headers for version 3.8.0 on 
i   linux-headers-generic           - Generic Linux kernel headers              
i   linux-image-3.8.0-13-generic    - Linux kernel image for version 3.8.0 on 64
i   linux-image-extra-3.8.0-13-gene - Linux kernel image for version 3.8.0 on 64
i   linux-libc-dev                  - Linux Kernel Headers for development      

```

Need more info?

Thanks in advance,
Jay

---

