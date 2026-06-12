---
title: "Error Message after restarting for the first time Part II"
date: 2007-08-05
forum: General Help
---

### Post by Helluo on 2007-08-05
I'm afraid I too have a problem during my Ubuntu installation using Wubi (which I might add is a great way to do all of this).

Upon the first reboot (after I've been back into Windows per the instructions), I get a similar error to many.

Loading, Please wait
No RAID disks
[  29.823199]sda: assuming drive cache: write through
[  29.836192]sda: assuming drive cache: write through
Check root=boot arg cat/proc/cmdline
or missing modules, devices: cat/proc/modules ls/dev
ALERT! does not exist.  Dropping to a shell!

:confused:

I'm installing on a NTFS HD with 16GB free after a 8GB installation. WinXp, 1.01gHZ Athlon with 512RAM. 

Please advise if possible.  The only reason I posted is that my "sda error" was apparently different from the API error other folks have reported.  I'm using Wubi, installing from the Fiesty Fawn "ubuntu-7.04-alternate-i386.iso torrent", so it should match the Wubi installer (Wubi-7.04.04.exe).  

Thanks for any help, great program, I'm excited to get another crack at Linux (ran Phatlinux briefly in college...a mixed bag, eh!).

Cheers,
-Mike.

---

### Post by ago on 2007-08-06
There should be a couple of log files unde /tmp, it would help if you could post their content

---

### Post by Helluo on 2007-08-06
Thanks for the attempt Ago, where might I find /tmp?
  Try booting again and use that as a command after it craps out?

Thanks

---

### Post by tuxcantfly on 2007-08-06
> Thanks for the attempt Ago, where might I find /tmp?
Try booting again and use that as a command after it craps out?

Thanks

```
ls /tmp
```

that'll list the files in /tmp, and for each file you find there (for example zenigata.log:
```

cat /tmp/zenigata.log | more
```

---

### Post by Helluo on 2007-08-06
I rebooted into Ubuntu, and this time I didn't get the sda error, just:

Loading, Please wait
No RAID disks

(long pause here)

Check root=boot arg cat/proc/cmdline
or missing modules, devices: cat/proc/modules ls/dev
ALERT! does not exist. Dropping to a shell!


I tried the dump of the zenigata.log, which seemed to be the only log in that /tmp directory.  I wrote down what I could, but I didn't know how to pause the dump (like in dos) so I hope I have it all:

+echo PROGRESS_STATE=12
+[ -x /sbin /usplash_write]
+/sbin/usplash_write PROGRESS12
+return 5
+log_warning_msg Could not find host..
+_log_msg Warning: Could not find host..
+echo Warning: Could not find host..
Warning: Could not find host..
+return5
+log_failure_msg Could not find host folder, please check boot parameters
+_log_msg Failure: Could not find host folder, please check boot parameters
+echo Failure:Could not find host folder, please check boot parameters
Failture: Could not find host folder, please check boot parameters
+pause_for_debug_ zenigata end
+cd/
+cp_logs
+[ -e /logs ]
+mkdir /logs
+cp   /tmp/zenigata.log /logs
+[ -e ]
+[ -e /logs ]
+cp   /tmp/zenigata.log /logs
+ [n = y]
+return 0
cat: Read Error: Is a directory
cat: more No such file or directory



Thanks for any advice, I appreciate your newbie patience!

---

### Post by ago on 2007-08-07
For some reason it cannot read the partition where you installed wubi, but the relevant log is not in there. Try a fresh install, if it still fails use the command:

more /tmp/zenigata.log

---

### Post by Helluo on 2007-08-08
Thanks again for the help ago.  Same "sda" error, though.  With that last tip I can peruse the entire zenigata.log.  Is there a way to copy it to a floppy or something?  I certainly can't type it all out, and I'm not sure what's most pertinent to my problem.


Thanks again for any assistance.  This is still being installed via Wubi and the torrented disc image,  onto an unparitioned hard drive.

---

### Post by ago on 2007-08-09
mkdir /floppy
mount -t auto /dev/fd0 /floppy
cp /tmp/*.log /floppy

this assumes that the floppy is already formatted

---

