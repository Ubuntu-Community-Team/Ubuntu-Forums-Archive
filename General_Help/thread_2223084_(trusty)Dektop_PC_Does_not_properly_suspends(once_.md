---
title: "(trusty)Dektop PC Does not properly suspends(once in five times on average)"
date: 2014-05-09
forum: General Help
---

### Post by azm1 on 2014-05-09
Hi, fresh install of Trusty does not properly suspend(sometimes) The disk turns off but the fans keep going and I have to force shutdown via holding the power button.

I tried to follow the link below and add the script to /etc/pm/sleep.d/20_custom-ehci_hcd 
but it looks line nothing has changed. Im not able to upload the whole crash report since it has over one MB.

Any help appreaciated.


[http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug](http://thecodecentral.com/2011/01/18/fix-ubuntu-10-10-suspendhibernate-not-working-bug)

```
ProblemType: KernelOopsAnnotation: This occured during a previous suspend and prevented it from resuming properly.
Architecture: amd64
Date: Fri May  9 15:01:57 2014
DistroRelease: Ubuntu 14.04
ExecutablePath: /usr/share/apport/apportcheckresume
ExecutableTimestamp: 1397576330
Failure: suspend/resume
InterpreterPath: /usr/bin/python3.4
Package: linux-image-3.13.0-24-generic
ProcCmdline: /usr/bin/python3 /usr/share/apport/apportcheckresume
ProcCwd: /
ProcEnviron:
 TERM=linux
 PATH=(custom, no user)
ProcMaps:
 00400000-00754000 r-xp 00000000 08:06 918493                             /usr/bin/python3.4
 00953000-00954000 r--p 00353000 08:06 918493                             /usr/bin/python3.4
 00954000-009e0000 rw-p 00354000 08:06 918493                             /usr/bin/python3.4
 009e0000-009fc000 rw-p 00000000 00:00 0 
 0245d000-02716000 rw-p 00000000 00:00 0                                  [heap]
 7fddc0158000-7fddc01d8000 rw-p 00000000 00:00 0 
 7fddc01d8000-7fddc01f9000 r-xp 00000000 08:06 397411                     /lib/x86_64-linux-gnu/liblzma.so.5.0.0
 7fddc01f9000-7fddc03f8000 ---p 00021000 08:06 397411                     /lib/x86_64-linux-gnu/liblzma.so.5.0.0
 7fddc03f8000-7fddc03f9000 r--p 00020000 08:06 397411                     /lib/x86_64-linux-gnu/liblzma.so.5.0.0
 7fddc03f9000-7fddc03fa000 rw-p 00021000 08:06 397411                     /lib/x86_64-linux-gnu/liblzma.so.5.0.0
 7fddc03fa000-7fddc0410000 r-xp 00000000 08:06 397391                     /lib/x86_64-linux-gnu/libgcc_s.so.1
 7fddc0410000-7fddc060f000 ---p 00016000 08:06 397391                     /lib/x86_64-linux-gnu/libgcc_s.so.1
 7fddc060f000-7fddc0610000 rw-p 00015000 08:06 397391                     /lib/x86_64-linux-gnu/libgcc_s.so.1
 7fddc0610000-7fddc06f6000 r-xp 00000000 08:06 928085                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.19
 7fddc06f6000-7fddc08f5000 ---p 000e6000 08:06 928085                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.19
 7fddc08f5000-7fddc08fd000 r--p 000e5000 08:06 928085                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.19
 7fddc08fd000-7fddc08ff000 rw-p 000ed000 08:06 928085                     /usr/lib/x86_64-linux-gnu/libstdc++.so.6.0.19
 7fddc08ff000-7fddc0914000 rw-p 00000000 00:00 0 
 7fddc0914000-7fddc0a58000 r-xp 00000000 08:06 927249                     /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0
 7fddc0a58000-7fddc0c58000 ---p 00144000 08:06 927249                     /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0
 7fddc0c58000-7fddc0c5c000 r--p 00144000 08:06 927249                     /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0
 7fddc0c5c000-7fddc0c5d000 rw-p 00148000 08:06 927249                     /usr/lib/x86_64-linux-gnu/libapt-pkg.so.4.12.0
 7fddc0c5d000-7fddc0c5e000 rw-p 00000000 00:00 0 
 7fddc0c5e000-7fddc0ca4000 r-xp 00000000 08:06 926080                     /usr/lib/python3/dist-packages/apt_pkg.cpython-34m-x86_64-linux-gnu.so
 7fddc0ca4000-7fddc0ea3000 ---p 00046000 08:06 926080                     /usr/lib/python3/dist-packages/apt_pkg.cpython-34m-x86_64-linux-gnu.so
 7fddc0ea3000-7fddc0ea5000 r--p 00045000 08:06 926080                     /usr/lib/python3/dist-packages/apt_pkg.cpython-34m-x86_64-linux-gnu.so
 7fddc0ea5000-7fddc0ead000 rw-p 00047000 08:06 926080                     /usr/lib/python3/dist-packages/apt_pkg.cpython-34m-x86_64-linux-gnu.so
 7fddc0ead000-7fddc0eed000 rw-p 00000000 00:00 0 
 7fddc0eed000-7fddc0f41000 r-xp 00000000 08:06 397379                     /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7fddc0f41000-7fddc1141000 ---p 00054000 08:06 397379                     /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7fddc1141000-7fddc1144000 r--p 00054000 08:06 397379                     /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7fddc1144000-7fddc114a000 rw-p 00057000 08:06 397379                     /lib/x86_64-linux-gnu/libssl.so.1.0.0
 7fddc114a000-7fddc114b000 rw-p 00000000 00:00 0 
 7fddc114b000-7fddc115e000 r-xp 00000000 08:06 1180212                    /usr/lib/python3.4/lib-dynload/_ssl.cpython-34m-x86_64-linux-gnu.so
 7fddc115e000-7fddc135d000 ---p 00013000 08:06 1180212                    /usr/lib/python3.4/lib-dynload/_ssl.cpython-34m-x86_64-linux-gnu.so
 7fddc135d000-7fddc135e000 r--p 00012000 08:06 1180212                    /usr/lib/python3.4/lib-dynload/_ssl.cpython-34m-x86_64-linux-gnu.so
 7fddc135e000-7fddc1362000 rw-p 00013000 08:06 1180212                    /usr/lib/python3.4/lib-dynload/_ssl.cpython-34m-x86_64-linux-gnu.so
 7fddc1362000-7fddc14e2000 rw-p 00000000 00:00 0 
 7fddc14e2000-7fddc1693000 r-xp 00000000 08:06 397324                     /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7fddc1693000-7fddc1892000 ---p 001b1000 08:06 397324                     /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7fddc1892000-7fddc18ad000 r--p 001b0000 08:06 397324                     /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7fddc18ad000-7fddc18b8000 rw-p 001cb000 08:06 397324                     /lib/x86_64-linux-gnu/libcrypto.so.1.0.0
 7fddc18b8000-7fddc18bc000 rw-p 00000000 00:00 0 
 7fddc18bc000-7fddc18c1000 r-xp 00000000 08:06 1180204                    /usr/lib/python3.4/lib-dynload/_hashlib.cpython-34m-x86_64-linux-gnu.so
 7fddc18c1000-7fddc1ac0000 ---p 00005000 08:06 1180204                    /usr/lib/python3.4/lib-dynload/_hashlib.cpython-34m-x86_64-linux-gnu.so
 7fddc1ac0000-7fddc1ac1000 r--p 00004000 08:06 1180204                    /usr/lib/python3.4/lib-dynload/_hashlib.cpython-34m-x86_64-linux-gnu.so
 7fddc1ac1000-7fddc1ac2000 rw-p 00005000 08:06 1180204                    /usr/lib/python3.4/lib-dynload/_hashlib.cpython-34m-x86_64-linux-gnu.so
 7fddc1ac2000-7fddc1b02000 rw-p 00000000 00:00 0 
 7fddc1b02000-7fddc1b11000 r-xp 00000000 08:06 397363                     /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7fddc1b11000-7fddc1d10000 ---p 0000f000 08:06 397363                     /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7fddc1d10000-7fddc1d11000 r--p 0000e000 08:06 397363                     /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7fddc1d11000-7fddc1d12000 rw-p 0000f000 08:06 397363                     /lib/x86_64-linux-gnu/libbz2.so.1.0.4
 7fddc1d12000-7fddc1d15000 r-xp 00000000 08:06 1180188                    /usr/lib/python3.4/lib-dynload/_bz2.cpython-34m-x86_64-linux-gnu.so
 7fddc1d15000-7fddc1f14000 ---p 00003000 08:06 1180188                    /usr/lib/python3.4/lib-dynload/_bz2.cpython-34m-x86_64-linux-gnu.so
 7fddc1f14000-7fddc1f15000 r--p 00002000 08:06 1180188                    /usr/lib/python3.4/lib-dynload/_bz2.cpython-34m-x86_64-linux-gnu.so
 7fddc1f15000-7fddc1f16000 rw-p 00003000 08:06 1180188                    /usr/lib/python3.4/lib-dynload/_bz2.cpython-34m-x86_64-linux-gnu.so
 7fddc1f16000-7fddc20b7000 rw-p 00000000 00:00 0 
 7fddc20b7000-7fddc20c2000 r-xp 00000000 08:06 397439                     /lib/x86_64-linux-gnu/libnss_files-2.19.so
 7fddc20c2000-7fddc22c1000 ---p 0000b000 08:06 397439                     /lib/x86_64-linux-gnu/libnss_files-2.19.so
 7fddc22c1000-7fddc22c2000 r--p 0000a000 08:06 397439                     /lib/x86_64-linux-gnu/libnss_files-2.19.so
 7fddc22c2000-7fddc22c3000 rw-p 0000b000 08:06 397439                     /lib/x86_64-linux-gnu/libnss_files-2.19.so
 7fddc22c3000-7fddc22ce000 r-xp 00000000 08:06 397449                     /lib/x86_64-linux-gnu/libnss_nis-2.19.so
 7fddc22ce000-7fddc24cd000 ---p 0000b000 08:06 397449                     /lib/x86_64-linux-gnu/libnss_nis-2.19.so
 7fddc24cd000-7fddc24ce000 r--p 0000a000 08:06 397449                     /lib/x86_64-linux-gnu/libnss_nis-2.19.so
 7fddc24ce000-7fddc24cf000 rw-p 0000b000 08:06 397449                     /lib/x86_64-linux-gnu/libnss_nis-2.19.so
 7fddc24cf000-7fddc24e6000 r-xp 00000000 08:06 397433                     /lib/x86_64-linux-gnu/libnsl-2.19.so
 7fddc24e6000-7fddc26e5000 ---p 00017000 08:06 397433                     /lib/x86_64-linux-gnu/libnsl-2.19.so
 7fddc26e5000-7fddc26e6000 r--p 00016000 08:06 397433                     /lib/x86_64-linux-gnu/libnsl-2.19.so
 7fddc26e6000-7fddc26e7000 rw-p 00017000 08:06 397433                     /lib/x86_64-linux-gnu/libnsl-2.19.so
 7fddc26e7000-7fddc26e9000 rw-p 00000000 00:00 0 
 7fddc26e9000-7fddc26f2000 r-xp 00000000 08:06 397435                     /lib/x86_64-linux-gnu/libnss_compat-2.19.so
 7fddc26f2000-7fddc28f1000 ---p 00009000 08:06 397435                     /lib/x86_64-linux-gnu/libnss_compat-2.19.so
 7fddc28f1000-7fddc28f2000 r--p 00008000 08:06 397435                     /lib/x86_64-linux-gnu/libnss_compat-2.19.so
 7fddc28f2000-7fddc28f3000 rw-p 00009000 08:06 397435                     /lib/x86_64-linux-gnu/libnss_compat-2.19.so
 7fddc28f3000-7fddc29f8000 r-xp 00000000 08:06 397414                     /lib/x86_64-linux-gnu/libm-2.19.so
 7fddc29f8000-7fddc2bf7000 ---p 00105000 08:06 397414                     /lib/x86_64-linux-gnu/libm-2.19.so
 7fddc2bf7000-7fddc2bf8000 r--p 00104000 08:06 397414                     /lib/x86_64-linux-gnu/libm-2.19.so
 7fddc2bf8000-7fddc2bf9000 rw-p 00105000 08:06 397414                     /lib/x86_64-linux-gnu/libm-2.19.so
 7fddc2bf9000-7fddc2c11000 r-xp 00000000 08:06 397527                     /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fddc2c11000-7fddc2e10000 ---p 00018000 08:06 397527                     /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fddc2e10000-7fddc2e11000 r--p 00017000 08:06 397527                     /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fddc2e11000-7fddc2e12000 rw-p 00018000 08:06 397527                     /lib/x86_64-linux-gnu/libz.so.1.2.8
 7fddc2e12000-7fddc2e39000 r-xp 00000000 08:06 397386                     /lib/x86_64-linux-gnu/libexpat.so.1.6.0
 7fddc2e39000-7fddc3039000 ---p 00027000 08:06 397386                     /lib/x86_64-linux-gnu/libexpat.so.1.6.0
 7fddc3039000-7fddc303b000 r--p 00027000 08:06 397386                     /lib/x86_64-linux-gnu/libexpat.so.1.6.0
 7fddc303b000-7fddc303c000 rw-p 00029000 08:06 397386                     /lib/x86_64-linux-gnu/libexpat.so.1.6.0
 7fddc303c000-7fddc303e000 r-xp 00000000 08:06 397519                     /lib/x86_64-linux-gnu/libutil-2.19.so
 7fddc303e000-7fddc323d000 ---p 00002000 08:06 397519                     /lib/x86_64-linux-gnu/libutil-2.19.so
 7fddc323d000-7fddc323e000 r--p 00001000 08:06 397519                     /lib/x86_64-linux-gnu/libutil-2.19.so
 7fddc323e000-7fddc323f000 rw-p 00002000 08:06 397519                     /lib/x86_64-linux-gnu/libutil-2.19.so
 7fddc323f000-7fddc3242000 r-xp 00000000 08:06 397381                     /lib/x86_64-linux-gnu/libdl-2.19.so
 7fddc3242000-7fddc3441000 ---p 00003000 08:06 397381                     /lib/x86_64-linux-gnu/libdl-2.19.so
 7fddc3441000-7fddc3442000 r--p 00002000 08:06 397381                     /lib/x86_64-linux-gnu/libdl-2.19.so
 7fddc3442000-7fddc3443000 rw-p 00003000 08:06 397381                     /lib/x86_64-linux-gnu/libdl-2.19.so
 7fddc3443000-7fddc35ff000 r-xp 00000000 08:06 397364                     /lib/x86_64-linux-gnu/libc-2.19.so
 7fddc35ff000-7fddc37fe000 ---p 001bc000 08:06 397364                     /lib/x86_64-linux-gnu/libc-2.19.so
 7fddc37fe000-7fddc3802000 r--p 001bb000 08:06 397364                     /lib/x86_64-linux-gnu/libc-2.19.so
 7fddc3802000-7fddc3804000 rw-p 001bf000 08:06 397364                     /lib/x86_64-linux-gnu/libc-2.19.so
 7fddc3804000-7fddc3809000 rw-p 00000000 00:00 0 
 7fddc3809000-7fddc3822000 r-xp 00000000 08:06 397484                     /lib/x86_64-linux-gnu/libpthread-2.19.so
 7fddc3822000-7fddc3a21000 ---p 00019000 08:06 397484                     /lib/x86_64-linux-gnu/libpthread-2.19.so
 7fddc3a21000-7fddc3a22000 r--p 00018000 08:06 397484                     /lib/x86_64-linux-gnu/libpthread-2.19.so
 7fddc3a22000-7fddc3a23000 rw-p 00019000 08:06 397484                     /lib/x86_64-linux-gnu/libpthread-2.19.so
 7fddc3a23000-7fddc3a27000 rw-p 00000000 00:00 0 
 7fddc3a27000-7fddc3a4a000 r-xp 00000000 08:06 397340                     /lib/x86_64-linux-gnu/ld-2.19.so
 7fddc3a78000-7fddc3ab8000 rw-p 00000000 00:00 0 
 7fddc3ae9000-7fddc3c2e000 rw-p 00000000 00:00 0 
 7fddc3c47000-7fddc3c49000 rw-p 00000000 00:00 0 
 7fddc3c49000-7fddc3c4a000 r--p 00022000 08:06 397340                     /lib/x86_64-linux-gnu/ld-2.19.so
 7fddc3c4a000-7fddc3c4b000 rw-p 00023000 08:06 397340                     /lib/x86_64-linux-gnu/ld-2.19.so
 7fddc3c4b000-7fddc3c4c000 rw-p 00000000 00:00 0 
 7fff33ce0000-7fff33d01000 rw-p 00000000 00:00 0                          [stack]
 7fff33dfe000-7fff33e00000 r-xp 00000000 00:00 0                          [vdso]
 ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
ProcStatus:
 Name:	apportcheckresu
 State:	R (running)
 Tgid:	979
 Ngid:	0
 Pid:	979
 PPid:	865
 TracerPid:	0
 Uid:	0	0	0	0
 Gid:	0	0	0	0
 FDSize:	64
 Groups:	0 
 VmPeak:	   66904 kB
 VmSize:	   66904 kB
 VmLck:	       0 kB
 VmPin:	       0 kB
 VmHWM:	   14712 kB
 VmRSS:	   14712 kB
 VmData:	    8856 kB
 VmStk:	     136 kB
 VmExe:	    3408 kB
 VmLib:	    8500 kB
 VmPTE:	     148 kB
 VmSwap:	       0 kB
 Threads:	1
 SigQ:	0/62590
 SigPnd:	0000000000000000
 ShdPnd:	0000000000000000
 SigBlk:	0000000000000000
 SigIgn:	0000000001001000
 SigCgt:	0000000180000002
 CapInh:	0000000000000000
 CapPrm:	0000001fffffffff
 CapEff:	0000001fffffffff
 CapBnd:	0000001fffffffff
 Seccomp:	0
 Cpus_allowed:	3
 Cpus_allowed_list:	0-1
 Mems_allowed:	00000000,00000001
 Mems_allowed_list:	0
 voluntary_ctxt_switches:	41
 nonvoluntary_ctxt_switches:	34
SleepLog:
 Initial commandline parameters: 
 Mon May  5 00:35:53 CEST 2014: Running hooks for suspend.
 Running hook /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend:
 /usr/lib/pm-utils/sleep.d/000kernel-change suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/000record-status suspend suspend:
 /usr/lib/pm-utils/sleep.d/000record-status suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00logging suspend suspend:
 Linux local1 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:11:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux
 Module                  Size  Used by
 dm_crypt               23177  0 
 bnep                   19624  2 
 rfcomm                 69160  0 
 bluetooth             395423  10 bnep,rfcomm
 intel_rapl             18773  0 
 x86_pkg_temp_thermal    14205  0 
 intel_powerclamp       14705  0 
 snd_hda_codec_realtek    61438  1 
 coretemp               13435  0 
 snd_hda_intel          52355  3 
 snd_hda_codec         192906  2 snd_hda_codec_realtek,snd_hda_intel
 kvm_intel             143060  0 
 joydev                 17381  0 
 kvm                   451511  1 kvm_intel
 snd_hwdep              13602  1 snd_hda_codec
 snd_pcm               102099  2 snd_hda_codec,snd_hda_intel
 snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
 snd_seq_midi           13324  0 
 snd_seq_midi_event     14899  1 snd_seq_midi
 snd_rawmidi            30144  1 snd_seq_midi
 crct10dif_pclmul       14289  0 
 snd_seq                61560  2 snd_seq_midi_event,snd_seq_midi
 crc32_pclmul           13113  0 
 snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
 psmouse               102222  0 
 ghash_clmulni_intel    13259  0 
 snd_timer              29482  2 snd_pcm,snd_seq
 serio_raw              13462  0 
 snd                    69238  16 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device,snd_seq_midi
 soundcore              12680  1 snd
 cryptd                 20359  1 ghash_clmulni_intel
 mei_me                 18627  0 
 mei                    82274  1 mei_me
 lpc_ich                21080  0 
 mac_hid                13205  0 
 parport_pc             32701  0 
 ppdev                  17671  0 
 lp                     17759  0 
 parport                42348  3 lp,ppdev,parport_pc
 hid_generic            12548  0 
 usbhid                 52616  0 
 hid                   106148  2 hid_generic,usbhid
 atl1c                  46086  0 
 i915                  783485  3 
 i2c_algo_bit           13413  1 i915
 drm_kms_helper         52758  1 i915
 video                  19476  1 i915
 drm                   302817  4 i915,drm_kms_helper
              total       used       free     shared    buffers     cached
 Mem:       8042988    3100880    4942108     590272     123084    1629768
 -/+ buffers/cache:    1348028    6694960
 Swap:            0          0          0
 /usr/lib/pm-utils/sleep.d/00logging suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/00powersave suspend suspend:
 /usr/lib/pm-utils/sleep.d/00powersave suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_grub-common suspend suspend:
 /etc/pm/sleep.d/10_grub-common suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend:
 /etc/pm/sleep.d/10_unattended-upgrades-hibernate suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend:
 /usr/lib/pm-utils/sleep.d/50unload_alx suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend:
 Failed to connect to non-global ctrl_ifname: (null)  error: No such file or directory
 /usr/lib/pm-utils/sleep.d/60_wpa_supplicant suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/75modules suspend suspend:
 /usr/lib/pm-utils/sleep.d/75modules suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/90clock suspend suspend:
 /usr/lib/pm-utils/sleep.d/90clock suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron suspend suspend:
 /usr/lib/pm-utils/sleep.d/95anacron suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led suspend suspend:
 /usr/lib/pm-utils/sleep.d/95led suspend suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend:
 Kernel modesetting video driver detected, not using quirks.
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler suspend suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video suspend suspend:
 kernel.acpi_video_flags = 0
 /usr/lib/pm-utils/sleep.d/99video suspend suspend: success.
 
 Running hook /etc/pm/sleep.d/novatel_3g_suspend suspend suspend:
 /etc/pm/sleep.d/novatel_3g_suspend suspend suspend: success.
 
 Mon May  5 00:35:53 CEST 2014: performing suspend
 Mon May  5 00:36:09 CEST 2014: Awake.
 Mon May  5 00:36:09 CEST 2014: Running hooks for resume
 Running hook /etc/pm/sleep.d/novatel_3g_suspend resume suspend:
 /etc/pm/sleep.d/novatel_3g_suspend resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/99video resume suspend:
 /usr/lib/pm-utils/sleep.d/99video resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend:
 /usr/lib/pm-utils/sleep.d/98video-quirk-db-handler resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95led resume suspend:
 /usr/lib/pm-utils/sleep.d/95led resume suspend: not applicable.
 
 Running hook /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend:
 /usr/lib/pm-utils/sleep.d/95hdparm-apm resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/95anacron resume suspend:
 /usr/lib/pm-utils/sleep.d/95anacron resume suspend: success.
 
 Running hook /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend:
 /usr/lib/pm-utils/sleep.d/94cpufreq resume suspend: success.
```

---

