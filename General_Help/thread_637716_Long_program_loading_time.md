---
title: "Long program loading time"
date: 2007-12-11
forum: General Help
---

### Post by ensis2k on 2007-12-11
Hello,

starting some programs, takes very long time. Also my Firefox halts for nearly a minute when I open some pages with a lot of Java content.
Which is confusing to me since not all Java pages open slowly and not all the programs start slowly.

Here is a strace of gedit. Only one of the system calls took very long time to execute:

```
     0.000094 mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2ba93eae2000
     0.000059 read(11, "\0\4XSMP\0\0\0\37local/apfel:/tmp/.ICE-"..., 4096) = 1694
     0.000082 close(11)                 = 0
     0.000053 munmap(0x2ba93eae2000, 4096) = 0
     0.000059 write(10, "\0\4\1\0\3\0\0\0\20\0\0\0\0\0\0\0tG\f\220\325\36g\345\376"..., 32) = 32
     0.000081 read(10, "\0\10\0\1\3\0\0\0", 8) = 8
     0.000063 read(10, "\7\0GnomeSM\0001.\6\0002.20.0\0\0\0\0", 24) = 24
     0.000097 write(10, "\1\1\1\0\1\0\0\0\0\0\0\0\0\0\0\0", 16) = 16
     0.000087 read(10, "\1\2\0\1\6\0\0\0", 8) = 8
    40.009535 read(10, "%\0\0\000101d63d6f9000119738255200000"..., 48) = 48
     0.000186 write(10, "\1\f\1\0\t\0\0\0\1\0\0\0\251+\0\0\20\0\0\0CurrentDirec"..., 80) = 80
     0.000119 write(10, "\1\f\1\0\10\0\0\0\1\0\0\0\251+\0\0\t\0\0\0ProcessIDrec"..., 72) = 72
     0.000090 write(10, "\1\f\1\0\10\0\0\0\1\0\0\0\251+\0\0\7\0\0\0ProgramIDrec"..., 72) = 72
     0.000095 write(10, "\1\f\1\0\10\0\0\0\1\0\0\0\251+\0\0\f\0\0\0CloneCommand"..., 72) = 72
     0.000113 write(10, "\1\f\1\0\25\0\0\0\1\0\0\0\251+\0\0\16\0\0\0RestartComm"..., 176) = 176
     0.000150 write(10, "\1\f\1\0\10\0\0\0\1\0\0\0\251+\0\0\6\0\0\0UserIDtComma"..., 72) = 72
     0.000124 write(3, "\233\2\4\0\1\0`\2\355\0\0\0\7\0\0\0\20\0\5\0\f\0\0\0SM"..., 36) = 36
     0.000087 read(3, 0x7fff775c0170, 32) = -1 EAGAIN (Resource temporarily unavailable)
     0.000071 poll([{fd=3, events=POLLIN, revents=POLLIN}], 1, -1) = 1
```


System specs:
64bit Dual Core AMD 4200+
2gb memory
Plenty of free disk space on all the partitions
Ubuntu 64bit version wich has the latest updates installed
Gnome Desktop


Regards,
Yelve Yakut

---

### Post by ken_vh on 2007-12-11
If I read this correctly, it took 40 seconds to read only 48 bytes ...
If that's true, I'd say your harddisk is broken(assuming that you're reading these files from a HDD). Try to see if any S.M.A.R.T. (hdd diagnose info) info tool tells you anything more about errors.

[edit] It could of course also a raid/sata driver problem.

---

### Post by ensis2k on 2007-12-11
Thank you for the suggestion but i couldnt find errors. Any other ideas?

```
SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      4431         -

