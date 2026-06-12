---
title: "LibreOffice is causing whole system crash"
date: 2017-11-13
forum: General Help
---

### Post by BigBaka on 2017-11-13
I'm working with a simple word document and a simple impress document in libre office, and for some reason it keeps crashing, logging out of the system and taking me to a login page. I looked around and saw a bug with Oracle Java, but I've already uninstalled that and installed open jdk instead.

I read the crash log and come up with the following.Thoughts? I have just reinstalled the system last week after some hard disk troubles, but suddenly started doing this, this morning.
Using Ubuntu 16.04 LTS
Libreoffice 5.1.6.2

> ProblemType: Crash
Architecture: amd64
CurrentDesktop: Unity
Date: Tue Nov 14 04:40:11 2017
DistroRelease: Ubuntu 16.04
ExecutablePath: /sbin/upstart
ExecutableTimestamp: 1463667884
ProcCmdline: /sbin/upstart --user
ProcCwd: /home/glenn
ProcEnviron:
 LC_PAPER=en_AU.UTF-8
 LC_ADDRESS=en_AU.UTF-8
 LC_MONETARY=en_AU.UTF-8
 SHELL=/bin/bash
 LC_NUMERIC=en_AU.UTF-8
 LC_TELEPHONE=en_AU.UTF-8
 PATH=(custom, user)
 LC_IDENTIFICATION=en_AU.UTF-8
 LANG=en_AU.UTF-8
 LC_MEASUREMENT=en_AU.UTF-8
 LANGUAGE=en_AU:en_US:en
 XDG_RUNTIME_DIR=<set>
 LC_TIME=en_AU.UTF-8
 LC_NAME=en_AU.UTF-8
