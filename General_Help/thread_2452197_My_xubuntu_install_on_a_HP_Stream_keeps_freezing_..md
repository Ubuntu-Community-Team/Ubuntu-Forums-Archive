---
title: "My xubuntu install on a HP Stream keeps freezing ..."
date: 2020-10-18
forum: General Help
---

### Post by dbee on 2020-10-18
So basically my old laptop computer (HP Stream) running xubuntu keeps freezing and I'm having to hit the power off button like 7 or 8 times everyday to get it back working.

I've tried *ctrl + alt + K* but it doesn't make any difference. The screen just freezes up and the mouse pointer won't even move.

I'm assuming because I hit power off that the system doesn't have time to log to syslog but here it is anyway ...

[https://pastebin.com/gdHdk4H6](https://pastebin.com/gdHdk4H6)

My best guess is that it's a mem issue. since my laptop has hardly any memory and can't be fitted with more.

```
top - 17:36:58 up 15 min,  1 user,  load average: 1.12, 1.35, 1.11
Tasks: 220 total,   1 running, 183 sleeping,   0 stopped,   0 zombie
%Cpu(s): 24.6 us,  6.2 sy,  0.0 ni, 67.3 id,  1.3 wa,  0.0 hi,  0.5 si,  0.0 st
KiB Mem :  1944608 total,   104764 free,  1401468 used,   438376 buff/cache
KiB Swap:  1392256 total,   750464 free,   641792 used.   262804 avail Mem 

```

```
dara@dara-HP-Stream-Laptop-11-y0XX:~$ uname -a
Linux dara-HP-Stream-Laptop-11-y0XX 4.15.0-121-generic #123-Ubuntu SMP Mon Oct 5 16:16:40 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux

```

is there anything I can do about this issue besides getting a new computer?

---

### Post by dbee on 2020-10-29
so i've emptied Trash and truncated /var/log/journal - which was 1.4GB.

```

truncate /var/log/journal/*/.journa* --size 0

```

My hard drive had only 5GB free. Could that have been the issue perhaps? In particular could it have effected the swap partition? I presume thtat's a separate partition on it's own?

I followed this guide to free up space. It's kinda long and was written for ubuntu, not xubuntu but you can get the idea ... 

[Freeing up space on ubuntu]("https://help.ubuntu.com/community/RecoverLostDiskSpace")

Apparently the sys req. for xubuntu is ...

> 
Recommended system resources

To get a smooth experience when running multiple applications parallel on the desktop, it is recommended to have a 1.5Ghz Dual Core processor with at least 2 GB of memory.

It is recommended to have at least 20 GB of free space on your hard disk. This allows new application installations as well as saving your personal data on the hard disk in addition to the core system.


I have a 1.6GHz dual core processor which should be fine for xubuntu. And 2GB memory which should suffice.

> 
dara@dara-HP-Stream-Laptop-11-y0XX:~$ cat /proc/cpuinfo
processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 76
model name	: Intel(R) Celeron(R) CPU  N3060  @ 1.60GHz
stepping	: 4
microcode	: 0x411
cpu MHz		: 1989.195
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx rdtscp lm constant_tsc arch_perfmon pebs bts rep_good nopl xtopology tsc_reliable nonstop_tsc cpuid aperfmperf tsc_known_freq pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer aes rdrand lahf_lm 3dnowprefetch epb pti ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat md_clear
bugs		: cpu_meltdown spectre_v1 spectre_v2 mds msbds_only
bogomips	: 3200.00
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 76
model name	: Intel(R) Celeron(R) CPU  N3060  @ 1.60GHz


The 2GB of mem should be able to handle most parallel applications IMO apart from maybe video editing software - which I don't use anyway.

According to `top` chrome seems to be a bit of a cpu and memory hog. I usually have 5 or 6 chrome tabs open at a time.

After clearing out some of the harddrive i now have 9.2GB free. Is that too little? Or does it make a difference? should I continue to look to free up hd space?

```

dara@dara-HP-Stream-Laptop-11-y0XX:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev            928M     0  928M   0% /dev
tmpfs           190M  1.5M  189M   1% /run
/dev/mmcblk0p2   29G   18G  9.2G  66% /
tmpfs           950M   95M  855M  10% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           950M     0  950M   0% /sys/fs/cgroup
/dev/mmcblk0p1   99M  6.1M   93M   7% /boot/efi
tmpfs           190M   20K  190M   1% /run/user/1000

```

---

### Post by argon-1511 on 2020-10-29
You could potentially try Lubuntu, given that it's designed for low resource.  I'm running it on an HP Stream, with 4 gigs of RAM though.

---

### Post by dbee on 2020-11-10
> **argon-1511 said:**
> You could potentially try Lubuntu, given that it's designed for low resource.  I'm running it on an HP Stream, with 4 gigs of RAM though.

I thought xUbuntu was for low resource systems ?

Also, will this Micro SD card work with my HP-Stream-Laptop-11-y0XX?

[https://www.amazon.co.uk/dp/B073JYC4XM/?coliid=I2EN0R4EAKOCGQ&colid=13HBHW27KUPS5&psc=1&ref_=lv_ov_lig_dp_it](https://www.amazon.co.uk/dp/B073JYC4XM/?coliid=I2EN0R4EAKOCGQ&colid=13HBHW27KUPS5&psc=1&ref_=lv_ov_lig_dp_it)

Do you think it's worth investing in? Will it solve my HP Stream freezing issue do you think?

---

