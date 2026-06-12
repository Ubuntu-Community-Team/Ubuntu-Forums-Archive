---
title: "Linux Ubuntu 19.4 Not Showing All RAM"
date: 2019-10-01
forum: General Help
---

### Post by venomx2 on 2019-10-01
Got a new PC which has 2 x 4GB of Fury Hyper X DDR4 ram  - so 8GB in total
In the details section of Linux it's saying I have 5.8GB of ram,

Fury only make 4Gb/8GB/16GB ram - so it's impossible to make 6GB



Is this normal I heard it's something to do with a "swap file " ? Thanks

---

### Post by venomx2 on 2019-10-01
When I run "free -m" in terminal it says...
Mem : 5968
Swap : 2047

When I run sudo lshw | grep -m 1 -A 25 "*-memory"

It says Size 8GiB

---

### Post by The Cog on 2019-10-01
It is my understanding that free does not show the memory that the OS itself is using - only what remains after loading the base OS.

---

### Post by TheFu on 2019-10-01
/proc/meminfo has what the OS sees.  
It is common for 512MB - 2G of RAM to be taken for the onboard GPU.  If you don't have 100% separate GPU in the system, look there.
```

$ inxi -Iz
Info:      Processes: 328 Uptime: 1 day Memory: 3227.8/7859.6MB
```

Shows what my Core i5 laptop sees as RAM.
```
$ glxinfo -B|grep -i memory
    Video memory: 3072MB
    Unified memory: yes

```
So this claims that 7859.6MB is RAM and 3GB is used by the onboard GPU. I think the 3G is the maximum the GPU might use. It is dynamic.
 
```
 $ lspci -vk |egrep --after-context=10 VGA
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 1d30
        Flags: bus master, fast devsel, latency 0, IRQ 126
        Memory at ee000000 (64-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=**256M**]
        I/O ports at f000 [size=64]
        [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

```
Appears the most correct. 256M makes the most sense. Another command, where we don't have to count lines to guess how many are needed:
```
$ lspci -vk |perl -lne 'print if /VGA/ .. /^[\w]*$/'
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 620 (rev 07) (prog-if 00 [VGA controller])
        Subsystem: ASUSTeK Computer Inc. Device 1d30
        Flags: bus master, fast devsel, latency 0, IRQ 126
        Memory at ee000000 (64-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (64-bit, prefetchable) [size=**256M**]
        I/O ports at f000 [size=64]
        [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915
```
Perl is a little more flexible ... it looks to "VGA" and shows all the lines until there's an empty line.

---

### Post by TheFu on 2019-10-01
A little math ...
8 x 1024 = 8192MB
8192 - 256 = 7936MB
There are always slight differences for other overhead items.

---

### Post by venomx2 on 2019-10-02
Thanks guys. After some reading a searching It is infact the integrated GPU which is taking up some RAM

---