ProcMaps:
 55f855489000-55f8554d0000 r-xp 00000000 08:05 393435                     /sbin/upstart
 55f8556d0000-55f8556d2000 r--p 00047000 08:05 393435                     /sbin/upstart
 55f8556d2000-55f8556d3000 rw-p 00049000 08:05 393435                     /sbin/upstart
 55f856b8b000-55f856c70000 rw-p 00000000 00:00 0                          [heap]
 7feb1897f000-7feb1898a000 r-xp 00000000 08:05 2364175                    /lib/x86_64-linux-gnu/libnss_files-2.23.so
 7feb1898a000-7feb18b89000 ---p 0000b000 08:05 2364175                    /lib/x86_64-linux-gnu/libnss_files-2.23.so
 7feb18b89000-7feb18b8a000 r--p 0000a000 08:05 2364175                    /lib/x86_64-linux-gnu/libnss_files-2.23.so
 7feb18b8a000-7feb18b8b000 rw-p 0000b000 08:05 2364175                    /lib/x86_64-linux-gnu/libnss_files-2.23.so
 7feb18b8b000-7feb18b91000 rw-p 00000000 00:00 0 
 7feb18b91000-7feb18b9c000 r-xp 00000000 08:05 2364185                    /lib/x86_64-linux-gnu/libnss_nis-2.23.so
 7feb18b9c000-7feb18d9b000 ---p 0000b000 08:05 2364185                    /lib/x86_64-linux-gnu/libnss_nis-2.23.so
 7feb18d9b000-7feb18d9c000 r--p 0000a000 08:05 2364185                    /lib/x86_64-linux-gnu/libnss_nis-2.23.so
 7feb18d9c000-7feb18d9d000 rw-p 0000b000 08:05 2364185                    /lib/x86_64-linux-gnu/libnss_nis-2.23.so
 7feb18d9d000-7feb18db3000 r-xp 00000000 08:05 2364169                    /lib/x86_64-linux-gnu/libnsl-2.23.so
 7feb18db3000-7feb18fb2000 ---p 00016000 08:05 2364169                    /lib/x86_64-linux-gnu/libnsl-2.23.so
 7feb18fb2000-7feb18fb3000 r--p 00015000 08:05 2364169                    /lib/x86_64-linux-gnu/libnsl-2.23.so
 7feb18fb3000-7feb18fb4000 rw-p 00016000 08:05 2364169                    /lib/x86_64-linux-gnu/libnsl-2.23.so
 7feb18fb4000-7feb18fb6000 rw-p 00000000 00:00 0 
 7feb18fb6000-7feb18fbe000 r-xp 00000000 08:05 2364171                    /lib/x86_64-linux-gnu/libnss_compat-2.23.so
 7feb18fbe000-7feb191bd000 ---p 00008000 08:05 2364171                    /lib/x86_64-linux-gnu/libnss_compat-2.23.so
 7feb191bd000-7feb191be000 r--p 00007000 08:05 2364171                    /lib/x86_64-linux-gnu/libnss_compat-2.23.so
 7feb191be000-7feb191bf000 rw-p 00008000 08:05 2364171                    /lib/x86_64-linux-gnu/libnss_compat-2.23.so
 7feb191bf000-7feb19bc5000 r--p 00000000 08:05 1187719                    /usr/lib/locale/locale-archive
 7feb19bc5000-7feb19bd7000 r-xp 00000000 08:05 2364120                    /lib/x86_64-linux-gnu/libgpg-error.so.0.17.0
 7feb19bd7000-7feb19dd7000 ---p 00012000 08:05 2364120                    /lib/x86_64-linux-gnu/libgpg-error.so.0.17.0
 7feb19dd7000-7feb19dd8000 r--p 00012000 08:05 2364120                    /lib/x86_64-linux-gnu/libgpg-error.so.0.17.0
 7feb19dd8000-7feb19dd9000 rw-p 00013000 08:05 2364120                    /lib/x86_64-linux-gnu/libgpg-error.so.0.17.0
 7feb19dd9000-7feb19ddc000 r-xp 00000000 08:05 2364100                    /lib/x86_64-linux-gnu/libdl-2.23.so
 7feb19ddc000-7feb19fdb000 ---p 00003000 08:05 2364100                    /lib/x86_64-linux-gnu/libdl-2.23.so
 7feb19fdb000-7feb19fdc000 r--p 00002000 08:05 2364100                    /lib/x86_64-linux-gnu/libdl-2.23.so
 7feb19fdc000-7feb19fdd000 rw-p 00003000 08:05 2364100                    /lib/x86_64-linux-gnu/libdl-2.23.so
 7feb19fdd000-7feb1a04b000 r-xp 00000000 08:05 2364205                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
 7feb1a04b000-7feb1a24b000 ---p 0006e000 08:05 2364205                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
 7feb1a24b000-7feb1a24c000 r--p 0006e000 08:05 2364205                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
 7feb1a24c000-7feb1a24d000 rw-p 0006f000 08:05 2364205                    /lib/x86_64-linux-gnu/libpcre.so.3.13.2
 7feb1a24d000-7feb1a325000 r-xp 00000000 08:05 2364116                    /lib/x86_64-linux-gnu/libgcrypt.so.20.0.5
 7feb1a325000-7feb1a524000 ---p 000d8000 08:05 2364116                    /lib/x86_64-linux-gnu/libgcrypt.so.20.0.5
 7feb1a524000-7feb1a525000 r--p 000d7000 08:05 2364116                    /lib/x86_64-linux-gnu/libgcrypt.so.20.0.5
 7feb1a525000-7feb1a52d000 rw-p 000d8000 08:05 2364116                    /lib/x86_64-linux-gnu/libgcrypt.so.20.0.5
 7feb1a52d000-7feb1a52e000 rw-p 00000000 00:00 0 
 7feb1a52e000-7feb1a54f000 r-xp 00000000 08:05 2364143                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
 7feb1a54f000-7feb1a74e000 ---p 00021000 08:05 2364143                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
 7feb1a74e000-7feb1a74f000 r--p 00020000 08:05 2364143                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
 7feb1a74f000-7feb1a750000 rw-p 00021000 08:05 2364143                    /lib/x86_64-linux-gnu/liblzma.so.5.0.0
 7feb1a750000-7feb1a76f000 r-xp 00000000 08:05 2364234                    /lib/x86_64-linux-gnu/libselinux.so.1
 7feb1a76f000-7feb1a96e000 ---p 0001f000 08:05 2364234                    /lib/x86_64-linux-gnu/libselinux.so.1
 7feb1a96e000-7feb1a96f000 r--p 0001e000 08:05 2364234                    /lib/x86_64-linux-gnu/libselinux.so.1
 7feb1a96f000-7feb1a970000 rw-p 0001f000 08:05 2364234                    /lib/x86_64-linux-gnu/libselinux.so.1
 7feb1a970000-7feb1a972000 rw-p 00000000 00:00 0 
 7feb1a972000-7feb1a98a000 r-xp 00000000 08:05 2364222                    /lib/x86_64-linux-gnu/libpthread-2.23.so
 7feb1a98a000-7feb1ab89000 ---p 00018000 08:05 2364222                    /lib/x86_64-linux-gnu/libpthread-2.23.so
 7feb1ab89000-7feb1ab8a000 r--p 00017000 08:05 2364222                    /lib/x86_64-linux-gnu/libpthread-2.23.so
 7feb1ab8a000-7feb1ab8b000 rw-p 00018000 08:05 2364222                    /lib/x86_64-linux-gnu/libpthread-2.23.so
 7feb1ab8b000-7feb1ab8f000 rw-p 00000000 00:00 0 
 7feb1ab8f000-7feb1ad4f000 r-xp 00000000 08:05 2364076                    /lib/x86_64-linux-gnu/libc-2.23.so
 7feb1ad4f000-7feb1af4f000 ---p 001c0000 08:05 2364076                    /lib/x86_64-linux-gnu/libc-2.23.so
 7feb1af4f000-7feb1af53000 r--p 001c0000 08:05 2364076                    /lib/x86_64-linux-gnu/libc-2.23.so
 7feb1af53000-7feb1af55000 rw-p 001c4000 08:05 2364076                    /lib/x86_64-linux-gnu/libc-2.23.so
 7feb1af55000-7feb1af59000 rw-p 00000000 00:00 0 
 7feb1af59000-7feb1af60000 r-xp 00000000 08:05 2364230                    /lib/x86_64-linux-gnu/librt-2.23.so
 7feb1af60000-7feb1b15f000 ---p 00007000 08:05 2364230                    /lib/x86_64-linux-gnu/librt-2.23.so
 7feb1b15f000-7feb1b160000 r--p 00006000 08:05 2364230                    /lib/x86_64-linux-gnu/librt-2.23.so
 7feb1b160000-7feb1b161000 rw-p 00007000 08:05 2364230                    /lib/x86_64-linux-gnu/librt-2.23.so
 7feb1b161000-7feb1b1ab000 r-xp 00000000 08:05 2364092                    /lib/x86_64-linux-gnu/libdbus-1.so.3.14.6
 7feb1b1ab000-7feb1b3ab000 ---p 0004a000 08:05 2364092                    /lib/x86_64-linux-gnu/libdbus-1.so.3.14.6
 7feb1b3ab000-7feb1b3ac000 r--p 0004a000 08:05 2364092                    /lib/x86_64-linux-gnu/libdbus-1.so.3.14.6
 7feb1b3ac000-7feb1b3ad000 rw-p 0004b000 08:05 2364092                    /lib/x86_64-linux-gnu/libdbus-1.so.3.14.6
 7feb1b3ad000-7feb1b3b5000 r-xp 00000000 08:05 2364162                    /lib/x86_64-linux-gnu/libnih-dbus.so.1.0.0
 7feb1b3b5000-7feb1b5b5000 ---p 00008000 08:05 2364162                    /lib/x86_64-linux-gnu/libnih-dbus.so.1.0.0
 7feb1b5b5000-7feb1b5b6000 r--p 00008000 08:05 2364162                    /lib/x86_64-linux-gnu/libnih-dbus.so.1.0.0
 7feb1b5b6000-7feb1b5b7000 rw-p 00009000 08:05 2364162                    /lib/x86_64-linux-gnu/libnih-dbus.so.1.0.0
 7feb1b5b7000-7feb1b5ce000 r-xp 00000000 08:05 2364164                    /lib/x86_64-linux-gnu/libnih.so.1.0.0
 7feb1b5ce000-7feb1b7ce000 ---p 00017000 08:05 2364164                    /lib/x86_64-linux-gnu/libnih.so.1.0.0
 7feb1b7ce000-7feb1b7cf000 r--p 00017000 08:05 2364164                    /lib/x86_64-linux-gnu/libnih.so.1.0.0
 7feb1b7cf000-7feb1b7d0000 rw-p 00018000 08:05 2364164                    /lib/x86_64-linux-gnu/libnih.so.1.0.0
 7feb1b7d0000-7feb1b7f1000 r-xp 00000000 08:05 2364081                    /lib/x86_64-linux-gnu/libcgmanager.so.0.0.0
 7feb1b7f1000-7feb1b9f0000 ---p 00021000 08:05 2364081                    /lib/x86_64-linux-gnu/libcgmanager.so.0.0.0
 7feb1b9f0000-7feb1b9f2000 r--p 00020000 08:05 2364081                    /lib/x86_64-linux-gnu/libcgmanager.so.0.0.0
 7feb1b9f2000-7feb1b9f3000 rw-p 00022000 08:05 2364081                    /lib/x86_64-linux-gnu/libcgmanager.so.0.0.0
 7feb1b9f3000-7feb1b9fd000 r-xp 00000000 08:05 2364135                    /lib/x86_64-linux-gnu/libjson-c.so.2.0.0
 7feb1b9fd000-7feb1bbfc000 ---p 0000a000 08:05 2364135                    /lib/x86_64-linux-gnu/libjson-c.so.2.0.0
 7feb1bbfc000-7feb1bbfd000 r--p 00009000 08:05 2364135                    /lib/x86_64-linux-gnu/libjson-c.so.2.0.0
 7feb1bbfd000-7feb1bbfe000 rw-p 0000a000 08:05 2364135                    /lib/x86_64-linux-gnu/libjson-c.so.2.0.0
 7feb1bbfe000-7feb1bc24000 r-xp 00000000 08:05 2364048                    /lib/x86_64-linux-gnu/ld-2.23.so
 7feb1bd77000-7feb1bd7d000 rw-p 00000000 00:00 0 
 7feb1bd7d000-7feb1bdfd000 r-xp 00000000 08:05 2359379                    /lib/x86_64-linux-gnu/libsystemd.so.0.14.0
 7feb1bdfd000-7feb1be00000 r--p 0007f000 08:05 2359379                    /lib/x86_64-linux-gnu/libsystemd.so.0.14.0
 7feb1be00000-7feb1be01000 rw-p 00082000 08:05 2359379                    /lib/x86_64-linux-gnu/libsystemd.so.0.14.0
 7feb1be01000-7feb1be05000 rw-p 00000000 00:00 0 
 7feb1be18000-7feb1be1f000 r--s 00000000 08:05 1443802                    /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
 7feb1be1f000-7feb1be20000 r--p 00000000 08:05 1710255                    /usr/share/locale-langpack/en_AU/LC_MESSAGES/libc.mo
 7feb1be20000-7feb1be21000 r--p 00000000 08:05 1710422                    /usr/share/locale-langpack/en_AU/LC_MESSAGES/upstart.mo
 7feb1be21000-7feb1be23000 rw-p 00000000 00:00 0 
 7feb1be23000-7feb1be24000 r--p 00025000 08:05 2364048                    /lib/x86_64-linux-gnu/ld-2.23.so
 7feb1be24000-7feb1be25000 rw-p 00026000 08:05 2364048                    /lib/x86_64-linux-gnu/ld-2.23.so
 7feb1be25000-7feb1be26000 rw-p 00000000 00:00 0 
 7ffc76b1b000-7ffc76b3c000 rw-p 00000000 00:00 0                          [stack]
 7ffc76ba8000-7ffc76baa000 r--p 00000000 00:00 0                          [vvar]
 7ffc76baa000-7ffc76bac000 r-xp 00000000 00:00 0                          [vdso]
 ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
