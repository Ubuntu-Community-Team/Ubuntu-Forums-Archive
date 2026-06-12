---
title: "Logwatch: Kernel Errors Present"
date: 2014-03-13
forum: General Help
---

### Post by Michael_Gaab on 2014-03-13
I'm on Ubuntu 12.04.4 LTS (GNU/Linux 3.2.0-60-virtual x86_64).


I'm seeing the following line in the logwatch report after a reboot.

 WARNING:  Kernel Errors Present
    EXT4-fs (vda): re-mounted. Opts: errors=remount-ro ...:  1 Time(s)

I'm seeing these lines in the syslog:

Mar 12 20:13:45 toktime kernel: [    2.239972] EXT4-fs (vda): mounted filesystem with ordered data mode. Opts: (null)
Mar 12 20:13:45 toktime kernel: [    2.480345] EXT4-fs (vda): re-mounted. Opts: errors=remount-ro

Is this something I should be concerned about? The servers are hosted at a popular VPS hosting service. They think it is nothing to be concerned about. I would like to know more. Thanks. Mike

---

### Post by fomember on 2014-04-29
I think it is a flaw with logwatch.
To my understanding it is normal behaviour that during boot the root filesystem is first mounted ro and after it has passed some checks it gets remounted.
Logwatch seems to just to check the fstab line in the log file, see the error option and report it as a false positive.
It is a false positive because the fstab entry says "in case of an error, remount as ro" but the file system in fact gets remounted as rw after it was initially mounted as ro.
So the line from fstab appears in the dmesg log and logwatch unfortunately just seems to trigger on the word error.
The same thing happens with the entry "ERST: Error Record Serializa" which gets me a logwatch error after every boot.
I hope that future versions of logwatch will have an option to filter those false positives which are a real nag to me.

---

