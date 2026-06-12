---
title: "Why Does Ubuntu Suddenly Feel So SLOW??"
date: 2023-08-23
forum: General Help
---

### Post by kabirgandhiok on 2023-08-23
Hi,

Is it just me or has ubuntu suddenly become slow or is it the Intel / AMD bug fix, I mean my system is ridiculously slow. All I need to do is put a torrent file of say about 10GB on download and watch a video alongside, and thats it, the system hangs and freezes. CPU loads reach way up above 4, ranging between 8 and 7 for what? just a torrent download and a video playback? It was not so slow about a week or two ago. Is it due the new Intel / AMD bug fix mitigation that makes the system 50% slower? I am running 11th generation i5 intel with integrated iris xe intel graphics. Is there anyway I can bypass or disable this mitigation if indeed that is the cause?

Thanks so much for helping me understand why this happening.

---

### Post by ian-weisser on 2023-08-23
Next time you encounter a slowdown, run the "free" command while it's slow, and post the complete output. Let's try some troubleshooting to confirm the problem before leaping to a conclusion.

---

### Post by SeijiSensei on 2023-08-24
Do you have a swapfile or swap partition? Here's a way to create a swapfile in case you're having memory problems.

[https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04)

---

### Post by kabirgandhiok on 2023-08-24
> **ian-weisser said:**
> Next time you encounter a slowdown, run the "free" command while it's slow, and post the complete output. Let's try some troubleshooting to confirm the problem before leaping to a conclusion.

Thanks for your suggestions, I was able to reproduce a slowdown with the same behavior. A torrent on download alongside a video playing on celluloid

```

kabir@kabirsubuntu:~$ free
               total        used        free      shared  buff/cache   available
Mem:        16107084     3084360      320620     1261896    12702104    11415692
Swap:       33554428     1052296    32502132

kabir@kabirsubuntu:~$ uptime
 01:10:13 up 2 days,  1:47,  1 user,  load average: 5.22, 4.68, 2.59
kabir@kabirsubuntu:~$ uptime
 01:16:33 up 2 days,  1:54,  1 user,  load average: 5.04, 4.54, 3.22
kabir@kabirsubuntu:~$ uptime
 01:17:44 up 2 days,  1:55,  1 user,  load average: 7.43, 5.12, 3.50

kabir@kabirsubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           1.6G  2.3M  1.6G   1% /run
/dev/sda2       916G  662G  208G  77% /
tmpfs           7.7G     0  7.7G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
/dev/sda1       511M  6.3M  505M   2% /boot/efi
tmpfs           1.6G  172K  1.6G   1% /run/user/1000

```

At this stage video playback has become choppy, skipping frames. Once I shutdown the torrent download, it works fine.
Thanks

---

### Post by kabirgandhiok on 2023-08-24
> **SeijiSensei said:**
> Do you have a swapfile or swap partition? Here's a way to create a swapfile in case you're having memory problems.

[https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-20-04)

I have a swapfile twice the size of the system ram (16gb)
```

kabir@kabirsubuntu:~$ swapon -s
Filename                Type        Size        Used        Priority
/swapfile               file        33554428    1093592        -2

```

---

### Post by TheFu on 2023-08-24
**inxi -Fz** would help us understand more about the system.
I haven't noticed any slowdowns myself.
If you don't actually need a huge swapfile the old rule-of-thumb for 2x RAM is just wrong.  The size should be about 4GB for a normal desktop that doesn't hibernate. No larger.
Also, when using commands like free, there's usually a "human output" option so we don't have to count places.  **free -hm** is the output I'd prefer. Same for df and du and even sort.  All have -h (human) options.

I know that many video websites have switched to vp9/hevc as their default format in the last few weeks.  If the hardware and driver aren't specifically setup to decode that video codec in hardware, the CPU will be pegged because it requires more CPU than h.264, the prior "normal" video codec used almost everywhere.  It is possible to specifically ask for h.264, but that's usually too much hassle for most people.  But, my raspberry pi models can't handle decoding hevc/h.265/vp9, so I had to figure out a solution.  Same for my Roku - it does h.264 great, but no h.265 at all.

Again, video sites like youtube switched their default about 2 weeks ago to save bandwidth for hi-def and above videos. They also set the resolution for h.264 videos to be 720p, if that's requested, but 1080p isn't specifically requested.

As for streaming and downloading at the same time, realtek NICs aren't as good at this as most Intel NICs which handle more of the NIC work internally, without using the CPU at nearly the same level as Realtek.

And lastly, if you don't have an SSD for the OS and temporary storage for the two downloads (yes, streams are downloads too), then there can be I/O contention between the different processes.  I'd use **glances** to see an overview of RAM, CPU, I/O, and some other things. Can't hurt to look.

Just some ideas.

---

### Post by ian-weisser on 2023-08-24
> **kabirgandhiok said:**
> 
```

kabir@kabirsubuntu:~$ free
               total        used        free      shared  buff/cache   available
Mem:        16107084     3084360      320620     1261896    12702104    11415692
Swap:       33554428     1052296    32502132

```


Let's dig into that more closely:
16GB RAM but only 0.3G free. Everything else has been committed by the kernel to usage, shared memory, caches, buffers, etc.
Looks like you are experiencing the slowdown as the system begins to swap pages to disk.
It makes sense that when you terminate a memory-hungry application you get an immediate performance improvements as swapping ceases.

@TheFu's suggestions for further investigation (if desired) are, as usual, excellent.

---

### Post by TheFu on 2023-08-24
> **ian-weisser said:**
> Let's dig into that more closely:
16GB RAM but only 0.3G free. Everything else has been committed by the kernel to usage, shared memory, caches, etc.
Looks like you are experiencing the slowdown as the system begins to swap pages to disk.
It makes sense that when you terminate a memory-hungry application you get an immediate performance improvements as swapping ceases.

@TheFu's suggestions for further investigation (if desired) are, as usual, excellent.

Most of the used RAM is being taken by buffers, so not really used.   Only 3.1GB of of real RAM is being used for program needs.  Further, only 1G of swap is being used because using swap for buffers would be foolish.  This assumes I can count places in huge numbers, which is a terrible assumption.  Let the computer do that for us.  Use **free -hm** to make that cleaner.

For my sanity ....
```
               total        used            free        shared     buff/cache    available
Mem:        16,107,084     3,084,360      320,620     1,261,896    12,702,104    11,415,692
Swap:       33,554,428     1,052,296    32,502,132
```
Yep, only 3G used for programs.  It is all being used for buffers.  There is such a thing as having too much swap.
For the most part, buffers get used to make disk access "appear" to be faster.  It can't fix how fast or slow any disk is, just that when a file is accepted to RAM-buffers as it slowly gets written to disk, the command waiting for the write to complete can return, even when the writes to actual storage might take another 2-20 minutes to finish.

Please, please, use the human readable output when it is available. Make life easy for my old eyes.  For example, one of my systems:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi        25Gi       2.2Gi       114Mi       3.3Gi       4.9Gi
Swap:         4.1Gi       1.6Gi       2.5Gi
```
Much easier to see what's happening, right?  RAM being used by programs with a little extra room for some more stuff.  Not too much used for buffers, but it can expand, when desired.  This box had 16GB of RAM a year ago. I had to limit what ran on it to stay below 15GB used.  Swapped in some more RAM and it has been rockin' to a few hours daily of heavy workloads, no issues.  Next to it, is another system, nearly identical.  the RAM use on it is much, much less. See:
```
$ free -hm
              total        used        free      shared  buff/cache   available
