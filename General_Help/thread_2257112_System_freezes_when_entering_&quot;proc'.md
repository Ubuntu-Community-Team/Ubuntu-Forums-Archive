---
title: "System freezes when entering &quot;/proc'"
date: 2014-12-17
forum: General Help
---

### Post by DGINSD on 2014-12-17
This is really driving me crazy, if I pull up nautilus and navigate to /proc, my system will completely freeze up.  The only way to get out seems to be to SysReq RSEINUB.  This happens even if I gksudo nautilus, I even created another user and I get the same thing. If I open up a shell and navigate there; no problems, same with using MC; no problem. I reinstalled nautilus and reinstalled the kernel; no dice. I don't even know what to provide as clues, as I cant find anything that seems significant in the logs, I really don't want to reinstall the whole system but I'm at an end here? Any help or sugestions appreciated.

---

### Post by DGINSD on 2014-12-18
So I purposely entered /proc using Nautilus last night so I could look through the logs before the crash. I did see this was a bit interesting the system crashed almose exactly at 9:00pm on the 17th but as soon as I started the recovery ([COLOR=#000000]SysReq RSEINUB) the times in the logs got all screwy, jumped forward about 8 hours, for the record I recovered the system no more than 5 min. after the crash.

[/COLOR]> Dec 17 21:01:07 HP-G6 kernel: [  444.764720]  [<ffffffff815d38b9>] cpuidle_idle_call+0xb9/0x1f0Dec 17 21:01:07 HP-G6 kernel: [  444.764729]  [<ffffffff8101d35e>] arch_cpu_idle+0xe/0x30
Dec 17 21:01:07 HP-G6 kernel: [  444.764736]  [<ffffffff810bef35>] cpu_startup_entry+0xc5/0x290
Dec 17 21:01:07 HP-G6 kernel: [  444.764745]  [<ffffffff8170f247>] rest_init+0x77/0x80
Dec 17 21:01:07 HP-G6 kernel: [  444.764753]  [<ffffffff81d35f70>] start_kernel+0x438/0x443
Dec 17 21:01:07 HP-G6 kernel: [  444.764760]  [<ffffffff81d35941>] ? repair_env_string+0x5c/0x5c
Dec 17 21:01:07 HP-G6 kernel: [  444.764767]  [<ffffffff81d35120>] ? early_idt_handlers+0x120/0x120
Dec 17 21:01:07 HP-G6 kernel: [  444.764774]  [<ffffffff81d355ee>] x86_64_start_reservations+0x2a/0x2c
Dec 17 21:01:07 HP-G6 kernel: [  444.764781]  [<ffffffff81d35733>] x86_64_start_kernel+0x143/0x152
Dec 17 21:01:07 HP-G6 kernel: [  444.764784] Code: ff fa 66 66 90 66 66 90 5d c3 8a 47 08 55 48 89 e5 3c 01 75 07 e8 ec 52 c2 ff eb 17 3c 02 75 07 e8 ba ff ff ff eb 0c 8b 57 04 ec <48> 8b 15 a8 82 ba 00 ed 5d c3 66 66 66 66 90 55 48 63 c2 48 8d 
[COLOR=#ff0000]**&#8203;Heres the break in time this is a piece of syslog, this line in the log was blank.**[/COLOR]

Dec 18 05:03:41 HP-G6 rsyslogd: rsyslogd's groupid changed to 104
Dec 18 05:03:41 HP-G6 rsyslogd: rsyslogd's userid changed to 101
Dec 18 05:03:41 HP-G6 kernel: [    0.000000] Initializing cgroup subsys cpuset
Dec 18 05:03:41 HP-G6 kernel: [    0.000000] Initializing cgroup subsys cpu
Dec 18 05:03:41 HP-G6 kernel: [    0.000000] Initializing cgroup subsys cpuacct
Dec 18 05:03:41 HP-G6 kernel: [    0.000000] Linux version 3.13.0-44-generic (buildd@lamiak) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #73-Ubuntu SMP Tue Dec 16 00:22:43 UTC 2014 (Ubuntu 3.13.0-44.73-generic 3.13.11-ckt12)
Dec 18 05:03:41 HP-G6 kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.13.0-44-generic root=UUID=5735cf93-f3ed-4a55-803e-f4d111b5cbec ro quiet splash
Dec 18 05:03:41 HP-G6 kernel: [    0.000000] KERNEL supported cpus:
Dec 18 05:03:41 HP-G6 kernel: [    0.000000]   Intel GenuineIntel
Dec 18 05:03:41 HP-G6 kernel: [    0.000000]   AMD AuthenticAMD




I also installed another gui file manager (dolphin) to see if the problem happened with another program. Dolphin worked just fine I could navigate to /proc without the system crashing, this would leave me to believe the problem lay with Nautilus, but I've already tried removing and re-installing. is there another way to say reset Nautilus?

---

### Post by nerdtron on 2014-12-18
maybe a filename error somewhere in /proc.
Let's see..
```
 ls -lah /proc
```

---

### Post by DGINSD on 2014-12-18
Ok heres the output of ** ls -lah /proc,** didn't see anything odd but not really sure what it should look like.

```

@HP-G6:~$ ls -lah /proctotal 4.0K
dr-xr-xr-x 240 root       root          0 Dec 17 23:28 .
drwxr-xr-x  26 root       root       4.0K Dec 18 07:23 ..
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 10
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1021
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1052
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1058
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1061
dr-xr-xr-x   9 daemon     daemon        0 Dec 18 07:29 1062
dr-xr-xr-x   9 whoopsie   whoopsie      0 Dec 18 07:29 1072
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 11
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1128
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 12
dr-xr-xr-x   9 colord     colord        0 Dec 18 07:29 1234
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1243
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1246
dr-xr-xr-x   9 kernoops   adm           0 Dec 18 07:29 1278
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 128
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 129
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1296
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 13
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1310
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1319
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 132
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1322
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1345
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 14
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1417
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1419
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1434
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1446
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1449
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1462
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1464
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1465
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1466
dr-xr-xr-x   9 nobody     dip           0 Dec 18 07:29 1471
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 15
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 151
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 152
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 16
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1606
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1614
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1619
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1631
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1682
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 17
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 1721
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 18
dr-xr-xr-x   9 rtkit      rtkit         0 Dec 18 07:29 1802
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 19
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 2
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 20
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2010
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2012
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 21
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2103
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2112
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2119
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2136
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2137
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2138
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2145
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2161
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2162
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2166
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2169
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2170
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2175
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2176
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2180
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2185
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2189
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2192
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2194
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2197
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 22
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2230
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2235
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2238
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2250
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2265
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2280
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 23
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2312
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2313
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2316
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2320
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2325
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2326
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2328
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2331
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2337
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2351
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2352
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2353
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2359
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2361
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2366
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2389
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2391
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 24
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2469
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 2477
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 25
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2511
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2533
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2538
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2548
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2552
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2558
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2562
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2567
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2583
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2588
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2594
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 26
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 27
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2707
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2710
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 275
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 28
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2809
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2817
dr-xr-xr-x   9 root       root          0 Dec 18 07:28 282
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2821
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2828
dr-xr-xr-x   9 david      david         0 Dec 18 07:29 2856
dr-xr-xr-x   9 david      david         0 Dec 18 07:30 2893
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 29
dr-xr-xr-x   9 david      david         0 Dec 18 07:30 2920
dr-xr-xr-x   9 david      david         0 Dec 18 07:30 2928
dr-xr-xr-x   9 david      david         0 Dec 18 07:30 2933
dr-xr-xr-x   9 root       root          0 Dec 18 07:30 2965
dr-xr-xr-x   9 david      david         0 Dec 18 07:30 2974
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 3
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 30
dr-xr-xr-x   9 david      david         0 Dec 18 07:31 3018
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 31
dr-xr-xr-x   9 david      david         0 Dec 18 07:32 3104
dr-xr-xr-x   9 root       root          0 Dec 18 07:32 3105
dr-xr-xr-x   9 david      david         0 Dec 18 07:33 3175
dr-xr-xr-x   9 david      david         0 Dec 18 07:34 3191
dr-xr-xr-x   9 david      david         0 Dec 18 07:34 3192
dr-xr-xr-x   9 david      david         0 Dec 18 07:34 3197
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 32
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 323
dr-xr-xr-x   9 david      david         0 Dec 18 07:34 3286
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 33
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 34
dr-xr-xr-x   9 root       utmp          0 Dec 18 07:34 3441
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 35
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 38
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 381
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 39
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 40
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 41
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 42
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 43
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 44
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 45
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 5
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 520
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 521
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 535
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 537
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 559
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 560
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 57
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 589
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 592
dr-xr-xr-x   9 root       root          0 Dec 18 13:12 6233
dr-xr-xr-x   9 root       root          0 Dec 18 14:07 6650
dr-xr-xr-x   9 root       root          0 Dec 18 14:10 6676
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 676
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 698
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 699
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 7
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 743
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 77
dr-xr-xr-x   9 messagebus messagebus    0 Dec 18 07:29 773
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 78
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 8
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 803
dr-xr-xr-x   9 syslog     syslog        0 Dec 18 07:29 818
dr-xr-xr-x   9 root       root          0 Dec 18 17:05 8202
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 846
dr-xr-xr-x   9 root       root          0 Dec 18 17:34 8464
dr-xr-xr-x   9 avahi      avahi         0 Dec 18 07:29 853
dr-xr-xr-x   9 avahi      avahi         0 Dec 18 07:29 855
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 863
dr-xr-xr-x   9 root       root          0 Dec 18 18:00 8661
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8674
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8683
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8684
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8686
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8689
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8693
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8694
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8696
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8716
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8723
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8772
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8805
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 881
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8812
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8844
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8848
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8862
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8871
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8890
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 890
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8901
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8927
dr-xr-xr-x   9 david      david         0 Dec 18 18:01 8955
dr-xr-xr-x   9 root       root          0 Dec 18 18:01 8967
dr-xr-xr-x   9 david      david         0 Dec 18 18:02 8987
dr-xr-xr-x   9 david      utmp          0 Dec 18 18:02 8994
dr-xr-xr-x   9 david      david         0 Dec 18 18:02 8995
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 9
dr-xr-xr-x   9 david      david         0 Dec 18 18:02 9053
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 965
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 968
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 972
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 980
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 981
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 984
dr-xr-xr-x   9 root       root          0 Dec 18 07:29 987
dr-xr-xr-x   5 root       root          0 Dec 18 18:02 acpi
dr-xr-xr-x   5 root       root          0 Dec 18 18:02 asound
dr-xr-xr-x   4 root       root          0 Dec 18 18:02 ati
-rw-r--r--   1 root       root          0 Dec 18 18:02 brcm_monitor0
-r--r--r--   1 root       root          0 Dec 18 18:02 buddyinfo
dr-xr-xr-x   4 root       root          0 Dec 18 07:29 bus
-r--r--r--   1 root       root          0 Dec 18 18:02 cgroups
-r--r--r--   1 root       root          0 Dec 18 18:02 cmdline
-r--r--r--   1 root       root          0 Dec 18 18:02 consoles
-r--r--r--   1 root       root          0 Dec 18 18:02 cpuinfo
-r--r--r--   1 root       root          0 Dec 18 18:02 crypto
-r--r--r--   1 root       root          0 Dec 18 18:02 devices
-r--r--r--   1 root       root          0 Dec 18 18:02 diskstats
-r--r--r--   1 root       root          0 Dec 18 18:02 dma
dr-xr-xr-x   2 root       root          0 Dec 18 18:02 driver
-r--r--r--   1 root       root          0 Dec 18 18:02 execdomains
-r--r--r--   1 root       root          0 Dec 18 18:02 fb
-r--r--r--   1 root       root          0 Dec 18 18:02 filesystems
dr-xr-xr-x   5 root       root          0 Dec 18 18:02 fs
-r--r--r--   1 root       root          0 Dec 18 18:02 interrupts
-r--r--r--   1 root       root          0 Dec 18 18:02 iomem
-r--r--r--   1 root       root          0 Dec 18 18:02 ioports
dr-xr-xr-x   2 root       root          0 Dec 18 18:02 ipmi
dr-xr-xr-x  27 root       root          0 Dec 18 18:02 irq
-r--r--r--   1 root       root          0 Dec 18 18:02 kallsyms
-r--------   1 root       root       128T Dec 18 18:02 kcore
-r--r--r--   1 root       root          0 Dec 18 18:02 keys
-r--r--r--   1 root       root          0 Dec 18 18:02 key-users
-r--------   1 root       root          0 Dec 18 07:29 kmsg
-r--------   1 root       root          0 Dec 18 18:02 kpagecount
-r--------   1 root       root          0 Dec 18 18:02 kpageflags
-rw-r--r--   1 root       root          0 Dec 18 18:02 latency_stats
-r--r--r--   1 root       root          0 Dec 18 18:02 loadavg
-r--r--r--   1 root       root          0 Dec 18 18:02 locks
-r--r--r--   1 root       root          0 Dec 18 18:02 mdstat
-r--r--r--   1 root       root          0 Dec 18 18:02 meminfo
-r--r--r--   1 root       root          0 Dec 18 18:02 misc
-r--r--r--   1 root       root          0 Dec 18 18:02 modules
lrwxrwxrwx   1 root       root         11 Dec 18 18:02 mounts -> self/mounts
-rw-r--r--   1 root       root          0 Dec 18 07:29 mtrr
lrwxrwxrwx   1 root       root          8 Dec 18 18:02 net -> self/net
-r--r--r--   1 root       root          0 Dec 18 18:02 pagetypeinfo
-r--r--r--   1 root       root          0 Dec 18 18:02 partitions
-r--r--r--   1 root       root          0 Dec 18 18:02 sched_debug
-r--r--r--   1 root       root          0 Dec 18 18:02 schedstat
dr-xr-xr-x   3 root       root          0 Dec 18 18:02 scsi
lrwxrwxrwx   1 root       root          0 Dec 17 23:28 self -> 9053
-r--------   1 root       root          0 Dec 18 18:02 slabinfo
-r--r--r--   1 root       root          0 Dec 18 18:02 softirqs
-r--r--r--   1 root       root          0 Dec 18 18:02 stat
-r--r--r--   1 root       root          0 Dec 18 07:29 swaps
dr-xr-xr-x   1 root       root          0 Dec 17 23:28 sys
--w-------   1 root       root          0 Dec 18 18:02 sysrq-trigger
dr-xr-xr-x   2 root       root          0 Dec 18 18:02 sysvipc
-r--r--r--   1 root       root          0 Dec 18 18:02 timer_list
-rw-r--r--   1 root       root          0 Dec 18 18:02 timer_stats
dr-xr-xr-x   4 root       root          0 Dec 18 18:02 tty
-r--r--r--   1 root       root          0 Dec 18 18:02 uptime
-r--r--r--   1 root       root          0 Dec 18 18:02 version
-r--r--r--   1 root       root          0 Dec 18 18:02 version_signature
-r--------   1 root       root          0 Dec 18 18:02 vmallocinfo
-r--r--r--   1 root       root          0 Dec 18 18:02 vmstat
-r--r--r--   1 root       root          0 Dec 18 18:02 zoneinfo



```

---

### Post by nerdtron on 2014-12-19
Hhmm...similar to mine nothing.. nothing out of the ordinary. and it's really puzzling that it only happens on nautilus and not on other file managers.

---

### Post by DGINSD on 2014-12-19
Yeah it seemed OK to me as well, I actually installed a patched version of nemo this morning, and navigating to /proc did cause a freeze, so it's something to do with the base functionality of Nautilus. I'm going to try purging and reinstalling Nautilus Nemo and their dependencies tonight and see if that fixes it beyond that looks like a reinstall. This has got to be the strangest problem I've ever encountered since using Ubuntu.

---

