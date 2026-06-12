---
title: "How can I find out how much memory used by a process"
date: 2008-03-31
forum: General Help
---

### Post by yinglcs2 on 2008-03-31
Hi,

From the 'ps -ef ' command, how can I find out how much memory used by a process?

Thank you.

---

### Post by jakupl on 2008-03-31
If you just write
```
$ top
```
you get a fine list

---

### Post by thorre on 2008-03-31
You could also try the following:
Find out which process id (PID) the proggie that you are intrested in has. You can do that with "ps auxw"

Then "cat /proc/<PID>/status"

This should give you detailed information.

The outbut should look something like this:

[I]eop:~# cat /proc/21225/status 
Name:	bash
State:	S (sleeping)
SleepAVG:	98%
Tgid:	21225
Pid:	21225
PPid:	21221
TracerPid:	0
Uid:	0	0	0	0
Gid:	0	0	0	0
FDSize:	256
Groups:	0 
VmPeak:	    4848 kB
VmSize:	    4848 kB
VmLck:	       0 kB
VmHWM:	    2604 kB
VmRSS:	    2604 kB
VmData:	    1116 kB
VmStk:	      84 kB
VmExe:	     644 kB
VmLib:	    2892 kB
VmPTE:	      12 kB
Threads:	1
SigQ:	1/4294967295
SigPnd:	0000000000000000
ShdPnd:	0000000000000000
SigBlk:	0000000000010000
SigIgn:	0000000000384004
SigCgt:	000000004b813efb
CapInh:	0000000000000000
CapPrm:	00000000fffffeff
CapEff:	00000000fffffeff
Cpus_allowed:	ff
Mems_allowed:	1[/I]

---