Mem:           30Gi       4.3Gi       6.1Gi       159Mi        20Gi        25Gi
Swap:         4.1Gi        42Mi       4.1Gi
```
Lots used for buffers, little used for actual programs. Nearly zero swap used, though if there's any RAM free, I'd rather have ZERO swap used. What's the point?
Also, please note how I follow my own advice for the size of swap?  That's many decades of experience, learning, trial and error.  Actually, inside my virtual machine servers, I only provide a tiny amount of swap when really, I'd rather have zero.  The kernel behaves differently if there isn't any swap (in a negative way), so I tune the amount of RAM provided to cover all server needs, then add just a little swap.  For desktops, it is harder to tune the amount of RAM needed, since a browser can start allocating GB and GB of RAM. I've seen all the major browsers claim to allocate over 60GB of RAM on my systems. Which is impressive since they only had 16GB of RAM and a 4GB swap at the time.  To fix that, I started running browsers in constrained RAM environments. They behave better when there isn't RAM available as far as they can see. I limit firefox to seeing just 10G total RAM.  With about 20 tabs open, it has allocated about 4.5G, but is actively using just 750MB.  Gotta teach these bloated browsers who is the boss or they will suck up RAM and crash.

---

### Post by TenPlus1 on 2023-08-25
This my help, edit /etc/sysctl.conf and add this to the end of the file, save and reboot: vm.swappiness=10

---

### Post by HermanAB on 2023-08-25
The little programs top and ntop will tell you why.

---

### Post by kabirgandhiok on 2023-08-25
Thanks so much for all the suggestions and ideas, @ian-weisser, @TheFu, @TenPlus1, @HermanAB

Some system info:
```

kabir@kabirsubuntu:~$ inxi -Fz
System:
  Kernel: 5.15.0-79-generic x86_64 bits: 64 Desktop: GNOME 42.9
    Distro: Ubuntu 22.04.3 LTS (Jammy Jellyfish)
Machine:
  Type: Laptop System: HP product: HP Laptop 15s-du3xxx
    v: Type1ProductConfigId serial: <superuser required>
  Mobo: HP model: 881D v: 50.27 serial: <superuser required> UEFI: Insyde
    v: F.53 date: 10/15/2021
Battery:
  ID-1: BAT1 charge: 15.5 Wh (43.1%) condition: 36.0/41.0 Wh (87.8%)
    volts: 10.8 min: 11.3
CPU:
  Info: quad core model: 11th Gen Intel Core i5-1135G7 bits: 64 type: MT MCP
    cache: L2: 5 MiB
  Speed (MHz): avg: 843 min/max: 400/4200 cores: 1: 625 2: 536 3: 737
    4: 1063 5: 1107 6: 968 7: 1150 8: 561
Graphics:
  Device-1: Intel TigerLake-LP GT2 [Iris Xe Graphics] driver: i915 v: kernel
  Device-2: Quanta HP TrueVision HD Camera type: USB driver: uvcvideo
  Display: wayland server: X.Org v: 1.22.1.1 with: Xwayland v: 22.1.1
    compositor: gnome-shell driver: X: loaded: modesetting unloaded: fbdev,vesa
    gpu: i915 resolution: 1920x1080~60Hz
  OpenGL: renderer: Mesa Intel Xe Graphics (TGL GT2)
    v: 4.6 Mesa 23.0.4-0ubuntu1~22.04.1
Audio:
  Device-1: Intel Tiger Lake-LP Smart Sound Audio
    driver: sof-audio-pci-intel-tgl
  Sound Server-1: ALSA v: k5.15.0-79-generic running: yes
  Sound Server-2: PulseAudio v: 15.99.1 running: yes
  Sound Server-3: PipeWire v: 0.3.48 running: yes
Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169
  IF: eno1 state: down mac: <filter>
  Device-2: Realtek RTL8822CE 802.11ac PCIe Wireless Network Adapter
    driver: rtw_8822ce
  IF: wlo1 state: up mac: <filter>
Bluetooth:
  Device-1: Realtek Bluetooth Radio type: USB driver: btusb
  Report: hciconfig ID: hci0 rfk-id: 4 state: down
    bt-service: enabled,running rfk-block: hardware: no software: yes
    address: <filter>
RAID:
  Hardware-1: Intel Volume Management Device NVMe RAID Controller driver: vmd
Drives:
  Local Storage: total: 931.51 GiB used: 657.52 GiB (70.6%)
  ID-1: /dev/sda vendor: Toshiba model: MQ04ABF100 size: 931.51 GiB
Partition:
  ID-1: / size: 915.32 GiB used: 657.51 GiB (71.8%) fs: ext4 dev: /dev/sda2
  ID-2: /boot/efi size: 511 MiB used: 6.2 MiB (1.2%) fs: vfat
    dev: /dev/sda1
Swap:
  ID-1: swap-1 type: file size: 32 GiB used: 110.5 MiB (0.3%) file: /swapfile
Sensors:
  System Temperatures: cpu: 27.8 C mobo: 10.0 C
  Fan Speeds (RPM): N/A
Info:
  Processes: 273 Uptime: 2h 3m Memory: 15.36 GiB used: 3.94 GiB (25.6%)
  Shell: Bash inxi: 3.3.13

kabir@kabirsubuntu:~$ free -hm
               total        used        free      shared  buff/cache   available
Mem:            15Gi       2.5Gi       312Mi       1.2Gi        12Gi        11Gi
Swap:           31Gi       110Mi        31Gi

```

@ian-weisser: I feel the slowdown could be related to swap's swappiness setting. As pointed by @TenPlus1 changing swappiness to 10 could help, but I changed it to 100. Did some reading about swappiness and what it does and I think maybe... because I use swap so much since I hibernate my laptop everyday, sometimes multiples times a day. I like all my applications to remain active in their current state so I use the sleep-then-hibernate and have set it to hibernate after sleeping for 30 minutes. Which is why I needed such a large swapfile. Initially I had created a 16GB swapfile @TheFu but that didn't work. Either the system would not hibernate or it would not resume from hibernation, forcing a hard reboot. Replacing that file with a 32GB file works fine, except that whenever I resume from hibernation the CPU loads are through the roof. And Firefox always disappears. I tried reproducing the same behavior upon waking from hibernation after setting swappiness to 100 and so far CPU loads were within limits, Firefox didn't crash. And the slowdown I was experiencing while downloading a torrent alongside video playback which is H.264 codec did not occur yet. Maybe I'm speaking too soon, maybe I've got it backwards. I think I should monitor for a couple of days if this has indeed fixed the problem or not.

---

### Post by MAFoElffen on 2023-08-25
A few notes to add about swaps and swappiness settings. swap partitions are faster than swap files. Debian went to swap file, just because they are more flexible and can be changed easily. The recommended for performance is still a swap partition. Swap should be located on your fastest device. swap can be put on a RAID device, striping across many, to make faster...

The vm.swappiness setting represents the percentage of the free memory before activating swap. The lower the value, the less swapping is used and the more memory pages are kept in physical memory. The current setting is stored at /proc/sys/vm/swappiness. That is where I query to find it.

The default value for vm.swappiness is 60. If not explicitly set in /etc/sysctl.conf, that is what it defaults to. This is how it works:
```

0 -- turns it off
1 -- lowest value without turning it off. Recommended setting by MariaDB.
10 -- Improves performance for machines with "enough memory". Recommended by Oracle DB. Recommended 'start point' for system tuning by RedHat.
60 -- Default. Compromise value that works well for most modern desktop systems. (Servers should be set as less.)
100 -- Aggressive paging.

```
Like I said, just mentioning some notes.

I tweak my settings for physical and virtual machines. I do a lot of testing, where I have crashed machines running out of memory. When I do, I just bump up the ceiling a little higher. On my servers: I locate swap partitions on PCIe NVMe. Others: On SSD.

Note that for my servers, I try to use 'separate' devices for disk caches and for swap... I want the throughput unhampered and not having to compete with something else.

---

### Post by kabirgandhiok on 2023-08-25
> **MAFoElffen said:**
> A few notes to add about swaps and swappiness settings. swap partitions are faster than swap files. Debian went to swap file, just because they are more flexible and can be changed easily. The recommended for performance is still a swap partition. Swap should be located on your fastest device. swap can be put on a RAID device, striping across many, to make faster...

The vm.swappiness setting represents the percentage of the free memory before activating swap. The lower the value, the less swapping is used and the more memory pages are kept in physical memory. The current setting is store at /proc/sys/vm/swappiness. That is where I query to find it.

The default value for vm.swappiness is 60. If not set in /etc/sysctl.conf, that is what it defaults to. This is how it works:
```

