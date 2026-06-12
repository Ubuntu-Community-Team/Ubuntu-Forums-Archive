---
title: "Ubuntu 12.10 Locks up and crashes frequently"
date: 2013-04-03
forum: General Help
---

### Post by Alake28 on 2013-04-03
I have been reading everywhere looking for a solution to this problem. I am a relatively new linux user so bear with me. I am trying to learn the ropes, but this issue I am having is backing me to a corner. The problem I am having is that ubuntu will crash and send me back to login whenever I do certain actions. Two actions that I can pinpoint is trying log into steam and switching windows. I will have my browser or terminal open, and then if i click to a window underneith it, it will just crash and send me to login. I checked my var/crash logs and the only file that shows up is a Xorg.0.crash file. The consensus I'm reading is that it might be a graphical issue so I've updated the drivers through ppa if i'm mistaken. I also tried all the of the drivers available in the software sources tool. All of them continue to bug out. Only the Xorg Nev driver even loads up the UI and dash for ubuntu, the rest fail to load up the Dash/UI on boot and I have to manually find my way to the driver settings to switch them to the Xorg drivers. Last thing I can say is that even with the Xorg drivers, it still crashes. Another odd thing about those drivers is that when I first start loading up the OS it gives me a purple screen(i assume normal), and then it glitches graphically for a second. After that, it takes me to the dash/ui. I'd love to post my crash report, but I dont know enough about linux to open a file other than pico and I can't c/p all that from the terminal since it crashes when i switch windows. If someone can give me the optimal way to show you guys what you need to see, I will be glad to provide that information. I am enjoying Ubuntu so far, it definitely speeds up my system, but these crashes are getting to me. 

Some additional specs:
Mobo:asus m3a78-t
CPU:AMD PHENOM 940 Quad 3.0ghz
GPU:Gforce GTX 650
Mem:4GB
OS:Ubuntu 12.10 64bit.

Thank you.

---

