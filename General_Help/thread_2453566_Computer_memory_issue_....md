---
title: "Computer memory issue ..."
date: 2020-11-13
forum: General Help
---

### Post by dbee on 2020-11-13
I seem to be running out of memory. The issue has gotten alot worse since i installed a microsd card...

this is my *top*. *kswapd* can use up to 50% of CPU at any given time, yet KiB Swap is zero ....

```

top - 07:48:08 up 13 min,  1 user,  load average: 4.76, 2.59, 1.60
Tasks: 192 total,   2 running, 153 sleeping,   0 stopped,   0 zombie
%Cpu(s): 31.8 us,  9.9 sy,  0.5 ni, 51.9 id,  5.5 wa,  0.0 hi,  0.5 si,  0.0 st
KiB Mem :  1944604 total,    63796 free,  1552500 used,   328308 buff/cache
KiB Swap:        0 total,        0 free,        0 used.    41836 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
   41 root      20   0       0      0      0 R  12.9  0.0   0:25.37 kswapd0
  174 root      20   0       0      0      0 S   3.2  0.0   0:08.17 mmcqd/0
 1130 dara      20   0 1016904 130296  11296 D   3.2  6.7   1:50.83 chrome
 3692 dara      20   0   44076   3528   2936 R   3.2  0.2   0:00.06 top
 1580 dara      20   0  545492  31332   5872 S   1.6  1.6   0:12.22 chrome
    1 root      20   0  225416   3604   1128 S   0.0  0.2   0:02.71 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    4 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 kworker/0:+
    5 root      20   0       0      0      0 I   0.0  0.0   0:00.19 kworker/u8+
    6 root       0 -20       0      0      0 I   0.0  0.0   0:00.00 mm_percpu_+
    7 root      20   0       0      0      0 S   0.0  0.0   0:00.14 ksoftirqd/0
    8 root      20   0       0      0      0 I   0.0  0.0   0:00.82 rcu_sched
    9 root      20   0       0      0      0 I   0.0  0.0   0:00.00 rcu_bh
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 migration/0
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/0
   12 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/0
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.00 cpuhp/1
   14 root      rt   0       0      0      0 S   0.0  0.0   0:00.00 watchdog/1

```

and my* /proc/meminfo*

```

dara@dara-HP-Stream-Laptop-11-y0XX:~/Desktop$ cat /proc/meminfo
MemTotal:        1944604 kB
MemFree:          153752 kB
MemAvailable:     677792 kB
Buffers:           40200 kB
Cached:           709140 kB
SwapCached:            0 kB
Active:          1179528 kB
Inactive:         432212 kB
Active(anon):     864828 kB
Inactive(anon):   113492 kB
Active(file):     314700 kB
Inactive(file):   318720 kB
Unevictable:          48 kB
Mlocked:              48 kB
SwapTotal:             0 kB
SwapFree:              0 kB
Dirty:               216 kB
Writeback:             0 kB
AnonPages:        862480 kB
Mapped:           270828 kB
Shmem:            115920 kB
Slab:             102772 kB
SReclaimable:      43524 kB
SUnreclaim:        59248 kB
KernelStack:        7472 kB
PageTables:        35944 kB
NFS_Unstable:          0 kB
Bounce:                0 kB
WritebackTmp:          0 kB
CommitLimit:      972300 kB
Committed_AS:    4757160 kB
VmallocTotal:   34359738367 kB
VmallocUsed:           0 kB
VmallocChunk:          0 kB
HardwareCorrupted:     0 kB
AnonHugePages:         0 kB
ShmemHugePages:        0 kB
ShmemPmdMapped:        0 kB
CmaTotal:              0 kB
CmaFree:               0 kB
HugePages_Total:       0
HugePages_Free:        0
HugePages_Rsvd:        0
HugePages_Surp:        0
Hugepagesize:       2048 kB
DirectMap4k:      202816 kB
DirectMap2M:     1798144 kB

```


I don't sem to be able to get much out of *dmesg*

Also, how do i unmount a microsd card? I can access it no problem so presumably it's mounted. Yet when i do 

```

dara@dara-HP-Stream-Laptop-11-y0XX:~/Desktop$ sudo blkid
/dev/mmcblk0p1: UUID="42EC-0B92" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="56c62bfb-2ace-40f5-842b-56d170dc18b1"
/dev/mmcblk0p2: UUID="76e2b547-702d-4386-a868-9fedbc97bb53" TYPE="ext4" PARTUUID="51735fd3-6d98-4c40-8b16-28fdcb4a318e"
/dev/mmcblk1: LABEL="microsd" UUID="0e36cfc3-c8fe-4c2a-b85b-4267fb9b8f7f" TYPE="ext4"
/dev/mmcblk0: PTUUID="52c3523d-707f-4f3d-9321-0d620c9526c4" PTTYPE="gpt"

dara@dara-HP-Stream-Laptop-11-y0XX:~/Desktop$ umount /dev/mmcblk1
umount: /dev/mmcblk1: not mounted.

```