0 -- turns it off
1 -- lowest value without turning it off. Recommended setting by MariaDB.
10 -- Improves performance for machines with "enough memory". Recommended by Oracle DB. Recommended 'start point' for system tuning by RedHat.
60 -- Default. Compromise value that works well for most modern desktop systems. (Servers should be set as less.)
100 -- Aggressive paging.

```
Like I said, just mentioning some notes.

I tweak my settings for physical and virtual machines. I do a lot of testing, where I have crashed machines running out of memory. When I do, I just bump up the ceiling a little higher. On my servers: I locate swap partitions on PCIe NVMe. Others: On SSD.
Very interesting, thanks for that. Setting swappiness to 100 made the slowdown worse. I will test it at 10 and see if that helps. My system doesn't have an SSD yet. There is a slot for an NVMe PCIe stick but I have not utilized it as yet. So if I get a PCIe NVMe stick and use that for a swap partition, while getting rid of the swapfile, perhaps it will make a big difference?

---

### Post by MAFoElffen on 2023-08-25
You can test is temporarily with the systctl command...
```

sudo sysctl -w vm.swappiness=10

```
Is the same as saying
```

sudo echo "10" > /proc/sys/vm/swappiness

```
That way, you do not have to reboot between tests...

When you find what works best for the specific machine with it's workload, then add the setting to /etc/sysctl.conf, in a line similar to
```

vm.swappiness = 10

```
That will make the setting persistent.

---

### Post by kabirgandhiok on 2023-08-25
> **MAFoElffen said:**
> You can test is temporarily with the systctl command...
```

sudo sysctl -w vm.swappiness=10

```
Is the same as saying
```

sudo echo "10" > /proc/sys/vm/swappiness

```
That way, you do not have to reboot between tests...

When you find what works best for the specific machine with it's workload, then add the setting to /etc/sysctl.conf, in a line similar to
```

vm.swappiness = 10

```
That will make the setting persistent.

Thanks but swappiness at 10 doesn't help either, slowdown occurs within minutes of torrent downloading and video playback. Maybe I need a partition instead of a swapfile?

---

### Post by MAFoElffen on 2023-08-25
What I notice with the stats you posted --> You use your swap. 

You just need to play with your swap size, how it is implemented (I would recommend going to a swap partition instead of a file) and tune your vm.swapiness to find out what works best for you.

Before going to a swap partition, play with differing swap file sizes. That is the strength of a swap file, is that it is easily changeable. That way you can change the size to find that "size" what works best for you, then convert it to a swap partition.

The thing about swap, is you can't really screw it up. What is inside it is "not important" in the long run... It's not like, oh dang, i lost this file located in my swap. LOL

The only time it is important for persistence, is on Desktop, when you wakeup from suspend/hibernate. But if it is corrupted, it still doesn't brick permanently. It is not a show stopper.

---

### Post by kabirgandhiok on 2023-08-25
> **MAFoElffen said:**
> What I notice with the stats you posted --> You use your swap. 

You just need to play with your swap size, how it is implemented (I would recommend going to a swap partition instead of a file) and tune your vm.swapiness to find out what works best for you.

Before going to a swap partition, play with differing swap file sizes. That is the strength of a swap file, is that it is easily changeable. That way you can change the size to find that "size" what works best for you, then convert it to a swap partition.

The thing about swap, is you can't really screw it up. What is inside it is "not important" in the long run... It's not like, oh dang, i lost this file located in my swap. LOL

The only time it is important for persistence, is on Desktop, when you wakeup from suspend/hibernate. But if it is corrupted, it still doesn't brick permanently. It is not a show stopper.

okay.. so I should increase my swapfile size, but is it possible that 32GB of swap in a partition would be about as efficient to say what 64GB would be in a swapfile format?

---

### Post by MAFoElffen on 2023-08-25
Is this on a laptop? What brand/model? Does it have an optical drive or WWAN port?

---

### Post by #&amp;thj^% on 2023-08-25
> **MAFoElffen said:**
> 
You just need to play with your swap size, how it is implemented (I would recommend going to a swap partition instead of a file) and tune your vm.swapiness to find out what works best for you.

The thing about swap, is you can't really screw it up. What is inside it is "not important" in the long run... It's not like, oh dang, i lost this file located in my swap. LOL

The only time it is important for persistence, is on Desktop, when you wakeup from suspend/hibernate. But if it is corrupted, it still doesn't brick permanently. It is not a show stopper.
Indeed Play Away:
```
 swapon -s
Filename		                        Type	        Size	        Used	Priority
/dev/nvme0n1p2                          partition	16634876	256	-3
/dev/nvme1n1p2                          partition	2097148	512	-2
/dev/dm-1                               partition	1998844	0	-4

```
Just some of the possibles.

> **kabirgandhiok said:**
> okay.. so I should increase my swapfile size, but is it possible that 32GB of swap in a partition would be about as efficient to say what 64GB would be in a swapfile format?

From the end-user perspective, swap files in higher Linux kernel versions are virtually as fast as swap partitions. Of course, the swap file should be contiguous to provide the same speed as a partition.

Also, there are a few things that the kernel does to increase the performance of swap files: Source: [https://www.baeldung.com/linux/swap-file-partition](https://www.baeldung.com/linux/swap-file-partition)

---

### Post by MAFoElffen on 2023-08-25
+1 -- That and some other issues.

If located on a spun-disk, it is faster if located near the outside of the platters (end of disk).

If there is encryption involved, where the swap is located and if it is encrypted...

If used with a Volume Manager, "the location of" is important, because when you do a snapshot, the swap needs to be excluded from the snapshot...

Etc...

---

### Post by Doug S on 2023-08-25
Just a completely different thought... Have you monitored your CPU frequencies before, and during, these slow downs? Is your system throttling down to protect itself against excessive temperatures and/or power use?
I use turbostat (linux-tools-common package, I think) to monitor things. Example:

```

sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt,CorWatt --interval 30
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt RAMWatt
0.60    4795    170908  40      17.14   16.49   0.00    1.45
7.43    4800    193741  55      27.32   26.49   0.00    2.51
8.70    4800    196948  54      29.50   28.63   0.00    2.71
2.25    4800    173871  42      19.34   18.64   0.00    1.73
0.38    4800    167859  41      16.38   15.73   0.00    1.45

```And if you delete the --quiet option, you will get a big spew of stuff on startup that will include some of the limits. Edited example:

```