### Post by Alake28 on 2013-04-03
```
ProblemType: CrashArchitecture: amd64
CrashCounter: 1
Date: Wed Apr  3 20:47:29 2013
DistroRelease: Ubuntu 12.10
ExecutablePath: /usr/bin/Xorg
ExecutableTimestamp: 1354002419
ProcCmdline: /usr/bin/X :0 -core -auth /var/run/lightdm/root/:0 -nolisten tcp v$
ProcCwd: /etc/X11
ProcEnviron:
ProcMaps:
 7f87a6ffd000-7f87a7312000 rw-s 00000000 00:04 819203                     /SYSV$
 7f87a7312000-7f87a7326000 rw-s 00000000 00:04 786434                     /SYSV$
 7f87a7326000-7f87a7332000 r-xp 00000000 08:01 2887187                    /lib/$
 7f87a7332000-7f87a7531000 ---p 0000c000 08:01 2887187                    /lib/$
 7f87a7531000-7f87a7532000 r--p 0000b000 08:01 2887187                    /lib/$
 7f87a7532000-7f87a7533000 rw-p 0000c000 08:01 2887187                    /lib/$
 7f87a7533000-7f87a753d000 r-xp 00000000 08:01 2887191                    /lib/$
 7f87a753d000-7f87a773d000 ---p 0000a000 08:01 2887191                    /lib/$
7f87a7961000-7f87a7b60000 ---p 00008000 08:01 2887183                    /lib/$
 7f87a7b60000-7f87a7b61000 r--p 00007000 08:01 2887183                    /lib/$
 7f87a7b61000-7f87a7b62000 rw-p 00008000 08:01 2887183                    /lib/$
 7f87a7b62000-7f87a7b67000 r-xp 00000000 08:01 1842805                    /usr/$
 7f87a7b67000-7f87a7d66000 ---p 00005000 08:01 1842805                    /usr/$
 7f87a7d66000-7f87a7d67000 r--p 00004000 08:01 1842805                    /usr/$
 7f87a7d67000-7f87a7d68000 rw-p 00005000 08:01 1842805                    /usr/$
 7f87a7d7a000-7f87a7d86000 r-xp 00000000 08:01 2231128                    /usr/$
 7f87a7d86000-7f87a7f86000 ---p 0000c000 08:01 2231128                    /usr/$
 7f87a7f86000-7f87a7f87000 r--p 0000c000 08:01 2231128                    /usr/$
 7f87a7f87000-7f87a7f88000 rw-p 0000d000 08:01 2231128                    /usr/$
 7f87a7f88000-7f87a84a8000 rw-s 100559000 00:05 8789                      /dev/$
7f87a84d9000-7f87a86d8000 ---p 00031000 08:01 1843016                    /usr/$
 7f87a86d8000-7f87a86d9000 r--p 00030000 08:01 1843016                    /usr/$
 7f87a86d9000-7f87a86da000 rw-p 00031000 08:01 1843016                    /usr/$
 7f87a86da000-7f87a86db000 ---p 00000000 00:00 0
 7f87a86db000-7f87a8edb000 rw-p 00000000 00:00 0                          [stac$
 7f87a8edb000-7f87a8edc000 ---p 00000000 00:00 0
 7f87a8edc000-7f87a96dc000 rw-p 00000000 00:00 0                          [stac$
 7f87a96dc000-7f87a96dd000 ---p 00000000 00:00 0
 7f87a96dd000-7f87a9edd000 rw-p 00000000 00:00 0                          [stac$
 7f87a9edd000-7f87a9ede000 ---p 00000000 00:00 0
 7f87a9ede000-7f87aa6de000 rw-p 00000000 00:00 0                          [stac$
 7f87aa6de000-7f87aa6e5000 r-xp 00000000 08:01 1842539                    /usr/$
 7f87aa6e5000-7f87aa8e4000 ---p 00007000 08:01 1842539                    /usr/$
 7f87aa8e4000-7f87aa8e5000 r--p 00006000 08:01 1842539                    /usr/$
 7f87aa8e5000-7f87aa8e6000 rw-p 00007000 08:01 1842539                    /usr/$
 7f87aa8e6000-7f87aa907000 r-xp 00000000 08:01 1837881                    /usr/$
 7f87aa907000-7f87aab07000 ---p 00021000 08:01 1837881                    /usr/$
 7f87aab07000-7f87aab0a000 r--p 00021000 08:01 1837881                    /usr/$
 7f87aab0a000-7f87aab0b000 rw-p 00024000 08:01 1837881                    /usr/$
7f87ac03d000-7f87ac049000 rw-p 00000000 00:00 0
 7f87ac049000-7f87ac06f000 r-xp 00000000 08:01 2887142                    /lib/$
 7f87ac06f000-7f87ac26f000 ---p 00026000 08:01 2887142                    /lib/$
 7f87ac26f000-7f87ac271000 r--p 00026000 08:01 2887142                    /lib/$
 7f87ac271000-7f87ac272000 rw-p 00028000 08:01 2887142                    /lib/$
 7f87ac272000-7f87ac5e7000 r-xp 00000000 08:01 1837760                    /usr/$
 7f87ac5e7000-7f87ac7e7000 ---p 00375000 08:01 1837760                    /usr/$
 7f87ac7e7000-7f87ac7fa000 r--p 00375000 08:01 1837760                    /usr/$
 7f87ac7fa000-7f87ac801000 rw-p 00388000 08:01 1837760                    /usr/$
 7f87ac801000-7f87ac81a000 rw-p 00000000 00:00 0
 7f87ac81a000-7f87aca1a000 r-xp 00000000 08:01 1837752                    /usr/$
 7f87aca1a000-7f87aca29000 r--p 00200000 08:01 1837752                    /usr/$
 7f87aca29000-7f87aca2d000 rw-p 0020f000 08:01 1837752                    /usr/$
 7f87aca2d000-7f87acbf5000 rw-p 00000000 00:00 0
 7f87acbf5000-7f87acc5c000 r-xp 00000000 08:01 2234024                    /usr/$
 7f87addc3000-7f87addc8000 r-xp 00000000 08:01 1842515                    /usr/$
 7f87addc8000-7f87adfc7000 ---p 00005000 08:01 1842515                    /usr/$
 7f87adfc7000-7f87adfc8000 r--p 00004000 08:01 1842515                    /usr/$
 7f87adfc8000-7f87adfc9000 rw-p 00005000 08:01 1842515                    /usr/$
 7f87adfc9000-7f87adff6000 r-xp 00000000 08:01 2101192                    /usr/$
 7f87adff6000-7f87ae1f5000 ---p 0002d000 08:01 2101192                    /usr/$
 7f87ae1f5000-7f87ae1f6000 r--p 0002c000 08:01 2101192                    /usr/$
 7f87ae1f6000-7f87ae1f9000 rw-p 0002d000 08:01 2101192                    /usr/$
 7f87ae1f9000-7f87ae25f000 r-xp 00000000 08:01 2228670                    /usr/$
 7f87ae25f000-7f87ae45f000 ---p 00066000 08:01 2228670                    /usr/$
 7f87ae45f000-7f87ae460000 r--p 00066000 08:01 2228670                    /usr/$
 7f87ae460000-7f87ae463000 rw-p 00067000 08:01 2228670                    /usr/$
 7f87ae463000-7f87ae465000 rw-p 00000000 00:00 0
 7f87ae465000-7f87ae47a000 r-xp 00000000 08:01 2887147                    /lib/$
 7f87ae47a000-7f87ae679000 ---p 00015000 08:01 2887147                    /lib/$
 7f87ae679000-7f87ae67a000 r--p 00014000 08:01 2887147                    /lib/$
 7f87ae67a000-7f87ae67b000 rw-p 00015000 08:01 2887147                    /lib/$
 7f87ae67b000-7f87ae67e000 rw-p 00000000 00:00 0
 7f87ae67e000-7f87ae684000 r-xp 00000000 08:01 1842545                    /usr/$
7f87aed31000-7f87aed32000 rw-p 0009b000 08:01 1835371                    /usr/$
 7f87aed32000-7f87aed48000 r-xp 00000000 08:01 2887256                    /lib/$
 7f87aed48000-7f87aef47000 ---p 00016000 08:01 2887256                    /lib/$
 7f87aef47000-7f87aef48000 r--p 00015000 08:01 2887256                    /lib/$
 7f87aef48000-7f87aef49000 rw-p 00016000 08:01 2887256                    /lib/$
 7f87aef49000-7f87aef4c000 r-xp 00000000 08:01 2887153                    /lib/$
 7f87aef4c000-7f87af14b000 ---p 00003000 08:01 2887153                    /lib/$
 7f87af14b000-7f87af14c000 r--p 00002000 08:01 2887153                    /lib/$
 7f87af14c000-7f87af14d000 rw-p 00003000 08:01 2887153                    /lib/$
 7f87af14d000-7f87af302000 r-xp 00000000 08:01 2887122                    /lib/$
 7f87af302000-7f87af501000 ---p 001b5000 08:01 2887122                    /lib/$
 7f87af501000-7f87af505000 r--p 001b4000 08:01 2887122                    /lib/$
 7f87af505000-7f87af507000 rw-p 001b8000 08:01 2887122                    /lib/$
 7f87af507000-7f87af50c000 rw-p 00000000 00:00 0
 7f87af50c000-7f87af513000 r-xp 00000000 08:01 2887226                    /lib/$
 7f87af513000-7f87af712000 ---p 00007000 08:01 2887226                    /lib/$
 7f87af712000-7f87af713000 r--p 00006000 08:01 2887226                    /lib/$
 7f87af713000-7f87af714000 rw-p 00007000 08:01 2887226                    /lib/$
 7f87af714000-7f87af80f000 r-xp 00000000 08:01 2887164                    /lib/$
 7f87afa10000-7f87afa15000 r-xp 00000000 08:01 1842336                    /usr/$
 7f87afa15000-7f87afc14000 ---p 00005000 08:01 1842336                    /usr/$
 7f87afc14000-7f87afc15000 r--p 00004000 08:01 1842336                    /usr/$
 7f87afc15000-7f87afc16000 rw-p 00005000 08:01 1842336                    /usr/$
 7f87afc16000-7f87afc18000 r-xp 00000000 08:01 1842325                    /usr/$
 7f87afc18000-7f87afe18000 ---p 00002000 08:01 1842325                    /usr/$
 7f87afe18000-7f87afe19000 r--p 00002000 08:01 1842325                    /usr/$
 7f87afe19000-7f87afe1a000 rw-p 00003000 08:01 1842325                    /usr/$
 7f87afe1a000-7f87afe55000 r-xp 00000000 08:01 1837825                    /usr/$
 7f87afe55000-7f87b0054000 ---p 0003b000 08:01 1837825                    /usr/$
 7f87b0054000-7f87b0055000 r--p 0003a000 08:01 1837825                    /usr/$
 7f87b0055000-7f87b0057000 rw-p 0003b000 08:01 1837825                    /usr/$
 7f87b0057000-7f87b00d7000 r-xp 00000000 08:01 1842879                    /usr/$
 7f87b00d7000-7f87b02d6000 ---p 00080000 08:01 1842879                    /usr/$
 7f87b02d6000-7f87b02dc000 r--p 0007f000 08:01 1842879                    /usr/$
 7f87b02dc000-7f87b02dd000 rw-p 00085000 08:01 1842879                    /usr/$
 7f87b02dd000-7f87b02e7000 r-xp 00000000 08:01 1842509                    /usr/$
 7f87b04e9000-7f87b0501000 r-xp 00000000 08:01 2887218                    /lib/$
 7f87b0501000-7f87b0700000 ---p 00018000 08:01 2887218                    /lib/$
 7f87b0700000-7f87b0701000 r--p 00017000 08:01 2887218                    /lib/$
 7f87b0701000-7f87b0702000 rw-p 00018000 08:01 2887218                    /lib/$
 7f87b0702000-7f87b0706000 rw-p 00000000 00:00 0
 7f87b0706000-7f87b070e000 r-xp 00000000 08:01 1842873                    /usr/$
 7f87b070e000-7f87b090d000 ---p 00008000 08:01 1842873                    /usr/$
 7f87b090d000-7f87b090e000 r--p 00007000 08:01 1842873                    /usr/$
 7f87b090e000-7f87b090f000 rw-p 00008000 08:01 1842873                    /usr/$
 7f87b090f000-7f87b0911000 r-xp 00000000 08:01 2887137                    /lib/$
 7f87b0911000-7f87b0b11000 ---p 00002000 08:01 2887137                    /lib/$
 7f87b0b11000-7f87b0b12000 r--p 00002000 08:01 2887137                    /lib/$
 7f87b0b12000-7f87b0b13000 rw-p 00003000 08:01 2887137                    /lib/$
 7f87b0b13000-7f87b0b8d000 r-xp 00000000 08:01 2887149                    /lib/$
 7f87b0b8d000-7f87b0d8d000 ---p 0007a000 08:01 2887149                    /lib/$
 7f87b0d8d000-7f87b0d8e000 r--p 0007a000 08:01 2887149                    /lib/$
 7f87b0d8e000-7f87b0d91000 rw-p 0007b000 08:01 2887149                    /lib/$
7f87b0d9d000-7f87b0f9c000 ---p 0000c000 08:01 2887241                    /lib/$
 7f87b0f9c000-7f87b0f9d000 r--p 0000b000 08:01 2887241                    /lib/$
 7f87b0f9d000-7f87b0f9e000 rw-p 0000c000 08:01 2887241                    /lib/$
 7f87b0f9e000-7f87b0fc0000 r-xp 00000000 08:01 2887100                    /lib/$
 7f87b105c000-7f87b10bc000 rw-s 00000000 00:04 229377                     /SYSV$
 7f87b10bc000-7f87b111c000 rw-s 00000000 00:04 196608                     /SYSV$
 7f87b111c000-7f87b11ac000 rw-p 00000000 00:00 0
 7f87b11b7000-7f87b11bb000 rw-s 100549000 00:05 8789                      /dev/$
 7f87b11bb000-7f87b11bd000 rw-s 1b7ff000 00:05 8789                       /dev/$
 7f87b11bd000-7f87b11c0000 rw-p 00000000 00:00 0
 7f87b11c0000-7f87b11c1000 r--p 00022000 08:01 2887100                    /lib/$
 7f87b11c1000-7f87b11c3000 rw-p 00023000 08:01 2887100                    /lib/$
 7f87b11c3000-7f87b13dd000 r-xp 00000000 08:01 1840268                    /usr/$
 7f87b15dd000-7f87b15e0000 r--p 0021a000 08:01 1840268                    /usr/$
 7f87b15e0000-7f87b15ec000 rw-p 0021d000 08:01 1840268                    /usr/$
 7f87b15ec000-7f87b15fd000 rw-p 00000000 00:00 0
 7f87b1eef000-7f87b5a33000 rw-p 00000000 00:00 0                          [heap]
 7fff29696000-7fff296bb000 rw-p 00000000 00:00 0                          [stac$
 7fff296cc000-7fff296cd000 r-xp 00000000 00:00 0                          [vdso]
7f87b0d9d000-7f87b0f9c000 ---p 0000c000 08:01 2887241                    /lib/$
 7f87b0f9c000-7f87b0f9d000 r--p 0000b000 08:01 2887241                    /lib/$
 7f87b0f9d000-7f87b0f9e000 rw-p 0000c000 08:01 2887241                    /lib/$
 7f87b0f9e000-7f87b0fc0000 r-xp 00000000 08:01 2887100                    /lib/$
 7f87b105c000-7f87b10bc000 rw-s 00000000 00:04 229377                     /SYSV$
 7f87b10bc000-7f87b111c000 rw-s 00000000 00:04 196608                     /SYSV$
 7f87b111c000-7f87b11ac000 rw-p 00000000 00:00 0
 7f87b11b7000-7f87b11bb000 rw-s 100549000 00:05 8789                      /dev/$
 7f87b11bb000-7f87b11bd000 rw-s 1b7ff000 00:05 8789                       /dev/$
 7f87b11bd000-7f87b11c0000 rw-p 00000000 00:00 0
 7f87b11c0000-7f87b11c1000 r--p 00022000 08:01 2887100                    /lib/$
 7f87b11c1000-7f87b11c3000 rw-p 00023000 08:01 2887100                    /lib/$
 7f87b11c3000-7f87b13dd000 r-xp 00000000 08:01 1840268                    /usr/$
 7f87b15dd000-7f87b15e0000 r--p 0021a000 08:01 1840268                    /usr/$
 7f87b15e0000-7f87b15ec000 rw-p 0021d000 08:01 1840268                    /usr/$
 7f87b15ec000-7f87b15fd000 rw-p 00000000 00:00 0
 7f87b1eef000-7f87b5a33000 rw-p 00000000 00:00 0                          [heap]
 7fff29696000-7fff296bb000 rw-p 00000000 00:00 0                          [stac$
 7fff296cc000-7fff296cd000 r-xp 00000000 00:00 0                          [vdso]
ProcStatus:
 Name:  Xorg
 State: S (sleeping)
 Tgid:  3651
 Pid:   3651
 PPid:  1097
 TracerPid:     0
 Uid:   0       0       0       0
 Gid:   0       0       0       0
 FDSize:        64
 Groups:
 VmPeak:          232300 kB
 VmSize:          222608 kB
 VmLck:        0 kB
 VmPin:        0 kB
 VmHWM:    83072 kB
 VmRSS:    80508 kB
 VmData:          102364 kB
 VmStk:      152 kB
VmExe:     2152 kB
 VmLib:    32604 kB
 VmPTE:      408 kB
 VmSwap:               0 kB
 Threads:       5
 SigQ:  1/30978
 SigPnd:        0000000000000000
 ShdPnd:        0000000000002000
 SigBlk:        000000001a392400
 SigIgn:        0000000010001000
SigCgt:        00000001c18066cf
 CapInh:        0000000000000000
 CapPrm:        ffffffffffffffff
 CapEff:        ffffffffffffffff
 CapBnd:        ffffffffffffffff
 Cpus_allowed:  f
 Cpus_allowed_list:     0-3
 Mems_allowed:  00000000,00000001
 Mems_allowed_list:     0
 voluntary_ctxt_switches:       74622
 nonvoluntary_ctxt_switches:    1930
Signal: 6
Uname: Linux 3.5.0-26-generic x86_64
UserGroups:
CoreDump: base64
 H4sICAAAAAAC/0NvcmVEdW1wAA==
 7N1/bKR5fR/wuTvAoJTzRkKZ0CDNJoJOkpbOBohMURVvSzlDSrAbqIyiNt6UpAYF8HJ34P5VtlJVHy$
 2bsX+KjKO+HjIShxtWXc3a7jvtvtpHtx3G7ruHVfI9u+79gWiNZLvFRCX3eJViVqqbHAEtrtUipKWo$
 2YMDAQAAAAAg/9dGUFVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVVV$
 Ycd+QqIK4gAAu3aTkCUzgv4ReQg8FEndoi2hIjO18hZYUCSEIHQIpHDrUKYFHqIFifASqRRaYNRBW+$















```

Theres my crash file. Its a bunch of gibberish for the coredump and it takes forever to load so I left the rest out. I hope this helps. If you guys need anything else I'll try and get it.

---

### Post by Alake28 on 2013-04-04
Bump

---

### Post by Slim Odds on 2013-04-04
I'd try running a memory test.

I have a very similar motherboard (maybe even the same one) with a Phenom II 955 3.2 GHz. I was using a GeForce GT 9600 but have since switched to the motherboards GeForce 8300. I have no problems whatsoever.

---

### Post by pfeiffep on 2013-04-04
I had problems with **Linux 3.5.0-26-generic x86_64** and reverted back to **-24-generic** ... after that everything was fine.

Certainly my solution was pragmatic :) but not so elegant

---