microsd is named but doesn't seem to be mounted for some reason ...

```

dara@dara-HP-Stream-Laptop-11-y0XX:~/Desktop$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
udev              949848        0    949848   0% /dev
tmpfs             194464     1408    193056   1% /run
/dev/mmcblk0p2  29407228 26584044   1306336  96% /
tmpfs             972300   104688    867612  11% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs             972300        0    972300   0% /sys/fs/cgroup
/dev/mmcblk0p1    523248     8596    514652   2% /boot/efi
tmpfs             194460       24    194436   1% /run/user/1000

```

Like i said, the problem seems to be exacerbated when i installed the microsd card. Also, when i open multiple tabs in chrome. Does each tab run as it's own process or something ?

---

### Post by wildmanne39 on 2020-11-13
*Thread moved to **General Help for a more appropriate fit**.*

---

### Post by dbee on 2020-11-13
I was getting a boot error with my system so i must have uncommented /mnt/microsd in */etc/fstab*

```

#UUID=0e36cfc3-c8fe-4c2a-b85b-4267fb9b8f7f /mnt/microsd/	  ext4	  discard,noatime,errors=remount-ro	  0	  1

```

How come i'm able to access my microsd card without mounting it specifically in */etc/fstab/* ? Is it because i named the volume ?

---

### Post by dbee on 2020-11-13
I ran a few 

```

du -h | sort -hr | more

```

and cleaned out some of the larger directories on my harddrive. Now i'm at 90% capacity.

computer doesn't seem to freeze when i keep chrome at 1 tab ...

when i don't, i get this from *dmesg*

```

   29.277137] IPv6: ADDRCONF(NETDEV_UP): br-5e87b27037b9: link is not ready
[   29.643540] IPv6: ADDRCONF(NETDEV_UP): br-6b997a73235d: link is not ready
[   29.952461] IPv6: ADDRCONF(NETDEV_UP): br-b3a964a0eb0e: link is not ready
[  645.722980] perf: interrupt took too long (2504 > 2500), lowering kernel.perf_event_max_sample_rate to 79750
[  784.530207] perf: interrupt took too long (3134 > 3130), lowering kernel.perf_event_max_sample_rate to 63750
[ 1291.406858] perf: interrupt took too long (3942 > 3917), lowering kernel.perf_event_max_sample_rate to 50500
[ 1919.866646] perf: interrupt took too long (4935 > 4927), lowering kernel.perf_event_max_sample_rate to 40500
[ 2390.342387] perf: interrupt took too long (6171 > 6168), lowering kernel.perf_event_max_sample_rate to 32250


```

---

### Post by TheFu on 2020-11-13
I don't see any swap enabled.  fix that.  The **swapon -s** command will check it. So will the **free -hm** command.

A system with only 2GB of RAM needs some swap.  If you use a modern browser, make it 4.1G swap size.

You can google how-to add swap. It could be just that old swap was disabled by you somehow. It would be very odd if o swap was setup during install.

---

### Post by ActionParsnip on 2020-11-14
Could upgrade the ram (if possible). It's pretty cheap and will really help the system

---

### Post by CelticWarrior on 2020-11-14
> **ActionParsnip said:**
> Could upgrade the ram (if possible).

No. not possible in a HP Stream 11. That's pretty much the definition of "disposable laptop". I should know, I have one.

---

### Post by TheFu on 2020-11-14
> **CelticWarrior said:**
> No. not possible in a HP Stream 11. That's pretty much the definition of "disposable laptop". I should know, I have one.

I had a chromebook running xUbuntu like that - 2G of RAM soldered onto the motherboard.  It was crashing due to low RAM. Changing the swap file to be 4.1G provided feedback so I could close programs before no ram was left and the system crashed. I had to learn to recognize when low RAM was happening.  It came with a 16G SSD, so making the swap huge wasn't an option.  I also enabled swap to be compressed. I think zswap is the default now, but it would be worth checking that as well.

---

### Post by dbee on 2020-11-15
[QUOTE=][/QUOTE]

So basically I seem to have unmounted the swap file in my system when i was editing the /etc/fstab file.

To fix it I added this to /etc/fstab ...

```

/swapfile        none            swap    sw              0       0

```

Then i remade swap, turned swapon and mounted it