...
cpu11: MSR_TURBO_RATIO_LIMIT: 0x2f3030303030
47 * 100.0 = 4700.0 MHz max turbo 6 active cores
48 * 100.0 = 4800.0 MHz max turbo 5 active cores
48 * 100.0 = 4800.0 MHz max turbo 4 active cores
48 * 100.0 = 4800.0 MHz max turbo 3 active cores
48 * 100.0 = 4800.0 MHz max turbo 2 active cores
48 * 100.0 = 4800.0 MHz max turbo 1 active cores
...
cpu0: MSR_PKG_POWER_INFO: 0x000003e8 (125 W TDP, RAPL 0 - 0 W, 0.000000 sec.)
cpu0: MSR_PKG_POWER_LIMIT: 0x428440001b83e8 (UNlocked)
cpu0: PKG Limit #1: ENabled (125.000 Watts, 8.000000 sec, clamp ENabled)
cpu0: PKG Limit #2: ENabled (136.000 Watts, 0.002441* sec, clamp DISabled)
...
cpu0: MSR_IA32_TEMPERATURE_TARGET: 0x19641422 (75 C) (100 default - 25 offset)
```

Note: I use the TCC offset method of Thermal limiting. As far as I know: Very few users know about it; It is not available for all Intel Processors.

---

### Post by TheFu on 2023-08-25
Hibernating to a swapfile used to have "issues". IDK if that still exists or not.  I've never used a swapfile, at least, not on purpose.

I completely understand trying 16G, seeing crashes/failures, so just double it.  Perhaps making it 17G would be better?

Looking over the inxi output ... some things I see and vaguely remember.

There was/is a problem with Iris Xe Graphics hardware. I don't recall if it was solved or not, nor how well Wayland is supported with it. For stability, perhaps X11 would be better?

There was a problem with Intel's RAID for NVMe.  In general, storage should be put into AHCI mode, never RAID.

 / size: 915.32G ... that's something I'd never do.  / should be 35-45G, no larger. This should be more than sufficient to hold an OS for 10 yrs. Pre-20.04, 20GB was sufficient. I split storage into different areas for backup and security reasons. A file system can map to a partition for simple setups and a file system is the smallest way that different mount options can be used to improve security.  

Additionally, if you use more advanced volume managers, a file system would be placed onto a volume and support snapshots.  Snapshots are what make perfect backups for running systems possible. Without a snapshot, there's a risk of some files being corrupted in the backup set.

Anyway, I've posted my disk layouts in these forums a number of times, showing where different parts are split onto different file systems and the sizes for each.

I'm so sorry that you have Realtek network devices.  Perhaps we see issues with these all the time because they are so popular. But I've had enough issues with Realtek to avoid them completely.  I use Intel NICs now and that ended driver and hardware issues that seemed to always happen with Realtek.

Again, I don't recall specifics or know if they've been solved. I just recall some issue causing problems with some of that hardware. Perhaps others here have more recent details and know these things work perfect now?

---

### Post by TheFu on 2023-08-25
> **kabirgandhiok said:**
> okay.. so I should increase my swapfile size, but is it possible that 32GB of swap in a partition would be about as efficient to say what 64GB would be in a swapfile format?

```
$ free -hm
               total        used        free      shared  buff/cache   available
Mem:            15Gi       2.5Gi       312Mi       1.2Gi        12Gi        11Gi
Swap:           31Gi       110Mi        31Gi

```
I see exactly the opposite.  Swap is barely being used from the data posted.  Only because he hibernates and has 16G of RAM would swap be significantly used.  Any more than 17GB is overkill and a waste.  However, I would move away from a swap file and setup a swap partition or LV. Call me old fashioned. I'm slow to change from things that are well understood.  Swap files on Linux are relatively new. Swap partitions have been used since the beginning. 1991.

---

### Post by #&amp;thj^% on 2023-08-25
> **TheFu said:**
> Hibernating to a swapfile used to have "issues". IDK if that still exists or not.  I've never used a swapfile, at least, not on purpose.


It still does, and that's important to say, good catch..

---

### Post by #&amp;thj^% on 2023-08-25
> **Doug S said:**
> Just a completely different thought... Have you monitored your CPU frequencies before, and during, these slow downs? Is your system throttling down to protect itself against excessive temperatures and/or power use?
I use turbostat (linux-tools-common package, I think) to monitor things. Example:

```

sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt,CorWatt --interval 30
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt RAMWatt
0.60    4795    170908  40      17.14   16.49   0.00    1.45
7.43    4800    193741  55      27.32   26.49   0.00    2.51
8.70    4800    196948  54      29.50   28.63   0.00    2.71
2.25    4800    173871  42      19.34   18.64   0.00    1.73
0.38    4800    167859  41      16.38   15.73   0.00    1.45

```And if you delete the --quiet option, you will get a big spew of stuff on startup that will include some of the limits. Edited example:

Note: I use the TCC offset method of Thermal limiting. As far as I know: Very few users know about it; It is not available for all Intel Processors.

Doug Why is your core watts so high? just curious is all?
```
Busy%	Bzy_MHz	IRQ	CorWatt	PkgWatt
4.68	1886	156875	0.72	4.46
5.90	2016	184387	1.05	4.85
8.03	2291	236908	1.76	5.63
8.52	2227	249862	1.85	5.70
7.13	2019	219953	1.33	5.10
6.25	1956	200085	1.06	4.82
6.63	2139	208366	1.28	5.07
5.51	1975	179806	0.95	4.68
^C5.65	1996	169270	0.99	4.75

```

---

### Post by MAFoElffen on 2023-08-25
I see that he is using his swap, but only at around 12GB. He has 16GB of RAM... That means his workload RAM is around 28GB??? Seems to be working it.

My old ThinkPad T520 is 8GB RAM with 32GB of swap. That is 3 times the system RAM. Why that allocated that large? Because i also have KVM installed on that and routinely over-allocate RAM on it (on purpose). I am not your normal user. 

I would have expected it to slow down, BUT-- I do not suffer from it running slowly at all.
```

mafoelffen@Mikes-ThinkPad-T520:~$ lsblk -e7 -o name,label,size,fstype,mountpoint,model
NAME     LABEL       SIZE FSTYPE     MOUNTPOINT MODEL
sda                  1.8T                       Samsung SSD 870 QVO 2TB
&#9500;&#9472;sda1   {SYSTEM}    550M vfat       /boot/efi  
&#9500;&#9472;sda2               128M                       
&#9500;&#9472;sda3   {Windows}   900G ntfs                  
&#9500;&#9472;sda4               983M                       
&#9500;&#9472;sda5                30G                       
&#9500;&#9472;sda6                32G                       
&#9474; &#9492;&#9472;swap swap         32G swap       [SWAP]     
&#9500;&#9472;sda7   bpool         2G zfs_member            
&#9500;&#9472;sda8   rpool       500G zfs_member            
&#9492;&#9472;sda9   hpool     397.4G zfs_member            
sdb                  1.8T                       Samsung SSD 870 QVO 2TB
&#9500;&#9472;sdb1   kpool      1000G zfs_member            
&#9492;&#9472;sdb2   dpool       863G zfs_member            
sdc                  1.8T                       Dogfish SSD 2TB
&#9492;&#9472;sdc1   backups     1.5T zfs_member            

```

---

### Post by Doug S on 2023-08-25
> **1fallen said:**
> Doug Why is your core watts so high? just curious is all?
```
Busy%	Bzy_MHz	IRQ	CorWatt	PkgWatt
4.68	1886	156875	0.72	4.46
5.90	2016	184387	1.05	4.85
8.03	2291	236908	1.76	5.63
8.52	2227	249862	1.85	5.70
7.13	2019	219953	1.33	5.10
6.25	1956	200085	1.06	4.82
6.63	2139	208366	1.28	5.07
5.51	1975	179806	0.95	4.68
^C5.65	1996	169270	0.99	4.75

```The power is high because I am at the top of my turbo range for CPU frequency and power use is rather non-linear in the turbo range.
I am 4 hours into a test, and am using the performance governor just to try to shorten it a little. For my post I also added 1 CPU at 100% load for a couple of minutes (12 CPUs, so 100% on 1 = 8.33% added overall).
The attached graph shows the non-linear power curve. It is an old graph, and for a different processor (i5-9600K).
[ATTACH=CONFIG]292645[/ATTACH]

On my test server most power consumption is via the cores, so it is usually close to the package power.

EDIT: An example of ~8.5% busy, but with lower CPU frequency:

```

doug@s19:~$ sudo turbostat --Summary --quiet --show Busy%,Bzy_MHz,IRQ,PkgWatt,PkgTmp,RAMWatt,GFXWatt,CorWatt --interval 60
Busy%   Bzy_MHz IRQ     PkgTmp  PkgWatt CorWatt GFXWatt RAMWatt
8.52    800     62173   35      2.25    1.61    0.00    1.75
8.52    800     61786   34      2.22    1.59    0.00    1.75
8.52    800     61872   34      2.12    1.49    0.00    1.75