ProcStatus:
 Name:	upstart
 Umask:	0002
 State:	S (sleeping)
 Tgid:	4126
 Ngid:	0
 Pid:	4126
 PPid:	3957
 TracerPid:	0
 Uid:	1000	1000	1000	1000
 Gid:	1000	1000	1000	1000
 FDSize:	256
 Groups:	4 24 27 30 46 113 128 1000 
 NStgid:	4126
 NSpid:	4126
 NSpgid:	4126
 NSsid:	4126
 VmPeak:	   53852 kB
 VmSize:	   53844 kB
 VmLck:	       0 kB
 VmPin:	       0 kB
 VmHWM:	    4756 kB
 VmRSS:	    4756 kB
 RssAnon:	    1184 kB
 RssFile:	    3572 kB
 RssShmem:	       0 kB
 VmData:	    1160 kB
 VmStk:	     132 kB
 VmExe:	     284 kB
 VmLib:	    5032 kB
 VmPTE:	     120 kB
 VmPMD:	      12 kB
 VmSwap:	       0 kB
 HugetlbPages:	       0 kB
 Threads:	1
 SigQ:	22/30567
 SigPnd:	0000000000000000
 ShdPnd:	0000000000000000
 SigBlk:	0000000000000000
 SigIgn:	0000000000001000
 SigCgt:	0000000180016001
 CapInh:	0000000000000000
 CapPrm:	0000000000000000
 CapEff:	0000000000000000
 CapBnd:	0000003fffffffff
 CapAmb:	0000000000000000
 NoNewPrivs:	0
 Seccomp:	0
 Cpus_allowed:	f
 Cpus_allowed_list:	0-3
 Mems_allowed:	00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000001
 Mems_allowed_list:	0
 voluntary_ctxt_switches:	479
 nonvoluntary_ctxt_switches:	759
