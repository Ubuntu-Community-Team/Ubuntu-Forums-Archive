---
title: "AppArmor Error When Upgrading Firmware from Version 77 to 371"
date: 2023-11-02
forum: General Help
---

### Post by lofiwk on 2023-11-02
[SIZE=4][FONT=arial]Just finished upgrading to 23.10, I encountered an 'AppArmor' error while upgrading firmware from version 77 to 371. Need help resolving this security-related issue.

[/FONT][/SIZE]```
 [SIZE=4][FONT=arial]Error:
XFailed to install firmware!org.freedesktop.DBus.Error.AccessDenied: An AppArmor policy prevents this sender from sending this message to this recipient; type="method_call", sender=":1.106" (uid=1000 pid=6412comm="/snap/firmware-updater/109/bin/firmware-updater --" label="snap.firmware-updater.firmware-updater-app (enforce)") interface="org.gnome.SessionManager" member="Reboot" error name="(unset)" requested_reply="0" destination="org.gnome.SessionManager" (uid=1000 pid=2848comm="/usr/libexec/gnome-session-binary-systemd-servic"label="unconfined")Close[/FONT][/SIZE]
```

&#8203;```
[SIZE=4][FONT=arial]
Additional information:
[/FONT][/SIZE][SIZE=4][FONT=arial]No LSB modules are available.[/FONT][/SIZE]
[SIZE=4][FONT=arial]Distributor ID:    Ubuntu[/FONT][/SIZE]
[SIZE=4][FONT=arial]Description:    Ubuntu 23.10[/FONT][/SIZE]
[SIZE=4][FONT=arial]Release:    23.10[/FONT][/SIZE]
[SIZE=4][FONT=arial]Codename:    mantic[/FONT][/SIZE]

```[SIZE=4][FONT=arial]
[/FONT][/SIZE]
&#8203;```