```

OP: apologies for the tangent on your thread.

---

### Post by #&amp;thj^% on 2023-08-25
> **Doug S said:**
> The power is high because I am at the top of my turbo range for CPU frequency and power use is rather non-linear in the turbo range.
I am 4 hours into a test, and am using the performance governor just to try to shorten it a little. For my post I also added 1 CPU at 100% load for a couple of minutes (12 CPUs, so 100% on 1 = 8.33% added overall).
The attached graph shows the non-linear power curve. It is an old graph, and for a different processor (i5-9600K).
[ATTACH=CONFIG]292645[/ATTACH]

On my test server most power consumption is via the cores, so it is usually close to the package power.
I should have guessed that.:(
Thanks Doug S
> **Doug S said:**
> 
OP: apologies for the tangent on your thread.
+1

---

### Post by kabirgandhiok on 2023-08-26
You all have given me a lot to think about but the one suggestion that stands out is to get a swap partition.

@Doug S when the slowdowns happen I just run sensors on the terminal and it shows CPU temps within limits. Also, the kernel has no control over the fans on my system. They are entirely controlled by the bios, so I have set fans to always on in the bios settings. The fans spin up whenever the grub shows up at boot and if the system temps rise above 60C or so. 

```

kabir@kabirsubuntu:~$ sensors
BAT1-acpi-0
Adapter: ACPI interface
in0:          13.03 V  

coretemp-isa-0000
Adapter: ISA adapter
Package id 0:  +45.0°C  (high = +100.0°C, crit = +100.0°C)
Core 0:        +43.0°C  (high = +100.0°C, crit = +100.0°C)
Core 1:        +43.0°C  (high = +100.0°C, crit = +100.0°C)
Core 2:        +41.0°C  (high = +100.0°C, crit = +100.0°C)
Core 3:        +38.0°C  (high = +100.0°C, crit = +100.0°C)

acpitz-acpi-0
Adapter: ACPI interface
temp1:        +27.8°C  (crit = +119.0°C)
temp2:        +10.0°C  

```

I did run sensors-detect on the LTS as well as 6.2 kernel but I never get any fan readings. To test the fans, I open countless tabs on Firefox, with youtube videos playing in all of them. That does the trick.

@1fallen, @MAFoElffen Today all day I've kept swappiness at 50, while trying to reproduce the same behavior. It did ever so slightly slowdown, but recovered after a few seconds. Maybe I should test some more at 50. Here's a thought @TheFu, is it possible the slowdown may begin to happen more visibly after 4 or 5 days of daily hibernation, irrespective of what setting I have on swappiness? Another question that's been on my mind, the disk on the system is almost full could that contribute to the slowdown?

```

kabir@kabirsubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           1.6G  2.3M  1.6G   1% /run
/dev/sda2       916G  702G  168G  81% /
tmpfs           7.7G     0  7.7G   0% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
/dev/sda1       511M  6.3M  505M   2% /boot/efi
tmpfs           1.6G  156K  1.6G   1% /run/user/1000

```

Is it possible that being at 81% whenever I download anything onto /dev/sda2 while simultaneously accessing data (video playback) from it, it slows down? If not, then I guess ultimately if the slowdown keep reoccurring a partition for swap would be the only way out. This is the first time I'm using a swap file. I've always had a partition for swap on this very system and not faced any slowdowns at all. I just went with the file because a swap partition was not installed by default or I might have skipped it. And I had never tried a swapfile so I thought of giving it a go.

---

### Post by Doug S on 2023-08-27
> **kabirgandhiok said:**
> Is it possible that being at 81% whenever I download anything onto /dev/sda2 while simultaneously accessing data (video playback) from it, it slows down?
From and earlier post, your disk is a HDD spinning at 5400 r.p.m. (MQ04ABF100). Conceivably, your seek times, which would already be a limiting factor, could become longer for a fuller disk.
By doing 2 things at the same time on your disk, it will be absolutely throughput limited by seek time limitations, as it will be going back and forth between the read file and the write file.
(I'll edit this post later with some supporting data, if I am able to get some.)

EDIT: While not the greatest example, I used some tools I already had to try to show an example. It did not work, I got similar average seek times for an 800 Gigabyte file as with a 100 Gigabyte file:

```

doug@s19:/media/sdb/bla$ ~/c/read_random_big
read_random_big: total bytes in file "big" (a compile time number): 858993459200  multiplier: 400
read_random_big:   1984 seeks: (   66 /s (last)) elapsed time:    30.0 seconds user cpu:   0.00 s. sys cpu:   0.13 s. longest seek:  0.090 s.
read_random_big:   3940 seeks: (   65 /s (last)) elapsed time:    60.0 seconds user cpu:   0.01 s. sys cpu:   0.28 s. longest seek:  0.090 s.
read_random_big:   5903 seeks: (   65 /s (last)) elapsed time:    90.0 seconds user cpu:   0.02 s. sys cpu:   0.43 s. longest seek:  0.090 s.
read_random_big:   7844 seeks: (   65 /s (last)) elapsed time:   120.0 seconds user cpu:   0.03 s. sys cpu:   0.57 s. longest seek:  0.090 s.

doug@s19:/media/sdb/bla$ ~/c/read_random_big
read_random_big: total bytes in file "big" (a compile time number): 107374182400  multiplier: 50
read_random_big:   1926 seeks: (   64 /s (last)) elapsed time:    30.0 seconds user cpu:   0.00 s. sys cpu:   0.14 s. longest seek:  0.240 s.
read_random_big:   3865 seeks: (   65 /s (last)) elapsed time:    60.0 seconds user cpu:   0.00 s. sys cpu:   0.28 s. longest seek:  0.240 s.
read_random_big:   5790 seeks: (   64 /s (last)) elapsed time:    90.0 seconds user cpu:   0.01 s. sys cpu:   0.41 s. longest seek:  0.240 s.
read_random_big:   7694 seeks: (   63 /s (last)) elapsed time:   120.0 seconds user cpu:   0.01 s. sys cpu:   0.55 s. longest seek:  0.240 s.

```

The above disk was a HDD at 7200 r.p.m.
Myself, I was surprised that your disk is an HDD instead of an SSD or NVME (SSD), as I noticed that your processor is 11th Gen Intel (i.e. fairly new motherboard).
Here is an example of seek times on my test servers NMVE SSD drive, where it doesn't actually have to physically move the heads to the cylinder and sector at all:

```

doug@s19:~/tmp$ ~/c/read_random_big
read_random_big: total bytes in file "big" (a compile time number): 107374182400  multiplier: 50
read_random_big: 754847 seeks: (25162 /s (last)) elapsed time:    30.0 seconds user cpu:   0.18 s. sys cpu:   2.00 s. longest seek:  0.010 s.
read_random_big:1506072 seeks: (25041 /s (last)) elapsed time:    60.0 seconds user cpu:   0.35 s. sys cpu:   3.97 s. longest seek:  0.010 s.
read_random_big:2246465 seeks: (24680 /s (last)) elapsed time:    90.0 seconds user cpu:   0.51 s. sys cpu:   5.92 s. longest seek:  0.010 s.
read_random_big:2971303 seeks: (24161 /s (last)) elapsed time:   120.0 seconds user cpu:   0.66 s. sys cpu:   7.87 s. longest seek:  0.010 s.

```

EDIT 2: Back to the HDD seeks times: My previous results were bugging me, so I did another test where I knew the 100G file and its directory would be close by each other physically on the disk and not be fragmented (which isn't typically a thing in linux anyhow) l spanning a bunch of other stuff. Then I got ~2.4 times improvement. The first one is slow because it had to go far away to read parent directory information once on startup, I assume:

```

doug@s19:/media/sdb/bla/bla$ ~/c/read_random_big
read_random_big: total bytes in file "big" (a compile time number): 107374182400  multiplier: 50
read_random_big:   2647 seeks: (   88 /s (last)) elapsed time:    30.0 seconds user cpu:   0.00 s. sys cpu:   0.14 s. longest seek:  0.400 s.
read_random_big:   7205 seeks: (  152 /s (last)) elapsed time:    60.0 seconds user cpu:   0.02 s. sys cpu:   0.37 s. longest seek:  0.400 s.
read_random_big:  11859 seeks: (  155 /s (last)) elapsed time:    90.0 seconds user cpu:   0.03 s. sys cpu:   0.62 s. longest seek:  0.400 s.
read_random_big:  16422 seeks: (  152 /s (last)) elapsed time:   120.0 seconds user cpu:   0.03 s. sys cpu:   0.89 s. longest seek:  0.400 s.
read_random_big:  21005 seeks: (  153 /s (last)) elapsed time:   150.0 seconds user cpu:   0.05 s. sys cpu:   1.15 s. longest seek:  0.400 s.
read_random_big:  25547 seeks: (  151 /s (last)) elapsed time:   180.0 seconds user cpu:   0.06 s. sys cpu:   1.41 s. longest seek:  0.400 s.
read_random_big:  30171 seeks: (  154 /s (last)) elapsed time:   210.0 seconds user cpu:   0.08 s. sys cpu:   1.65 s. longest seek:  0.400 s.

