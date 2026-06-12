---
title: "symptom similar to thermal shutdown"
date: 2018-02-13
forum: General Help
---

### Post by jschissel on 2018-02-13
Hi, everyone, I am having a very strange situation and I am not sure how to troubleshoot.  I will try to keep this as logically sorted and concise as possible.

Headless media server running xubuntu, typically serving SQL, NFS, SMB, AFP, SSH, VNC, and sporting 4 hard drives, one system software hard drive, and 3 in a software RAID 5 array for network storage and backup.  Latest xubuntu release.  All drives in RAID array are UUU.

The weirdness: System suddenly started to shut down in a way that would mimic a thermal shutdown.  It is an abrupt stop with no log entry that I've identified.  However, it's possible I'm missing something.

Observations and troubleshooting:
[LIST]
[*]CPU 1 & 2 both vary but end up between 30 and 40 degrees.
[*]Another temperature, the northbridge maybe? reads between 50 and 55 degrees.
[*]Fan speeds are at around ~10000rpm at full speed as manipulated by me
[*]System may operate 5 minutes before shutdown, progressively worse from several days ago when it would operate maybe even several hours.
[/LIST]

Weirdness:
[LIST]
[*]When RAID drives are removed, the system does not experience the possible thermal shut down, and the only open ports are RPCBIND and NFS.  I am able to successfully connect to NFS share.
[*]Reinserting the three RAID drives causes them to spin up, but no other changes in system operation are apparent to me and there are no thermal shutdowns.  I am still only left with NFS.  NFS shares do not include any system files in this case.
[/LIST]

I used pwmconfig and fancontrol.  I am able to get a VGA cable that connects to the motherboard so I am thinking that is my next step.  If anyone has any suggestions, the help is greatly appreciated!!!!!!!!!

Best regards,
Joe

---

### Post by papibe on 2018-02-13
Hi jschissel. Welcome to the forum ):P

A few thoughts:

After a crash, check not onlythe last lines of the log, but the boot process too. There you may find a warning that can point you in the right direction.

I would also check if you have enough space on the root partition, both blocks and inodes.

You can also check the smart data of your hard drives including thermals.

Does you PSU support all the power required to support all those drives?

Regards.

---

### Post by Yellow Pasque on 2018-02-14
What CPU is this? (To rule out possibility of issues with recent Intel microcode issues): 
```
cat /proc/cpuinfo
```

---

### Post by jschissel on 2018-02-14
Thanks!  And thank you very much for the tip, I will check the boot as soon as I'm able to get into it.  I think I will have to get my VGA cable at this point.  Also the smart status.

I am interested to know what your thought process behind space and inodes is to lead to a shutdown like this.

I am not sure on the PSU, will try to figure it out as well.  The system itself is pretty old at this point, but was built with four storage bays and a backplane with the intent of serving media from a Windows Home Server OS.

CPU is an Athlon x2 3800+ [COLOR=#333333][FONT=&quot]ADD3800IAA5CU[/FONT][/COLOR]

---