Signal: 6
Uname: Linux 4.10.0-38-generic x86_64
UserGroups: adm cdrom dip lpadmin plugdev sambashare sudo
_LogindSession: c5
CoreDump: base64

---

### Post by BigBaka on 2017-11-20
Just happened again
Couldn't see anything in the crash log, but got this from var/log/kern.log at the time it happened.



> Nov 20 15:40:34 advisor kernel: [25599.857152] [drm] GPU HANG: ecode 9:0:0x85dffffb, in Xorg [1051], reason: Hang on render ring, action: reset
Nov 20 15:40:34 advisor kernel: [25599.857193] drm/i915: Resetting chip after gpu hang
Nov 20 15:40:34 advisor kernel: [25599.857250] [drm] RC6 on
Nov 20 15:40:34 advisor kernel: [25599.872716] [drm] GuC firmware load skipped
Nov 20 15:40:35 advisor kernel: [25600.534278] [drm] probing gen 2 caps for device 8086:9d10 = 1724843/e
Nov 20 15:40:35 advisor kernel: [25600.534281] [drm] PCIE gen 3 link speeds already enabled
Nov 20 15:40:35 advisor kernel: [25600.540154] [drm] PCIE GART of 2048M enabled (table at 0x0000000000040000).
Nov 20 15:40:35 advisor kernel: [25600.540257] radeon 0000:01:00.0: WB enabled
Nov 20 15:40:35 advisor kernel: [25600.540258] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000100000c00 and cpu addr 0xffff9fd92fb0ec00
Nov 20 15:40:35 advisor kernel: [25600.540260] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000100000c04 and cpu addr 0xffff9fd92fb0ec04
Nov 20 15:40:35 advisor kernel: [25600.540261] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000100000c08 and cpu addr 0xffff9fd92fb0ec08
Nov 20 15:40:35 advisor kernel: [25600.540262] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000100000c0c and cpu addr 0xffff9fd92fb0ec0c
Nov 20 15:40:35 advisor kernel: [25600.540263] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000100000c10 and cpu addr 0xffff9fd92fb0ec10
Nov 20 15:40:35 advisor kernel: [25600.732991] [drm] ring test on 0 succeeded in 1 usecs
Nov 20 15:40:35 advisor kernel: [25600.732995] [drm] ring test on 1 succeeded in 1 usecs
Nov 20 15:40:35 advisor kernel: [25600.733000] [drm] ring test on 2 succeeded in 1 usecs
Nov 20 15:40:35 advisor kernel: [25600.733007] [drm] ring test on 3 succeeded in 4 usecs
Nov 20 15:40:35 advisor kernel: [25600.733012] [drm] ring test on 4 succeeded in 3 usecs
Nov 20 15:40:35 advisor kernel: [25600.733103] [drm] ib test on ring 0 succeeded in 0 usecs
Nov 20 15:40:35 advisor kernel: [25600.733164] [drm] ib test on ring 1 succeeded in 0 usecs
Nov 20 15:40:35 advisor kernel: [25600.733266] [drm] ib test on ring 2 succeeded in 0 usecs
Nov 20 15:40:35 advisor kernel: [25600.733280] [drm] ib test on ring 3 succeeded in 0 usecs
Nov 20 15:40:35 advisor kernel: [25600.733294] [drm] ib test on ring 4 succeeded in 0 usecs
Nov 20 15:40:46 advisor kernel: [25611.812618] drm/i915: Resetting chip after gpu hang
Nov 20 15:40:46 advisor kernel: [25611.812728] [drm] RC6 on
Nov 20 15:40:46 advisor kernel: [25611.824190] [drm] GuC firmware load skipped
Nov 20 15:40:46 advisor kernel: [25612.018085] Chrome_~dThread[9309]: segfault at 0 ip 00007ff0b1031fe2 sp 00007ff0a5afe4f0 error 6 in libxul.so[7ff0b01c3000+57b2000]
Nov 20 15:40:47 advisor kernel: [25612.882970] [drm] probing gen 2 caps for device 8086:9d10 = 1724843/e
Nov 20 15:40:47 advisor kernel: [25612.882973] [drm] PCIE gen 3 link speeds already enabled
Nov 20 15:40:47 advisor kernel: [25612.888837] [drm] PCIE GART of 2048M enabled (table at 0x0000000000040000).
Nov 20 15:40:47 advisor kernel: [25612.888931] radeon 0000:01:00.0: WB enabled
Nov 20 15:40:47 advisor kernel: [25612.888933] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000100000c00 and cpu addr 0xffff9fd92fb0ec00
Nov 20 15:40:47 advisor kernel: [25612.888934] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000100000c04 and cpu addr 0xffff9fd92fb0ec04
Nov 20 15:40:47 advisor kernel: [25612.888935] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000100000c08 and cpu addr 0xffff9fd92fb0ec08
Nov 20 15:40:47 advisor kernel: [25612.888936] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000100000c0c and cpu addr 0xffff9fd92fb0ec0c
Nov 20 15:40:47 advisor kernel: [25612.888936] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000100000c10 and cpu addr 0xffff9fd92fb0ec10
Nov 20 15:40:47 advisor kernel: [25613.081910] [drm] ring test on 0 succeeded in 1 usecs
Nov 20 15:40:47 advisor kernel: [25613.081915] [drm] ring test on 1 succeeded in 1 usecs
Nov 20 15:40:47 advisor kernel: [25613.081919] [drm] ring test on 2 succeeded in 1 usecs
Nov 20 15:40:47 advisor kernel: [25613.081926] [drm] ring test on 3 succeeded in 4 usecs
Nov 20 15:40:47 advisor kernel: [25613.081932] [drm] ring test on 4 succeeded in 3 usecs
Nov 20 15:40:47 advisor kernel: [25613.082021] [drm] ib test on ring 0 succeeded in 0 usecs
Nov 20 15:40:47 advisor kernel: [25613.082081] [drm] ib test on ring 1 succeeded in 0 usecs
Nov 20 15:40:47 advisor kernel: [25613.082182] [drm] ib test on ring 2 succeeded in 0 usecs
Nov 20 15:40:47 advisor kernel: [25613.082195] [drm] ib test on ring 3 succeeded in 0 usecs
Nov 20 15:40:47 advisor kernel: [25613.082206] [drm] ib test on ring 4 succeeded in 0 usecs
Nov 20 15:41:12 advisor gnome-session-binary[10671]: Entering running state