```

EDIT 3: If I write a file to my HDD at the same time as I am reading another file, the read speed drops by a factor of about 12:
```

doug@s19:/media/sdb/bla/bla$ /media/sda/test/testreadbig
Completed 1 gig loops:    1  : Last time: 6.980000 seconds  : Last rate: 146.704871 Mega Bytes per second
Completed 1 gig loops:    2  : Last time: 6.780000 seconds  : Last rate: 151.032448 Mega Bytes per second  [COLOR="#FF0000"]<<< Nothing else going on on this disk[/COLOR]
Completed 1 gig loops:    3  : Last time: 6.920000 seconds  : Last rate: 147.976879 Mega Bytes per second
Completed 1 gig loops:    4  : Last time: 6.800000 seconds  : Last rate: 150.588235 Mega Bytes per second
Completed 1 gig loops:    5  : Last time: 6.850000 seconds  : Last rate: 149.489051 Mega Bytes per second
Completed 1 gig loops:    6  : Last time: 6.820000 seconds  : Last rate: 150.146628 Mega Bytes per second
Completed 1 gig loops:    7  : Last time: 6.830000 seconds  : Last rate: 149.926794 Mega Bytes per second
Completed 1 gig loops:    8  : Last time: 12.100000 seconds  : Last rate: 84.628099 Mega Bytes per second
Completed 1 gig loops:    9  : Last time: 79.720000 seconds  : Last rate: 12.844957 Mega Bytes per second
Completed 1 gig loops:   10  : Last time: 92.320000 seconds  : Last rate: 11.091854 Mega Bytes per second
Completed 1 gig loops:   11  : Last time: 84.720000 seconds  : Last rate: 12.086874 Mega Bytes per second  [COLOR="#FF0000"]<<< Another task is writing a file as fast as it can[/COLOR]
Completed 1 gig loops:   12  : Last time: 83.960000 seconds  : Last rate: 12.196284 Mega Bytes per second
Completed 1 gig loops:   13  : Last time: 82.010000 seconds  : Last rate: 12.486282 Mega Bytes per second
Completed 1 gig loops:   14  : Last time: 82.680000 seconds  : Last rate: 12.385099 Mega Bytes per second
Completed 1 gig loops:   15  : Last time: 93.190000 seconds  : Last rate: 10.988303 Mega Bytes per second

```
I do not know how close your applications are to any limits, so don't know if you would see this or not.

---

### Post by MAFoElffen on 2023-08-27
I happen to feel that Doug S & TheFu have some things to look into further...

TheFu on the OP's NIC type (RealTec). 
```

Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169
  IF: eno1 state: down mac: <filter>
  Device-2: Realtek RTL8822CE 802.11ac PCIe Wireless Network Adapter
    driver: rtw_8822ce
  IF: wlo1 state: up mac: <filter>

```
Unfortunately-- Since a laptop he has no choice on changing that. Streaming involves downloading and network throughput. There are some options for trying to tune that, but he is still going to hit the limits of that hardware. Especially since he is doing Wireless Networking, not Wired.

Doug S.'es options have some possibilities... Really curious on seeing more details of that, and to see if that is related to what is going on here.

---

### Post by TheFu on 2023-08-28
> **MAFoElffen said:**
> I happen to feel that Doug S & TheFu have some things to look into further...

TheFu on the OP's NIC type (RealTec). 
```

Network:
  Device-1: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet
    driver: r8169
  IF: eno1 state: down mac: <filter>
  Device-2: Realtek RTL8822CE 802.11ac PCIe Wireless Network Adapter
    driver: rtw_8822ce
  IF: wlo1 state: up mac: <filter>

```
Unfortunately-- Since a laptop he has no choice on changing that. Streaming involves downloading and network throughput. There are some options for trying to tune that, but he is still going to hit the limits of that hardware. Especially since he is doing Wireless Networking, not Wired.

He does have a choice. For $10-$20, a USB wifi adapter that fully supports Linux are available.

I don't use realtek, nor wifi.  I have seen mention to disable power saving in wifi to improve performance.  I specifically avoid realtek. The $20 savings isn't worth even 1 trouble as far as I'm concerned.  Just not something I want to waste time over. It is a problem easily avoided, so I do.

I had a system with that specific realtek NIC for wired connections. Worked fine for a few years, then it started dropping packets and eventually it failed.  I replaced it with an Intel PRO/1000 NIC and then added a 4-port Intel NIC as my networking needs became more complex.  Can't think of any time when I've had issues with Intel GigE NICs with any OS.  The BSDs all work better with Intel, for example.

---

### Post by MAFoElffen on 2023-08-28
@TheFu --- +1, Yes.  

Most my machines here, I run Intel NIC's. My GigaByte server has RealTek. It is running 22.04.3:
```