```

---

### Post by ken_vh on 2007-12-11
[https://answers.launchpad.net/ubuntu/+question/16273](https://answers.launchpad.net/ubuntu/+question/16273)
Here was a person with a similar problem.
Someone said it could be a corrupt memory issue, which kind of makes sense, since all read/write actions are buffered in memory. Could you run memtest86 from the Ubuntu LiveCD(iirc, that's a boot option)?

---

### Post by ensis2k on 2007-12-12
Good idea. Thank you.

memtest86, after several hours of testing and 7 passes for each of the different kinds of tests, resulted in no errors at all.

The guy on the other forum had a different problem. The boot time of my system is fine. My system does not freeze randomly. My problem is reproduceable and is always in the _same place_ of the strace output. My strace shows that the problem is in a specific place.
Further the guy solved his problem by reinstalling linux ... i thought the "format c:" days were over :(

Here a strace of the totem player, wich also starts slowly. The slow part is also *always* on the same place.
```

     0.000085 mmap(NULL, 4096, PROT_READ|PROT_WRITE, MAP_PRIVATE|MAP_ANONYMOUS, -1, 0) = 0x2b2a30843000
     0.000056 read(11, "\0\4XSMP\0\0\0\37local/apfel:/tmp/.ICE-"..., 4096) = 1694
     0.000078 close(11)                 = 0
     0.000052 munmap(0x2b2a30843000, 4096) = 0
     0.000057 write(10, "\0\4\1\0\3\0\0\0\20\0\0\0\0\0\0\0\0X\262\361\335\212\224"..., 32) = 32
     0.000079 read(10, "\0\10\0\1\3\0\0\0", 8) = 8
     0.000061 read(10, "\7\0GnomeSM\0001.\6\0002.20.1\0\0\0\0", 24) = 24
     0.000108 write(10, "\1\1\1\0\1\0\0\0\0\0\0\0\0\0\0\0", 16) = 16
     0.000076 read(10, "\1\2\0\1\6\0\0\0", 8) = 8
    20.004229 read(10, "%\0\0\000103a4dbb07000119749279900000"..., 48) = 48
     0.000246 write(10, "\1\f\1\0\t\0\0\0\1\0\0\0*+\0\0\20\0\0\0CurrentDirec"..., 80) = 80
     0.000182 write(10, "\1\f\1\0\10\0\0\0\1\0\0\0*+\0\0\t\0\0\0ProcessIDrec"..., 72) = 72
     0.000087 write(10, "\1\f\1\0\10\0\0\0\1\0\0\0*+\0\0\7\0\0\0ProgramIDrec"..., 72) = 72
     0.000097 write(10, "\1\f\1\0\10\0\0\0\1\0\0\0*+\0\0\f\0\0\0CloneCommand"..., 72) = 72
     0.000117 write(10, "\1\f\1\0\25\0\0\0\1\0\0\0*+\0\0\16\0\0\0RestartComma"..., 176) = 176
     0.000089 write(10, "\1\f\1\0\10\0\0\0\1\0\0\0*+\0\0\6\0\0\0UserIDtComma"..., 72) = 72
     0.000126 write(3, "\233\2\4\0\1\0\0\4\355\0\0\0\7\0\0\0\20\0\5\0\f\0\0\0S"..., 36) = 36
     0.000084 read(3, 0x7fff869eb530, 32) = -1 EAGAIN (Resource temporarily unavailable)
     0.000065 poll([{fd=3, events=POLLIN, revents=POLLIN}], 1, -1) = 1
     0.000063 read(3, "\0010_\0\0\0\0\0(\1\0\0\0\0\0\0$\266~\0\0\0\0\0p\32\246"..., 32) = 32

```


Again after a GnomeSM call. Is something wrong with my Gnome Session Manager?


Thanks,
Yelve

Edit:
The problematic part of the strace result of totem looks identical to the problematic part of gedit. Maybe it is some library that makes all those problems?

---

### Post by the C.L.A. on 2007-12-16
Hi.

I had the same problem and strace looked the same as well. In my case it got solved by editing /etc/hosts:

1. commenting out all IPv6 entries
2. adding my hostname to the line for localhost

See:
[https://bugs.launchpad.net/ubuntu/+bug/93447](https://bugs.launchpad.net/ubuntu/+bug/93447)

---

### Post by ensis2k on 2007-12-19
This solved my problem.
Thank you very much for this nice Christmas gift.

I wish you all a merry Christmas.

---