[SIZE=4][FONT=arial]Notebook: MSI Stealth 15M A11UEK
Architecture:            x86_64[/FONT][/SIZE]
[SIZE=4][FONT=arial]  CPU op-mode(s):        32-bit, 64-bit[/FONT][/SIZE]
[SIZE=4][FONT=arial]  Address sizes:         39 bits physical, 48 bits virtual[/FONT][/SIZE]
[SIZE=4][FONT=arial]  Byte Order:            Little Endian[/FONT][/SIZE]
[SIZE=4][FONT=arial]CPU(s):                  8[/FONT][/SIZE]
[SIZE=4][FONT=arial]  On-line CPU(s) list:   0-7[/FONT][/SIZE]
[SIZE=4][FONT=arial]Vendor ID:               GenuineIntel[/FONT][/SIZE]
[SIZE=4][FONT=arial]  Model name:            11th Gen Intel(R) Core(TM) i7-11375H @ 3.30GHz[/FONT][/SIZE]
[SIZE=4][FONT=arial]    CPU family:          6[/FONT][/SIZE]
[SIZE=4][FONT=arial]    Model:               140[/FONT][/SIZE]
[SIZE=4][FONT=arial]    Thread(s) per core:  2[/FONT][/SIZE]
[SIZE=4][FONT=arial]    Core(s) per socket:  4[/FONT][/SIZE]
[SIZE=4][FONT=arial]    Socket(s):           1[/FONT][/SIZE]
[SIZE=4][FONT=arial]    Stepping:            1[/FONT][/SIZE]
[SIZE=4][FONT=arial]    CPU(s) scaling MHz:  63%[/FONT][/SIZE]
[SIZE=4][FONT=arial]    CPU max MHz:         5000.0000[/FONT][/SIZE]
[SIZE=4][FONT=arial]    CPU min MHz:         400.0000[/FONT][/SIZE]
[SIZE=4][FONT=arial]    BogoMIPS:            6604.80[/FONT][/SIZE]
[SIZE=4][FONT=arial]    Flags:               fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mc[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         a cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss [/FONT][/SIZE]
[SIZE=4][FONT=arial]                         ht tm pbe syscall nx pdpe1gb rdtscp lm constant_tsc art[/FONT][/SIZE]
[SIZE=4][FONT=arial]                          arch_perfmon pebs bts rep_good nopl xtopology nonstop_[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes6[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         4 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr p[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         dcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         _timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefe[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         tch cpuid_fault epb cat_l2 invpcid_single cdp_l2 ssbd i[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         brs ibpb stibp ibrs_enhanced tpr_shadow flexpriority ep[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         t vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 e[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         rms invpcid rdt_a avx512f avx512dq rdseed adx smap avx5[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         12ifma clflushopt clwb intel_pt avx512cd sha_ni avx512b[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         w avx512vl xsaveopt xsavec xgetbv1 xsaves split_lock_de[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         tect dtherm ida arat pln pts hwp hwp_notify hwp_act_win[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         dow hwp_epp hwp_pkg_req vnmi avx512vbmi umip pku ospke [/FONT][/SIZE]
[SIZE=4][FONT=arial]                         avx512_vbmi2 gfni vaes vpclmulqdq avx512_vnni avx512_bi[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         talg avx512_vpopcntdq rdpid movdiri movdir64b fsrm avx5[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         12_vp2intersect md_clear ibt flush_l1d arch_capabilitie[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         s
[/FONT][/SIZE]
```
```

[SIZE=4][FONT=arial]Virtualization features: [/FONT][/SIZE]
[SIZE=4][FONT=arial]  Virtualization:        VT-x[/FONT][/SIZE]
[SIZE=4][FONT=arial]Caches (sum of all):     [/FONT][/SIZE]
[SIZE=4][FONT=arial]  L1d:                   192 KiB (4 instances)[/FONT][/SIZE]
[SIZE=4][FONT=arial]  L1i:                   128 KiB (4 instances)[/FONT][/SIZE]
[SIZE=4][FONT=arial]  L2:                    5 MiB (4 instances)[/FONT][/SIZE]
[SIZE=4][FONT=arial]  L3:                    12 MiB (1 instance)[/FONT][/SIZE]
[SIZE=4][FONT=arial]NUMA:                    [/FONT][/SIZE]
[SIZE=4][FONT=arial]  NUMA node(s):          1[/FONT][/SIZE]
[SIZE=4][FONT=arial]  NUMA node0 CPU(s):     0-7[/FONT][/SIZE]
[SIZE=4][FONT=arial]Vulnerabilities:         [/FONT][/SIZE]
[SIZE=4][FONT=arial]  Gather data sampling:  Mitigation; Microcode[/FONT][/SIZE]
[SIZE=4][FONT=arial]  Itlb multihit:         Not affected[/FONT][/SIZE]
[SIZE=4][FONT=arial]  L1tf:                  Not affected[/FONT][/SIZE]
[SIZE=4][FONT=arial]  Mds:                   Not affected[/FONT][/SIZE]
[SIZE=4][FONT=arial]  Meltdown:              Not affected[/FONT][/SIZE]
[SIZE=4][FONT=arial]  Mmio stale data:       Not affected[/FONT][/SIZE]
[SIZE=4][FONT=arial]  Retbleed:              Not affected[/FONT][/SIZE]
[SIZE=4][FONT=arial]  Spec rstack overflow:  Not affected[/FONT][/SIZE]
[SIZE=4][FONT=arial]  Spec store bypass:     Mitigation; Speculative Store Bypass disabled via prctl[/FONT][/SIZE]
[SIZE=4][FONT=arial]  Spectre v1:            Mitigation; usercopy/swapgs barriers and __user pointer[/FONT][/SIZE]
[SIZE=4][FONT=arial]                          sanitization[/FONT][/SIZE]
[SIZE=4][FONT=arial]  Spectre v2:            Mitigation; Enhanced / Automatic IBRS, IBPB conditional[/FONT][/SIZE]
[SIZE=4][FONT=arial]                         , RSB filling, PBRSB-eIBRS SW sequence[/FONT][/SIZE]
[SIZE=4][FONT=arial]  Srbds:                 Not affected[/FONT][/SIZE]
[SIZE=4][FONT=arial]  Tsx async abort:       Not affected
[/FONT][/SIZE]&#8203;
```

---

### Post by MAFoElffen on 2023-11-02
First, please go to the Code Tags link in my post, so that you can edit your last post to enclose your output within CODE Tags...

 I noticed thiserror while dev testing Noble. I did update it > Got that error > Rebooted and checked again... Even though it said it errored. ti did update mine anyways. LOL

You might want to reboot and check if yours updated.

---

### Post by lofiwk on 2023-11-03
I apologize for the issue with the font.  I'm new here. The problem was caused by UEFI secure boot being enabled, which prevented the firmware from updating properly. I disabled it for other reasons prior to initiating the firmware update and now it checked out.  Thanks.

---

### Post by MAFoElffen on 2023-11-03
From the "Posting Guidelines" ink in my signature line > "When asking for Technical Support" > #3
> 
When posting long outputs from terminal commands or from certain scripts, or the contents of configuration files, wrap this between[noparse]```
 and 
```[/noparse] tags. This is to preserve essential formatting and to prevent the posting of large difficult-to-read walls of text.

What they didn't explain in that, is that posting commands and raw output sometimes does weird things to the Forum's system software, so added pressure on that policy.

I asked you to refer to the "CODE Tags" link in my signature line, so you would learn how to use those tags to edit your post and fix the format of that...

Just trying to keep you out of trouble.

If fixed now, please go to the "Thread Tools" link in the upper right of this page, and mark your thread as "Solved".

---