mafoelffen@Mikes-B460M:~$ speedtest-cli
Retrieving speedtest.net configuration...
Testing from Comcast Cable (71.197.252.194)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Ziply Fiber (Bothell, WA) [85.17 km]: 28.923 ms
[COLOR=#ff0000]Testing download speed................................................................................
Download: 267.46 Mbit/s
Testing upload speed......................................................................................................
Upload: 5.85 Mbit/s
[/COLOR]mafoelffen@Mikes-B460M:~$ sudo lshw -C network
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:0c:00.0
       logical name: enp12s0
       version: 16
       serial: 18:c0:4d:3f:4d:d5
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=6.2.0-26-generic duplex=full firmware=rtl8168h-2_0.0.2 02/26/15 ip=10.0.0.3 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:16 ioport:3000(size=256) memory:b1804000-b1804fff memory:b1800000-b1803fff
  *-network
       description: Wireless interface
       product: Dual Band Wireless-AC 3168NGW [Stone Peak]
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:0d:00.0
       logical name: wlp13s0
       version: 10
       serial: 58:a0:23:dc:fd:ca
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=6.2.0-26-generic firmware=29.198743027.0 3168-29.ucode ip=10.0.0.229 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:285 memory:b1700000-b1701fff
3000(size=256) memory:b1804000-b1804fff memory:b1800000-b1803fff

```
Those specs compared with my workstation, which is Intel, also 22.04.3:
```

mafoelffen@msi-ubuntu:~$ speedtest-cli
Retrieving speedtest.net configuration...
Testing from Comcast Cable (71.197.252.194)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Ziply Fiber (Bothell, WA) [85.17 km]: 30.983 ms
[COLOR=#ff0000]Testing download speed................................................................................
Download: 398.53 Mbit/s
Testing upload speed......................................................................................................
Upload: 5.10 Mbit/s
[/COLOR]mafoelffen@msi-ubuntu:~$ sudo lshw -c network
  *-network                 
       description: Wireless interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 14.3
       bus info: pci@0000:00:14.3
       logical name: wlo1
       version: 11
       serial: a4:f9:33:cc:0e:d9
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=6.2.0-26-generic firmware=72.a764baac.0 so-a0-gf-a0-72.uc ip=10.0.0.11 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:74e1c000-74e1ffff
  *-network
       description: Ethernet interface
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: enp6s0
       version: 04
       serial: 04:7c:16:c3:58:a0
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list ethernet physical 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igc driverversion=6.2.0-26-generic duplex=full firmware=2017:888d ip=10.0.0.5 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:16 memory:74600000-746fffff memory:74700000-74703fff
  *-network:0
       description: Ethernet interface
       product: 82576 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: enp9s0f0
       version: 01
       serial: 1c:fd:08:79:e8:0e
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=6.2.0-26-generic duplex=full firmware=1.2.1 latency=0 link=yes multicast=yes port=twisted pair speed=1Gbit/s
       resources: irq:16 memory:74420000-7443ffff memory:74000000-743fffff ioport:3020(size=32) memory:74444000-74447fff memory:73c00000-73ffffff memory:74448000-74467fff memory:74468000-74487fff
  *-network:1
       description: Ethernet interface
       product: 82576 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 0.1
       bus info: pci@0000:09:00.1
       logical name: enp9s0f1
       version: 01
       serial: 1c:fd:08:79:e8:0f
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi msix pciexpress bus_master cap_list rom ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=igb driverversion=6.2.0-26-generic firmware=1.2.1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:17 memory:74400000-7441ffff memory:73800000-73bfffff ioport:3000(size=32) memory:74440000-74443fff memory:73400000-737fffff memory:74488000-744a7fff memory:744a8000-744c7fff
  *-network:2
       description: Ethernet interface
       product: 82576 Virtual Function
       vendor: Intel Corporation
       physical id: 10
       bus info: pci@0000:09:10.0
       logical name: enp9s0f0v0
       version: 01
       serial: e6:66:b4:2d:4b:44
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: msix pciexpress bus_master cap_list ethernet physical 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic duplex=full ip=10.0.0.10 latency=0 link=yes multicast=yes speed=1Gbit/s
       resources: irq:0 memory:74448000-7444bfff memory:74468000-7446bfff
  *-network:3 DISABLED
       description: Ethernet interface
       product: 82576 Virtual Function
       vendor: Intel Corporation
       physical id: 10.1
       bus info: pci@0000:09:10.1
       logical name: enp9s0f1v0
       version: 01
       serial: 56:b2:18:6f:d5:65
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: msix pciexpress bus_master cap_list ethernet physical 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic latency=0 link=no multicast=yes
       resources: irq:0 memory:74488000-7448bfff memory:744a8000-744abfff
  *-network:4
       description: Ethernet interface
       product: 82576 Virtual Function
       vendor: Intel Corporation
       physical id: 10.2
       bus info: pci@0000:09:10.2
       logical name: enp9s0f0v1
       version: 01
       serial: 5e:78:5f:90:e1:09
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: msix pciexpress bus_master cap_list ethernet physical 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic duplex=full ip=10.0.0.11 latency=0 link=yes multicast=yes speed=1Gbit/s
       resources: irq:0 memory:7444c000-7444ffff memory:7446c000-7446ffff
  *-network:5 DISABLED
       description: Ethernet interface
       product: 82576 Virtual Function
       vendor: Intel Corporation
       physical id: 10.3
       bus info: pci@0000:09:10.3
       logical name: enp9s0f1v1
       version: 01
       serial: 9a:87:35:b4:b9:4f
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: msix pciexpress bus_master cap_list ethernet physical 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic latency=0 link=no multicast=yes
       resources: irq:0 memory:7448c000-7448ffff memory:744ac000-744affff
  *-network:6
       description: Ethernet interface
       product: 82576 Virtual Function
       vendor: Intel Corporation
       physical id: 10.4
       bus info: pci@0000:09:10.4
       logical name: enp9s0f0v2
       version: 01
       serial: de:39:ab:9a:db:58
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: msix pciexpress bus_master cap_list ethernet physical 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic duplex=full ip=10.0.0.12 latency=0 link=yes multicast=yes speed=1Gbit/s
       resources: irq:0 memory:74450000-74453fff memory:74470000-74473fff
  *-network:7 DISABLED
       description: Ethernet interface
       product: 82576 Virtual Function
       vendor: Intel Corporation
       physical id: 10.5
       bus info: pci@0000:09:10.5
       logical name: enp9s0f1v2
       version: 01
       serial: 86:19:1d:f1:b2:7c
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: msix pciexpress bus_master cap_list ethernet physical 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic latency=0 link=no multicast=yes
       resources: irq:0 memory:74490000-74493fff memory:744b0000-744b3fff
  *-network:8
       description: Ethernet interface
       product: 82576 Virtual Function
       vendor: Intel Corporation
       physical id: 10.6
       bus info: pci@0000:09:10.6
       logical name: enp9s0f0v3
       version: 01
       serial: 52:5d:78:fa:d3:14
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: msix pciexpress bus_master cap_list ethernet physical 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic duplex=full ip=10.0.0.13 latency=0 link=yes multicast=yes speed=1Gbit/s
       resources: irq:0 memory:74454000-74457fff memory:74474000-74477fff
  *-network:9 DISABLED
       description: Ethernet interface
       product: 82576 Virtual Function
       vendor: Intel Corporation
       physical id: 10.7
       bus info: pci@0000:09:10.7
       logical name: enp9s0f1v3
       version: 01
       serial: 6a:97:7c:ac:75:ef
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: msix pciexpress bus_master cap_list ethernet physical 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic latency=0 link=no multicast=yes
       resources: irq:0 memory:74494000-74497fff memory:744b4000-744b7fff
  *-network:10
       description: Ethernet interface
       product: 82576 Virtual Function
       vendor: Intel Corporation
       physical id: 11
       bus info: pci@0000:09:11.0
       logical name: enp9s0f0v4
       version: 01
       serial: 96:14:e8:98:6f:7b
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: msix pciexpress bus_master cap_list ethernet physical 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic duplex=full ip=10.0.0.14 latency=0 link=yes multicast=yes speed=1Gbit/s
       resources: irq:0 memory:74458000-7445bfff memory:74478000-7447bfff
  *-network:11 DISABLED
       description: Ethernet interface
       product: 82576 Virtual Function
       vendor: Intel Corporation
       physical id: 11.1
       bus info: pci@0000:09:11.1
       logical name: enp9s0f1v4
       version: 01
       serial: 06:98:ba:b6:23:23
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: msix pciexpress bus_master cap_list ethernet physical 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic latency=0 link=no multicast=yes
       resources: irq:0 memory:74498000-7449bfff memory:744b8000-744bbfff
  *-network:12
       description: Ethernet interface
       product: 82576 Virtual Function
       vendor: Intel Corporation
       physical id: 11.2
       bus info: pci@0000:09:11.2
       logical name: enp9s0f0v5
       version: 01
       serial: 02:3d:f6:89:ba:eb
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: msix pciexpress bus_master cap_list ethernet physical 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic duplex=full ip=10.0.0.15 latency=0 link=yes multicast=yes speed=1Gbit/s
       resources: irq:0 memory:7445c000-7445ffff memory:7447c000-7447ffff
  *-network:13 DISABLED
       description: Ethernet interface
       product: 82576 Virtual Function
       vendor: Intel Corporation
       physical id: 11.3
       bus info: pci@0000:09:11.3
       logical name: enp9s0f1v5
       version: 01
       serial: a6:32:58:29:8f:c9
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: msix pciexpress bus_master cap_list ethernet physical 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic latency=0 link=no multicast=yes
       resources: irq:0 memory:7449c000-7449ffff memory:744bc000-744bffff
  *-network:14
       description: Ethernet interface
       product: 82576 Virtual Function
       vendor: Intel Corporation
       physical id: 11.4
       bus info: pci@0000:09:11.4
       logical name: enp9s0f0v6
       version: 01
       serial: 0a:8e:d2:76:85:fc
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: msix pciexpress bus_master cap_list ethernet physical 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic duplex=full ip=10.0.0.16 latency=0 link=yes multicast=yes speed=1Gbit/s
       resources: irq:0 memory:74460000-74463fff memory:74480000-74483fff
  *-network:15 DISABLED
       description: Ethernet interface
       product: 82576 Virtual Function
       vendor: Intel Corporation
       physical id: 11.5
       bus info: pci@0000:09:11.5
       logical name: enp9s0f1v6
       version: 01
       serial: 42:be:a3:6a:7b:ba
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: msix pciexpress bus_master cap_list ethernet physical 1000bt-fd
       configuration: autonegotiation=off broadcast=yes driver=igbvf driverversion=6.2.0-26-generic latency=0 link=no multicast=yes
       resources: irq:0 memory:744a0000-744a3fff memory:744c0000-744c3fff

```
So, similar machines, but one with Intel and the other with RealTek. The RealTek NIC'es download stats is about half that of the Intel NIC.

---

### Post by MAFoElffen on 2023-08-28
TheFu said something that jogged my memory, if he is running that WiFi card: 
```

Realtek RTL8822CE 802.11ac PCIe Wireless Network Adapter

```
Remember I used to be an Onsite HP Warranty Service Tech? This card is used in HP Laptops. There is a compatible direct upgrade from HP for this card to:
```

Intel Wi-Fi 6 AX200 ax 2×2 + Bluetooth 5.0 MU-MIMO M.2 2230 non-vPro   HP part number L35282-005.

```
Though some places say that RealTek WiFi card is rated at 864MBPS, but most of these real-world only benchmark out at 433MBPS.  

The Intel Wi-Fi 6 AX200 tests out at 2.4 Gbps on the 5GHz band, and 574 MB/s on the 2.4 GHz band.

Search for it via the HP part number, you can get brand new from HP for about $75, but under $30 from EBay and Amazon.

---

### Post by #&amp;thj^% on 2023-08-28
> **MAFoElffen said:**
> 
Search for it via the HP part number, you can get brand new from HP for about $75, but under $30 from EBay and Amazon.
+1
But My experience with Amazon is **buyer beware**, just flip for the few extra bucks, and smile with new card.

---

### Post by TheFu on 2023-08-28
Internet speed tests are less about the NIC and more about the internet connection.
I happen to have 2 ISPs right now.
```
$ speedtest-cli 
Retrieving speedtest.net configuration...
Testing from **Comcast Business** (50.73.91.145)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by GSL Networks (Atlanta, GA) [42.47 km]: 20.029 ms
Testing download speed................................................................................
Download: 26.55 Mbit/s
Testing upload speed......................................................................................................
Upload: 6.30 Mbit/s
```

My WAN router will only get about 350Mbps for a single stream, but it can handle 940 Mbps if multiple streams are running. That WAN router is an APU2 running OPNSense with intel i210 NICs for each port. That says more about BSD than it does the hardware, actually.

The speed test for the other connection was over wifi with a tablet.  They only provide image output, not text. [https://librespeed.org/results/?id=1ppapmd](https://librespeed.org/results/?id=1ppapmd)  has the image. Meh. 
```
Download: 347 Mbps
Upload: 254 Mbps

```

Begin rant ... 

Can you guess which one is fibre and which one I'm likely to be using only next week?  Did I mention that it costs 50% less too? That's the difference between business service and what-ever-you-get Residential service.  Price related directly to the need for support, who you speak with and how quickly issues are resolved.  For example, the more expensive ISP with a business account, I get to speak with a real human in about 10 seconds and that person can actually do something.  Further, they will roll at tech within 2 days, worst case.  I've had techs show up the following morning a few times, however.

With the new ISP, I've been trying to get a billing issue resolved for over 3 months. Each time I think it is handled and the person on the other end claims it is, I've been disappointed.  Last week, I had them tell me EXACTLY how much my next bill would be and I paid it.  Today I logged into their billing website, saw the payment and saw a balance of $0.01.  I'm not joking.  Additionally, I still see the billing issue for service I never got due to a door-to-door sales guy not knowing their own products and prices.  I asked for something because I was told it would be $3/month.  They insisted that I speed with someone on the sub-continent (halfway around the world) to get it. That person was not understandable, so I asked for another.  They refused to just let me speak with someone who was working right then.  It isn't like I was asking for some special thing. It is a very common thing in networking that I wanted.  Anyway, the next person had an even thicker accent AND spoke far to fast. I asked him to slow down at least 5 times during 1 call.  I never understood why I needed to be on the call for them to do this task. Made zero sense.   BTW, the first ISP did the same thing and just provided me with the details I needed for my router and it was handled.  Anyway - the new ISP said it would be $30/month, not $3/month so I said to cancel that part of the order.  However, they've been charging me for that addon that I never got all this time.

At this point, I'm inclined to just cancel the new service and come back in 3 months to try again.  It shouldn't be this hard to deal with a US company, even though both of these companies are in the top 10 most hated companies in the country.  I completely understand why now.  My practical side will probably win. I'll probably eat the extra cost just to get the higher throughput. Even then, it is less costly.  This was not any special deal ... well, expect the first 2 months were free and that has been honored.

Plus the old ISP started teasing faster connectivity for the same price a few weeks ago. The new faster throughput is still 200Mbps slower than the fiber connection for the down and 10x slower for the up.

Sorry about that.  Most definitely a 1st world problem.  I can get 10 Gbps service at home, but it is expensive.  The fiber ISP will go to 5 Gbps, symmetric.  No idea what the cost is, but they say my current modem will handle it, so it is just a software/setting change, not hardware.  The power of fiber.

---

### Post by #&amp;thj^% on 2023-08-28
> **TheFu said:**
> 
Can you guess which one is fibre and which one I'm likely to be using only next week?  Did I mention that it costs 50% less too?

Eww eww pick me pick me!:lolflag:
I run a tight ship here:
```
speedtest
Retrieving speedtest.net configuration...
Cannot retrieve speedtest configuration
ERROR: HTTP Error 403: Forbidden

```

---

### Post by kabirgandhiok on 2023-08-29
Doug S, getting an SSD will take time. I'm going to have to stick with what I have. Having said that, an NVMe PCIe stick is something I can arrange soon enough. But we have not really ruled out anything here. Maybe all these slowdowns cease if I just get a swap partition instead of the file. Also, let's say I empty half of my HDD data onto an external disk, that could help?

TheFu, Is the WiFi adapter really the problem here? I mean, my ping and download, upload stats are consistent with what I had asked my ISP to provide, which is 100 mbps Down and Up, I figured that much would be enough for my needs. Would I be better off with a wired connection instead?

```

kabir@kabirsubuntu:~$ speedtest-cli --secure
Retrieving speedtest.net configuration...
Testing from Tata Sky Broadband Private Limited (103.208.70.147)...
Retrieving speedtest.net server list...
Selecting best server based on ping...
Hosted by Ultranet (Noida) [12.36 km]: 11.895 ms
Testing download speed................................................................................
Download: 105.18 Mbit/s
Testing upload speed......................................................................................................
Upload: 110.67 Mbit/s

kabir@kabirsubuntu:~$ sudo lshw -C network
[sudo] password for kabir: 
Sorry, try again.
[sudo] password for kabir: 
  *-network                 
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: eno1
       version: 15
       serial: 6c:02:e0:d1:7a:b6
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=5.15.0-82-generic firmware=rtl8168h-2_0.0.2 02/26/15 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:16 ioport:4000(size=256) memory:52104000-52104fff memory:52100000-52103fff
  *-network
       description: Wireless interface
       product: RTL8822CE 802.11ac PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlo1
       version: 00
       serial: 20:4e:f6:f2:82:15
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtw_8822ce driverversion=5.15.0-82-generic firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes wireless=IEEE 802.11
       resources: irq:148 ioport:3000(size=256) memory:52000000-5200ffff

```

MAFoElffen, 1fallen, and everyone else who have been so helpful and given so many suggestions that it's hard to keep up LOL, I think I should get a swap partition, and check if that helps, so we can rule that out. I mean, maybe I should do that before I consider getting new hardware.

---

### Post by TheFu on 2023-08-29
> **TheFu said:**
> Internet speed tests are less about the NIC and more about the internet connection.


as i wrote.

---

### Post by TheFu on 2023-08-29
> **TheFu said:**
> as i wrote.

Higher throughput only matters for LAN-to-LAN transfers. In a house with 1 device, only matching the internet limits matters because you'll never experience anything faster.

---

