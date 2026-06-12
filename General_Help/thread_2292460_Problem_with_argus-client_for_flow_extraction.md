---
title: "Problem with argus-client for flow extraction"
date: 2015-08-28
forum: General Help
---

### Post by almehrdad on 2015-08-28
hello friend 
How can I solve my problem????????



```
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78c4e)[0x7fa3643f2c4e]
/lib/x86_64-linux-gnu/libc.so.6(__fortify_fail+0x5c)[0x7fa364492e8c]
/lib/x86_64-linux-gnu/libc.so.6(+0x116e80)[0x7fa364490e80]
argus[0x409a62]
/usr/lib/x86_64-linux-gnu/libpcap.so.0.8(+0x1e014)[0x7fa364a6a014]
argus[0x40a792]
argus[0x4033f7]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0)[0x7fa36439aa40]
argus[0x4036dd]
======= Memory map: ========
00400000-00429000 r-xp 00000000 fc:01 24251046                           /usr/sbin/argus_linux
00628000-00629000 r--p 00028000 fc:01 24251046                           /usr/sbin/argus_linux
00629000-0062b000 rw-p 00029000 fc:01 24251046                           /usr/sbin/argus_linux
0062b000-0079a000 rw-p 00000000 00:00 0 
011c3000-01206000 rw-p 00000000 00:00 0                                  [heap]
7fa363d3d000-7fa363d53000 r-xp 00000000 fc:01 2494634                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7fa363d53000-7fa363f52000 ---p 00016000 fc:01 2494634                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7fa363f52000-7fa363f53000 rw-p 00015000 fc:01 2494634                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7fa363f53000-7fa363f5f000 r-xp 00000000 fc:01 2494691                    /lib/x86_64-linux-gnu/libnss_files-2.21.so
7fa363f5f000-7fa36415e000 ---p 0000c000 fc:01 2494691                    /lib/x86_64-linux-gnu/libnss_files-2.21.so
7fa36415e000-7fa36415f000 r--p 0000b000 fc:01 2494691                    /lib/x86_64-linux-gnu/libnss_files-2.21.so
7fa36415f000-7fa364160000 rw-p 0000c000 fc:01 2494691                    /lib/x86_64-linux-gnu/libnss_files-2.21.so
7fa364160000-7fa364177000 r-xp 00000000 fc:01 2494685                    /lib/x86_64-linux-gnu/libnsl-2.21.so
7fa364177000-7fa364376000 ---p 00017000 fc:01 2494685                    /lib/x86_64-linux-gnu/libnsl-2.21.so
7fa364376000-7fa364377000 r--p 00016000 fc:01 2494685                    /lib/x86_64-linux-gnu/libnsl-2.21.so
7fa364377000-7fa364378000 rw-p 00017000 fc:01 2494685                    /lib/x86_64-linux-gnu/libnsl-2.21.so
7fa364378000-7fa36437a000 rw-p 00000000 00:00 0 
7fa36437a000-7fa36453a000 r-xp 00000000 fc:01 2494605                    /lib/x86_64-linux-gnu/libc-2.21.so
7fa36453a000-7fa36473a000 ---p 001c0000 fc:01 2494605                    /lib/x86_64-linux-gnu/libc-2.21.so
7fa36473a000-7fa36473e000 r--p 001c0000 fc:01 2494605                    /lib/x86_64-linux-gnu/libc-2.21.so
7fa36473e000-7fa364740000 rw-p 001c4000 fc:01 2494605                    /lib/x86_64-linux-gnu/libc-2.21.so
7fa364740000-7fa364744000 rw-p 00000000 00:00 0 
7fa364744000-7fa36484b000 r-xp 00000000 fc:01 2494664                    /lib/x86_64-linux-gnu/libm-2.21.so
7fa36484b000-7fa364a4a000 ---p 00107000 fc:01 2494664                    /lib/x86_64-linux-gnu/libm-2.21.so
7fa364a4a000-7fa364a4b000 r--p 00106000 fc:01 2494664                    /lib/x86_64-linux-gnu/libm-2.21.so
7fa364a4b000-7fa364a4c000 rw-p 00107000 fc:01 2494664                    /lib/x86_64-linux-gnu/libm-2.21.so
7fa364a4c000-7fa364a89000 r-xp 00000000 fc:01 24257237                   /usr/lib/x86_64-linux-gnu/libpcap.so.1.6.2
7fa364a89000-7fa364c88000 ---p 0003d000 fc:01 24257237                   /usr/lib/x86_64-linux-gnu/libpcap.so.1.6.2
7fa364c88000-7fa364c8a000 r--p 0003c000 fc:01 24257237                   /usr/lib/x86_64-linux-gnu/libpcap.so.1.6.2
7fa364c8a000-7fa364c8b000 rw-p 0003e000 fc:01 24257237                   /usr/lib/x86_64-linux-gnu/libpcap.so.1.6.2
7fa364c8b000-7fa364c8c000 rw-p 00000000 00:00 0 
7fa364c8c000-7fa364c94000 r-xp 00000000 fc:01 2494776                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7fa364c94000-7fa364e93000 ---p 00008000 fc:01 2494776                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7fa364e93000-7fa364e94000 r--p 00007000 fc:01 2494776                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7fa364e94000-7fa364e95000 rw-p 00008000 fc:01 2494776                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7fa364e95000-7fa364e96000 rw-p 00000000 00:00 0 
7fa364e96000-7fa364eba000 r-xp 00000000 fc:01 2494577                    /lib/x86_64-linux-gnu/ld-2.21.so
7fa36501a000-7fa36509f000 rw-p 00000000 00:00 0 
7fa3650b4000-7fa3650b9000 rw-p 00000000 00:00 0 
7fa3650b9000-7fa3650ba000 r--p 00023000 fc:01 2494577                    /lib/x86_64-linux-gnu/ld-2.21.so
7fa3650ba000-7fa3650bb000 rw-p 00024000 fc:01 2494577                    /lib/x86_64-linux-gnu/ld-2.21.so
7fa3650bb000-7fa3650bc000 rw-p 00000000 00:00 0 
7ffe83019000-7ffe8303a000 rw-p 00000000 00:00 0                          [stack]
7ffe83120000-7ffe83122000 r--p 00000000 00:00 0                          [vvar]
7ffe83122000-7ffe83124000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
```