```

root@dara-HP-Stream-Laptop-11-y0XX:/etc# sudo mkswap /swapfile
mkswap: /swapfile: warning: wiping old swap signature.

Setting up swapspace version 1, size = 1.3 GiB (1425670144 bytes)
no label, UUID=23390c3c-eec5-428b-abd7-83e447016d52

root@dara-HP-Stream-Laptop-11-y0XX:/etc# sudo swapon /swapfile

root@dara-HP-Stream-Laptop-11-y0XX:/etc# mount -a

root@dara-HP-Stream-Laptop-11-y0XX:/etc# free -h

              total        used        free      shared  buff/cache   available
Mem:           1.9G        1.1G         95M        160M        680M        465M
Swap:          1.3G          0B        1.3G

```

Seems to have been an easy fix all things considered

---

### Post by dbee on 2020-11-15
> **TheFu said:**
> I don't see any swap enabled.  fix that.  The **swapon -s** command will check it. So will the **free -hm** command.

A system with only 2GB of RAM needs some swap.  If you use a modern browser, make it 4.1G swap size.

You can google how-to add swap. It could be just that old swap was disabled by you somehow. It would be very odd if o swap was setup during install.

I'll see how 1.3 GB does with regards to the swap partition. I barely have any hd left, so 4 GB would be a stretch.

Need to get a new travel laptop. Pronto.

Why have laptop prices gone way up btw? Is there a mem or cpu shortage?

---

### Post by TheFu on 2020-11-15
> **dbee said:**
> Why have laptop prices gone way up btw? Is there a mem or cpu shortage?

Supply and Demand. COVID-19.  More people needed laptops for their kids school work and to be able to work from home.

Just add more storage or replace the storage you have. That should be fairly cheap, unless you bought a laptop with eMMC soldered into storage.  BTW, don't do that - EVER.

If you want guidance for other things, post **inxi -Fz** output. Use _code tags_ for that, or it won't be readable here. I assume there are many different models of "hp-stream" devices.

---

