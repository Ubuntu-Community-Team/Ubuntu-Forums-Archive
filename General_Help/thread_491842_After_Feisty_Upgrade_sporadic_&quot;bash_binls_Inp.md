---
title: "After Feisty Upgrade: sporadic &quot;bash: /bin/ls: Input/output error&quot;"
date: 2007-07-04
forum: General Help
---

### Post by cribble on 2007-07-04
Hi,

after my upgrade to feisty I get sporadic Input/output errors.
I can't reproduce them or track them down to something, they happen in every situation, with load, without load, with disk IO and without. Frequency is about 2 times a day and on every second system halt, right before the system should power off itself.
In this state the system is of course not usable, as every application dies that wants to write to disk.

In the shell it looks like this then:

```

rob@robert:~$ ls
bash: /bin/ls: Input/output error
rob@robert:~$ dmesg
bash: /usr/bin/command-not-found: Input/output error

```

I checked my disk with long and short S.M.A.R.T. test, tested the whole disk with badblocks and checked my XFS Filesystem.

System is a default Feisty with lowlatency kernel.
```

rob@robert:~$ uname -a
Linux robert 2.6.20-15-lowlatency #2 SMP PREEMPT Sun Apr 15 07:39:03 UTC 2007 i686 GNU/Linux

```

The problem also appeared with my own kernel.

Anyone knows how I can redirect syslog output to i.e. vt 12?

Thanks for help and hints,

cribble

---