Any ideas?

---

### Post by BigBaka on 2017-11-22
So seems I'm to answer my own question.

Since my system crashed again a couple of days ago, I have been looking around and found this thread [LibreOffice 5.1.6.2 crashes ubuntu 16.04 (64-bit)]("https://askubuntu.com/questions/964576/libreoffice-5-1-6-2-crashes-ubuntu-16-04-64-bit")

Based on that I tried this

> sudo apt remove xserver-xorg-core-hwe-16.04 xserver-xorg-input-all-hwe-16.04 linux-generic-hwe-16.04 xserver-xorg-video-all-hwe-16.04

Then:

> sudo apt install xserver-xorg-core

And finally:

> sudo apt install ubuntu-desktop xserver-xorg xserver-xorg-video-all xserver-xorg-

It's been a couple of days now without a crash, seems to be holding up.

---

### Post by mastablasta on 2017-11-22
you can also try with newer version of Libre office. it has various improvements and bugfixes. the long term support version ("stale") is now at 5.3.7, while the "normal" stable one (Fresh) is at 5.4.3.

add a PPA of your choice to have it updated: [https://launchpad.net/~libreoffice/+archive/ubuntu/ppa](https://launchpad.net/~libreoffice/+archive/ubuntu/ppa)

i found it beneficial to keep the office software updated (at least on stale version), because the development is quite active and they are solving many bugs with each new release. the new features and design improvements are also generally good, which is why i would also keep it up to date and on Fresh on windows pcs.

---

### Post by BigBaka on 2017-11-29
Just by way of a quick update, my problem seems to have been resolved after making the above changes. 

@mastarblaster - thanks for the idea, I had previously been using the newer releases of libreoffice in my old setup, but just got the feeling that the newer release was slightly  more buggy than the stable ("stale") version, so keeping with stale for the moment.

---