---

### Post by TheFu on 2015-08-28
Perhaps if you explain a little what is running, what you are trying to do, which version of Ubuntu is being used and the kernel?

Perhaps?  Plus anything else you think someone would need to know.

---

### Post by almehrdad on 2015-08-28
yes of courrse.
i use argus-client for flow extraction.

When executing a command argus-client for use of this work was to this error. and stoped my work.
i am use ubuntu 15.04

my instruct :
argus -r bot.pcap -w - | ra -s bytes,sbytes,dbytes,pkts, spkts,dpkts,dir,status.

---

### Post by dino99 on 2015-08-28
run 'journalctl to get the errors flow, and glance at the errors
maybe you can run argus with dbg symbol; and/or run it with less paramaters at once to know if it matters (maybe glace at the man page too)

---

### Post by Bucky Ball on 2015-08-28
Using a descriptive thread title gets you off to a good start when looking for support. I have changed this one. I have also added code tags for your output in the first post. See my signature for how to use them and also tips for effective posting to increase your chances of getting support. Good luck. :)

---

### Post by almehrdad on 2015-08-29
I still did not answer my question.

This command works great on other files.
 But questions have taken on this file.
 And its features are extracted.
 Where is the problem? This error on my system?
Nobody knows the answer to my problem?

The first line of the error message was Bold. please solve my problem.