### Post by CelticWarrior on 2020-11-15
> [COLOR=#000000]unless you bought a laptop with eMMC soldered into storage.[/COLOR]
Exactly that. 32 GB years ago, now 64GB.

> [COLOR=#000000]BTW, don't do that - EVER.[/COLOR]
Why not? As long as you have the correct expectations for the device then you got a reliable ultra-light media player laptop for cheap, very capable for the realistic tasks it can do for the next 2-3 years, maybe a little longer, and then you dispose of it and get yourself a more modern replacement.
The problem here is unrealistic expectations for a laptop that already passed its due date.

---

### Post by TheFu on 2020-11-15
> **CelticWarrior said:**
> Exactly that. 32 GB years ago, now 64GB.


Why not? As long as you have the correct expectations for the device then you got a reliable ultra-light media player laptop for cheap, very capable for the realistic tasks it can do for the next 2-3 years, maybe a little longer, and then you dispose of it and get yourself a more modern replacement.
The problem here is unrealistic expectations for a laptop that already passed its due date.

Many people don't intend to buy a new system every 2-3 yrs. Clearly the OP and I do not.  I have a laptop still being used from 2010.  It is powered on now. Used it for about 2 hrs earlier and use it daily still for specialized stuff that aren't worth moving anywhere else (specific hardware).  The internal storage on it was 320G, then 500G, then 750G and now it has a 1TB black drive.  I think the discrete AMD GPU will fail before anything else does. If only the Core i5 CPU it came with had an iGPU, I'd be much happier.  The battery life on that laptop always sucked. New, I think it got around 2 hrs, max.

I'd still be using my 2012 Acer Chromebook C720 if my attempt to swap the keyboard didn't brick it.

Always have a way to replace storage for any laptop and I don't mean via USB3 or MicroSD.  Real storage.  So when the current storage dies - all storage dies eventually - it can be cheaply replaced.  We need to vote with our $$$ and end crappy hardware from being produced.  There just isn't any need for eMMC today outside embedded, high-vibration, situations.

The planet needs us to use stuff longer.

IMHO.

---

### Post by dbee on 2020-11-17
Yeah, so the biggest drains on the system were GIMP which is a memory hog. But quite reasonably so IMO.

And chrome. Which seems to open a new process for every tab. Since *http* is stateless and a non-persistent connection. I wonder what the idea behind opening a new process for every tab is?

Never did any chrome programming or extension programming so I can't say I know much about the internals. But it seems excessive.

After the system crashing again, I figured I'd do a little spring cleaning and try to bump my swap to the suggested 4GB to see if that made any difference.

So I'd moved all my git projects to */mnt/microsd* which freed up some storage space ...

```

dara@dara-HP-Stream-Laptop-11-y0XX:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
udev              949628        0    949628   0% /dev
tmpfs             194464     1400    193064   1% /run
/dev/mmcblk0p2  29407228 25762812   2127568  93% /
tmpfs             972300    77780    894520   8% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs             972300        0    972300   0% /sys/fs/cgroup
/dev/mmcblk0p1    523248     8596    514652   2% /boot/efi
tmpfs             194460       16    194444   1% /run/user/1000

```

Then it was a case of releasing as much storage capacity as possible ... so i ran another ..

```

du -h | sort -hr | more
1.6G	/home/dara/.config/google-chrome
853M	/home/dara/.config/google-chrome/Profile 1
646M	/home/dara/.config/google-chrome/Default

```

It turns out that *google-chrome* in .config is 1.6 freaking GB. 

```

dara@dara-HP-Stream-Laptop-11-y0XX:~$ du -h ~/.config/google-chrome | sort -hr | more
1.6G	/home/dara/.config/google-chrome
853M	/home/dara/.config/google-chrome/Profile 1
646M	/home/dara/.config/google-chrome/Default
499M	/home/dara/.config/google-chrome/Profile 1/Service Worker
492M	/home/dara/.config/google-chrome/Profile 1/Service Worker/CacheStorage
231M	/home/dara/.config/google-chrome/Profile 1/Service Worker/CacheStorage/8
cbb992fe0cd9ef960e69a214646bd270516a23e
212M	/home/dara/.config/google-chrome/Profile 1/Service Worker/CacheStorage/4
c237d5e33167c88df3e45d9c8b59fdd4d727472
189M	/home/dara/.config/google-chrome/Default/Service Worker
182M	/home/dara/.config/google-chrome/Default/Service Worker/CacheStorage
157M	/home/dara/.config/google-chrome/Default/Application Cache/Cache
157M	/home/dara/.config/google-chrome/Default/Application Cache
147M	/home/dara/.config/google-chrome/Default/Service Worker/CacheStorage/8cb
b992fe0cd9ef960e69a214646bd270516a23e

```

What should i do about this chrome directory? Apprently *.cache* is 586MB. So I enter 

```

 chrome://settings/clearBrowserData

```

in the chrome URL bar. Which clears only 184MB according to chrome...

```

dara@dara-HP-Stream-Laptop-11-y0XX:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
udev              949628        0    949628   0% /dev
tmpfs             194464     1400    193064   1% /run
/dev/mmcblk0p2  29407228 25347436   2542944  91% /
tmpfs             972300    74360    897940   8% /dev/shm
tmpfs               5120        4      5116   1% /run/lock
tmpfs             972300        0    972300   0% /sys/fs/cgroup
/dev/mmcblk0p1    523248     8596    514652   2% /boot/efi
tmpfs             194460       16    194444   1% /run/user/1000


```

But my calculator seems to suggest that it freed 415 MB from my system. Plus I can't find the cache file any more. 

I'd like to keep my google-chrome cache file from building up... does anyone know whether i can delete the cache file on system boot from the crontab perhaps?

```

crontab -e
@reboot rm -rf ~/.config/google-chrome/cache

```

Is this safe? Or should i use the above method to delete via chrome?

Lastly, this is how i readjusted my */swapfile* to reset it from 1.6GB to 4GB which is the recommended max for a 2GB RAM system ...

```

sudo fallocate -l 4G /swapfile
sudo chmod 600 /swapfile
sudo mkswap /swapfile
sudo swapon /swapfile
sudo swapon --show
echo '/swapfile none swap sw 0 0' | sudo tee -a /etc/fstab

```

only do the last command if *cat /etc/fstab* doesn't have a swap file listed/mounted already. 

It's a pity that chrome lite only comes in android and tablet flavour.

Also, 2 more questions ...

1) Should i move the */swapfile* to */mnt/microsd* or will there be lagging/connection issues do you reckon? According to the ubuntu docs. It's a good idea to move it off your main harddrive.

2) Is it a good idea to move my work files to */mnt/microsd*? I'd prefer not to lose them, but i have most of them backed up...

3) How do i slim down the *.config/google-chrome/Profile 1* 854MB profile file? I could do with the storage. 

My harddrive is now at 100% capacity since I expanded my */swapfile*. Bummer. Time for a new computer I think.

---

### Post by dbee on 2020-11-17
Didn't need to touch the *google-chrome/profile* afterall. Turns out that *./var/lib/docker/overlay2* the docker image file was 6.5 GB.

I only use docker for *wp-env* to create WordPress containers and run themes, plugins etc...

I don't need to store any docker networks, volumes, connections etc...

So i ran a...

```

docker system prune -a

```

and it freed up 6.5GB on my system. Plus i can still run *wp-env*.

I added the command to my *crontab* to run it on reboot everytime and things are sorted.

---

### Post by TheFu on 2020-11-17
is this solved?  Use the **THREAD TOOLS** button so people can search and find it as solved.
If not, hw faults and kernel issues are next. to check.  Look in the system log files.

Browsers run tabs in different processes for security reasons.

---

