---
title: "question about my software raid / entries in mdadm.conf"
date: 2013-11-08
forum: General Help
---

### Post by eyjoel on 2013-11-08
hi community,

i am using ubuntu 12.04 lts 64 bit as a file server.
i have a raid1 with the os and a raid 5 with my data.
when i reboot my system i receive an error while the system is trying to mount the raid5.
during the boot process fsck failed on my raid5.

i am not sure why so i wanted to discuss here some things.

i have[INDENT]2 disks /dev/sda1 /dev/sdb1 as software raid1
[/INDENT]
[INDENT]4 disks /dev/sdc /dev/sdd /dev/sde /dev/sdef as software raid 5
[/INDENT]

/proc/mdstat shows me 
```

Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md4 : active raid5 sde1[2] sdc1[0] sdd1[1] sdf1[3](S)
      3907026944 blocks level 5, 512k chunk, algorithm 2 [3/3] [UUU]
      
md0 : active raid1 sda1[0] sdb1[1]
      58559360 blocks super 1.2 [2/2] [UU]
      
unused devices: <none>

```

my fstab looks like
```

proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/md127 during installation
UUID=b40bd47b-9fb7-412e-8193-91f272df1451 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=a4278484-97cb-48f4-8e3f-55ad17079e2b none            swap    sw              0       0
# swap was on /dev/sdb5 during installation
UUID=aa26ba52-afee-48cb-a40c-6f535b7caace none            swap    sw              0       0
# data
UUID=a1bee469-8263-4fb3-b948-46c8116b72ec /export         xfs    defaults 0       2

```

my mdadm.conf has
```

ARRAY /dev/md0 metadata=1.2 UUID=61daa231:f14750ae:228036d4:59b5176e
ARRAY /dev/md4 UUID=09106cbd:52334774:ab873052:abf2e7ef
   spares=2

```

in the boot.log i can see (some parts are german, sry ... )

```

fsck von util-linux 2.20.1
fsck: fsck.xfs: not found
fsck: error 2 while executing fsck.xfs for /dev/md4
mountall: fsck /export [358] brach mit dem Status 8 ab
mountall: Nicht behebbarer fsck-Fehler: /export

```

now my questions:
is this only from the missing fsck for xfs file system?
i have installed xfsprogs. i will make a reboot at proper time to see if the error come up again.

is my mdadm.conf ok?
i wonder because  "spares = 2". i have only 1 spare configured. does the 2nd spare comes from the raid5 mechanism itself?

best regards

--christian

---

### Post by TheFu on 2013-11-08
**fsck: fsck.xfs: not found**

That is the issue. Are there xfs-tools to be installed?  Is this the same system where the RAID5-xfs file system was created?
That is all I've got.  

You can try:
**whereis fsck.xfs**
but if it was in the PATH, this probably is not likely.

You can try 
**locate fsck.xfs**
but if the system doesn't keep the updatedb current ... 

You can try 
**find / -name fsck.xfs -type f**
but that will take a long time and may not find anything if the xfs tools weren't installed. the program could be corrupted.

I would check the log files for other issues - dmesg, /var/log/* ... look for warnings and errors.

---