```
*** buffer overflow detected ***: argus terminated
======= Backtrace: =========
/lib/x86_64-linux-gnu/libc.so.6(+0x78c4e)[0x7f40ebff2c4e]
/lib/x86_64-linux-gnu/libc.so.6(__fortify_fail+0x5c)[0x7f40ec092e8c]
/lib/x86_64-linux-gnu/libc.so.6(+0x116e80)[0x7f40ec090e80]
argus[0x409a62]
/usr/lib/x86_64-linux-gnu/libpcap.so.0.8(+0x1e014)[0x7f40ec66a014]
argus[0x40a792]
argus[0x4033f7]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0)[0x7f40ebf9aa40]
argus[0x4036dd]
======= Memory map: ========
00400000-00429000 r-xp 00000000 fc:01 24251046                           /usr/sbin/argus_linux
00628000-00629000 r--p 00028000 fc:01 24251046                           /usr/sbin/argus_linux
00629000-0062b000 rw-p 00029000 fc:01 24251046                           /usr/sbin/argus_linux
0062b000-0079a000 rw-p 00000000 00:00 0 
02547000-02568000 rw-p 00000000 00:00 0                                  [heap]
7f40eb93d000-7f40eb953000 r-xp 00000000 fc:01 2494634                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f40eb953000-7f40ebb52000 ---p 00016000 fc:01 2494634                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f40ebb52000-7f40ebb53000 rw-p 00015000 fc:01 2494634                    /lib/x86_64-linux-gnu/libgcc_s.so.1
7f40ebb53000-7f40ebb5f000 r-xp 00000000 fc:01 2494691                    /lib/x86_64-linux-gnu/libnss_files-2.21.so
7f40ebb5f000-7f40ebd5e000 ---p 0000c000 fc:01 2494691                    /lib/x86_64-linux-gnu/libnss_files-2.21.so
7f40ebd5e000-7f40ebd5f000 r--p 0000b000 fc:01 2494691                    /lib/x86_64-linux-gnu/libnss_files-2.21.so
7f40ebd5f000-7f40ebd60000 rw-p 0000c000 fc:01 2494691                    /lib/x86_64-linux-gnu/libnss_files-2.21.so
7f40ebd60000-7f40ebd77000 r-xp 00000000 fc:01 2494685                    /lib/x86_64-linux-gnu/libnsl-2.21.so
7f40ebd77000-7f40ebf76000 ---p 00017000 fc:01 2494685                    /lib/x86_64-linux-gnu/libnsl-2.21.so
7f40ebf76000-7f40ebf77000 r--p 00016000 fc:01 2494685                    /lib/x86_64-linux-gnu/libnsl-2.21.so
7f40ebf77000-7f40ebf78000 rw-p 00017000 fc:01 2494685                    /lib/x86_64-linux-gnu/libnsl-2.21.so
7f40ebf78000-7f40ebf7a000 rw-p 00000000 00:00 0 
7f40ebf7a000-7f40ec13a000 r-xp 00000000 fc:01 2494605                    /lib/x86_64-linux-gnu/libc-2.21.so
7f40ec13a000-7f40ec33a000 ---p 001c0000 fc:01 2494605                    /lib/x86_64-linux-gnu/libc-2.21.so
7f40ec33a000-7f40ec33e000 r--p 001c0000 fc:01 2494605                    /lib/x86_64-linux-gnu/libc-2.21.so
7f40ec33e000-7f40ec340000 rw-p 001c4000 fc:01 2494605                    /lib/x86_64-linux-gnu/libc-2.21.so
7f40ec340000-7f40ec344000 rw-p 00000000 00:00 0 
7f40ec344000-7f40ec44b000 r-xp 00000000 fc:01 2494664                    /lib/x86_64-linux-gnu/libm-2.21.so
7f40ec44b000-7f40ec64a000 ---p 00107000 fc:01 2494664                    /lib/x86_64-linux-gnu/libm-2.21.so
7f40ec64a000-7f40ec64b000 r--p 00106000 fc:01 2494664                    /lib/x86_64-linux-gnu/libm-2.21.so
7f40ec64b000-7f40ec64c000 rw-p 00107000 fc:01 2494664                    /lib/x86_64-linux-gnu/libm-2.21.so
7f40ec64c000-7f40ec689000 r-xp 00000000 fc:01 24257237                   /usr/lib/x86_64-linux-gnu/libpcap.so.1.6.2
7f40ec689000-7f40ec888000 ---p 0003d000 fc:01 24257237                   /usr/lib/x86_64-linux-gnu/libpcap.so.1.6.2
7f40ec888000-7f40ec88a000 r--p 0003c000 fc:01 24257237                   /usr/lib/x86_64-linux-gnu/libpcap.so.1.6.2
7f40ec88a000-7f40ec88b000 rw-p 0003e000 fc:01 24257237                   /usr/lib/x86_64-linux-gnu/libpcap.so.1.6.2
7f40ec88b000-7f40ec88c000 rw-p 00000000 00:00 0 
7f40ec88c000-7f40ec894000 r-xp 00000000 fc:01 2494776                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f40ec894000-7f40eca93000 ---p 00008000 fc:01 2494776                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f40eca93000-7f40eca94000 r--p 00007000 fc:01 2494776                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f40eca94000-7f40eca95000 rw-p 00008000 fc:01 2494776                    /lib/x86_64-linux-gnu/libwrap.so.0.7.6
7f40eca95000-7f40eca96000 rw-p 00000000 00:00 0 
7f40eca96000-7f40ecaba000 r-xp 00000000 fc:01 2494577                    /lib/x86_64-linux-gnu/ld-2.21.so
7f40ecc1a000-7f40ecc9f000 rw-p 00000000 00:00 0 
7f40eccb4000-7f40eccb9000 rw-p 00000000 00:00 0 
7f40eccb9000-7f40eccba000 r--p 00023000 fc:01 2494577                    /lib/x86_64-linux-gnu/ld-2.21.so
7f40eccba000-7f40eccbb000 rw-p 00024000 fc:01 2494577                    /lib/x86_64-linux-gnu/ld-2.21.so
7f40eccbb000-7f40eccbc000 rw-p 00000000 00:00 0 
7ffc3720d000-7ffc3722e000 rw-p 00000000 00:00 0                          [stack]
7ffc37318000-7ffc3731a000 r--p 00000000 00:00 0                          [vvar]
7ffc3731a000-7ffc3731c000 r-xp 00000000 00:00 0                          [vdso]
ffffffffff600000-ffffffffff601000 r-xp 00000000 00:00 0                  [vsyscall]
08-29-15 11:10:14.724803 08-29-15 11:10:14.730002        0.005199        0.005199                            1  man  v2.0      0          0
```

---

### Post by Bucky Ball on 2015-08-29
Please wait at least 12 hours before bumping threads. Thanks. And I asked you previously and showed you how: Please use code tags for your output. See the last link in my signature for how. Thanks.

---

### Post by almehrdad on 2015-08-29
in ubuntu 15.04  i use argus- client tool for extraction flow.
i use this command 
argus -r botng.pcapng -w - | ra -s startime, lasttime, count, dur, avgdur,saddr, daddr, proto, sport, dport,stos,dtos,bytes,sbytes,dbytes,pkts, spkts,dpkts,dir,status
 
This command works properly on the another pcapfile.But on this Pcap file has errors. 
Is the problem file?
 Ubuntu is the problem?

---

### Post by cariboo on 2015-08-29
Your error message pretty well tells you what happened:

> *** buffer overflow detected ***: argus terminated

I'd suggest there is something wrong with the file you are trying to open.

---

### Post by almehrdad on 2015-08-29
cariboo 
  
thank you . but one question?

The same command for another changelog file matches the on the same system works properly.
 Why on this file has errors?
 How do I fix the error?
Why command this tool error is only on this file?

please help

---

