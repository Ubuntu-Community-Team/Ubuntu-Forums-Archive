---
title: "Using Partial RAM on 12.10"
date: 2013-02-06
forum: General Help
---

### Post by cazazo on 2013-02-06
Hi after updating from 11.04 to 12.10 my system is not using the 12GB I have installed in.

```
# free -m
             total       used       free     shared    buffers     cached
Mem:          8090       1996       6094          0         87       1012
-/+ buffers/cache:        897       7193
Swap:        12284          0      12284

```

any Ideas??? I shows up in the swap section though.

---

### Post by mcduck on 2013-02-06
Does the last 4GB show correctly in BIOS or if you boot to the memtest from Grub menu?

---

### Post by tgalati4 on 2013-02-06
I presume that you have a swap partition that is a little over 12GB in size.

Open a terminal:

```
cat /etc/fstab
```

Only 8GB is showing.  Perhaps there is a RAM problem.  Try reseating the RAM modules.

Check the BIOS to see if the RAM is seen in BIOS.  Run memtest to see if 12GB is seen.

```
dmesg | more
```

Look for memory-related errors.

---

### Post by cazazo on 2013-02-06
The output of the given cli

```
:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=693854c1-bcf8-42e0-8441-b86092d8697b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d80a0973-6885-449b-b1a4-c6c3c6d86657 none            swap    sw              0       0


:~$ dmesg | more
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-23-generic (buildd@aatxe) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #35-Ubuntu SMP Thu 
Jan 24 13:05:29 UTC 2013 (Ubuntu 3.5.0-23.35-generic 3.5.7.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x00000000000977ff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000097800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cbe7ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cbe80000-0x00000000cbe8ffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cbe90000-0x00000000cbecffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cbed0000-0x00000000cbedffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cbeeb800-0x00000000cbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
```

---

### Post by rnerwein on 2013-02-06
> **cazazo said:**
> The output of the given cli

```
:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=693854c1-bcf8-42e0-8441-b86092d8697b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=d80a0973-6885-449b-b1a4-c6c3c6d86657 none            swap    sw              0       0


:~$ dmesg | more
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.5.0-23-generic (buildd@aatxe) (gcc version 4.7.2 (Ubuntu/Linaro 4.7.2-2ubuntu1) ) #35-Ubuntu SMP Thu 
Jan 24 13:05:29 UTC 2013 (Ubuntu 3.5.0-23.35-generic 3.5.7.2)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] e820: BIOS-provided physical RAM map:
[    0.000000] BIOS-e820: [mem 0x0000000000000000-0x00000000000977ff] usable
[    0.000000] BIOS-e820: [mem 0x0000000000097800-0x000000000009ffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000000e4000-0x00000000000fffff] reserved
[    0.000000] BIOS-e820: [mem 0x0000000000100000-0x00000000cbe7ffff] usable
[    0.000000] BIOS-e820: [mem 0x00000000cbe80000-0x00000000cbe8ffff] ACPI data
[    0.000000] BIOS-e820: [mem 0x00000000cbe90000-0x00000000cbecffff] ACPI NVS
[    0.000000] BIOS-e820: [mem 0x00000000cbed0000-0x00000000cbedffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000cbeeb800-0x00000000cbffffff] reserved
[    0.000000] BIOS-e820: [mem 0x00000000fee00000-0x00000000fee00fff] reserved
```
hi
what does: grep -i memory /var/log/syslog (or syslog.1) gives you ?
cheers

---

### Post by tgalati4 on 2013-02-06
Examining fstab validates that you have a real swap partition on /dev/sda5.  So there is no RAMdisk swap or temporary swap file that is taking up RAM.

dmesg | more

You need to use the spacebar to page forward through the messages, "q" to quit.  This allows you to examine messages related to memory detection.

Try this:

```
dmesg | grep MB
```

---

### Post by Cheesemill on 2013-02-06
Can you post the output of...
```
sudo dmidecode -t memory
```

This will give us a lot more information on your memory setup.

---

### Post by cazazo on 2013-02-07
Well I didn't do anything other than disconnect on of the extra fans I did install for the video card... took the memories off their slots and plug them back in... and was back in the system.
Is that possible that the fan has influenced on the memory??? once I have disconnected the power cable and the memory has come back up??? Could it be the power limit?? 
I'm really confused here!

```
desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:         12146       1426      10719          0         95        677
-/+ buffers/cache:        653      11492
Swap:        12284          0      12284

```

---

### Post by mcduck on 2013-02-07
Since you took the memory modules off the slots and plugged them back again, that was most likely what made them work again.

In other words, one of the modules just wasn't properly in it's place.

...and no, it's extremely unlikely that the fans had anything to do with the problem. :D

---

### Post by cazazo on 2013-02-07
Thank you guys!

---

### Post by rnerwein on 2013-02-07
> **cazazo said:**
> Well I didn't do anything other than disconnect on of the extra fans I did install for the video card... took the memories off their slots and plug them back in... and was back in the system.
Is that possible that the fan has influenced on the memory??? once I have disconnected the power cable and the memory has come back up??? Could it be the power limit?? 
I'm really confused here!

```
desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:         12146       1426      10719          0         95        677
-/+ buffers/cache:        653      11492
Swap:        12284          0      12284

```
hi
belive on mcduck - he is telling the truth.
(fan will never use memory only temprature :-)  )
and a hint. be grounded when you plug in modules in your box - EMP is the suddent die of modules !! )
stay relaxed now.
cheers

---

