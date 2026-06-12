---
title: "sddm-greeter crashes  locks server"
date: 2021-09-30
forum: General Help
---

### Post by linuxpc4me on 2021-09-30
Hello All!

I have new Dell Power edge server and installed Lubuntu 20.04 (upgraded to 20.10)

Frequently, the server locks  up.  The only way to resolve is kill the power. Dell had discovered some faulty components and replaced those.  But the freezes continue.
After a lot of reading, I found  a crash report " /var/crash/_usr_bin_sddm-greeter.118.crash

Here is excerpt starting with line 1:

ProblemType: Crash
Architecture: amd64
Date: Thu Sep 23 14:00:17 2021
DistroRelease: Ubuntu 20.10
ExecutablePath: /usr/bin/sddm-greeter
ExecutableTimestamp: 1597300990
ProcCmdline: /usr/bin/sddm-greeter --socket /tmp/sddm-:0-cGcrua --theme /usr/share/sddm/themes/ubuntu-theme
ProcCwd: /var/lib/sddm
ProcEnviron:
 LANG=en_US.UTF-8
 LC_ADDRESS=en_US.UTF-8
 LC_IDENTIFICATION=en_US.UTF-8
 LC_MEASUREMENT=en_US.UTF-8
 LC_MONETARY=en_US.UTF-8
 LC_NAME=en_US.UTF-8
 LC_NUMERIC=en_US.UTF-8
 LC_PAPER=en_US.UTF-8
 LC_TELEPHONE=en_US.UTF-8
 LC_TIME=en_US.UTF-8
 PATH=(custom, no user)
 SHELL=/bin/false
 XDG_RUNTIME_DIR=<set>
ProcMaps:


>>>  skipping portion <<<<<


1009 ProcStatus:
1010  Name:  sddm-greeter
1011  Umask: 0002
1012  State: D (disk sleep)
1013  Tgid:  2320
1014  Ngid:  2358
1015  Pid:   2320
1016  PPid:  2306
1017  TracerPid:     0
1018  Uid:   118     118     118     118
1019  Gid:   125     125     125     125
1020  FDSize:        64
1021  Groups:        125
1022  NStgid:        2320
1023  NSpid: 2320
1024  NSpgid:        1234
1025  NSsid: 1234
1026  VmPeak:         3283888 kB
1027  VmSize:         3279808 kB
1028  VmLck:        0 kB
1029  VmPin:        0 kB
1030  VmHWM:   186548 kB
1031  VmRSS:   186548 kB
1032  RssAnon:         101932 kB
1033  RssFile:          80584 kB
1034  RssShmem:          4032 kB
1035  VmData:          447800 kB
1036  VmStk:      132 kB
1037  VmExe:      120 kB
1038  VmLib:   127240 kB
1039  VmPTE:      940 kB
1040  VmSwap:               0 kB
1041  HugetlbPages:         0 kB
1042  CoreDumping:   1
1043  THP_enabled:   1
1044  Threads:       41
1045  SigQ:  0/62199
1046  SigPnd:        0000000000000000
1047  ShdPnd:        0000000000000000
1048  SigBlk:        0000000000000000
1049  SigIgn:        0000000000001000
1050  SigCgt:        0000000180000000
1051  CapInh:        0000000000000000
1052  CapPrm:        0000000000000000
1053  CapEff:        0000000000000000
1054  CapBnd:        000000ffffffffff
1055  CapAmb:        0000000000000000
1056  NoNewPrivs:    0
1057  Seccomp:       0
1058  Speculation_Store_Bypass:      thread vulnerable
1059  Cpus_allowed:  ffffffff
1060  Cpus_allowed_list:     0-31
1061  Mems_allowed:  00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,00000000,000>1062  Mems_allowed_list:     0-1
1063  voluntary_ctxt_switches:       4509085
1064  nonvoluntary_ctxt_switches:    63736
1065 Signal: 11
1066 Uname: Linux 5.8.0-63-generic x86_64
1067 UserGroups: N/A
1068 CoreDump: base64
1069  H4sICAAAAAAC/0NvcmVEdW1wAA==

>>> more below but not copied here<<<<


So it appears the login screen ( sddm-greeter) is goobered  up and the server plays dead.

Can anyone suggest a fix?

Thanks so much

---

### Post by guiverc on 2021-09-30
Ubuntu 20.10 (*along with all flavors*) is ***End-of-Life***

See 

- [https://fridge.ubuntu.com/2021/07/25/ubuntu-20-10-groovy-gorilla-end-of-life-reached-on-july-22-2021/](https://fridge.ubuntu.com/2021/07/25/ubuntu-20-10-groovy-gorilla-end-of-life-reached-on-july-22-2021/)
- [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

Unless your box is off-line, I'd suggest moving to a *supported* release (and use LTS releases unless you're willing to *release-upgrade* every 6-9 months; 20.10 tells you it was the 2020-October release; with 9 months of *life* knowing it'll EOL in 2021-July isn't difficult)

---

