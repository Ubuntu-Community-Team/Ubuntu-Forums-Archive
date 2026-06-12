---
title: "Why when I run firefox browser it takes a lot of memory?"
date: 2024-08-18
forum: General Help
---

### Post by nilovsergey on 2024-08-18
On Kubuntu 22.04 sometimes when I run the Firefox browser I see it takes a lot of memory and my OS becomes very slow. 
Sometimes it hangs up the system. I check with the top command  and see this. :


          ```
63 root      20   0       0      0      0 R  73,9   0,0   0:26.99 kswapd0                                                                                                                                                                                                
      19765 master    20   0   11,6g 237964   8744 R  52,2   3,0   0:15.20 firefox                                                                                                                                                                                                
      18164 master    20   0   32,5g  30468   7700 R  47,8   0,4   0:09.27 skypeforlinux                                                                                                                                                                                          
      18978 root      20   0       0      0      0 D  21,7   0,0   0:01.14 kworker/u8:4+loop20                                                                                                                                                                                    
        752 root      20   0  106284  94860    640 S  13,0   1,2   4:58.19 mount.ntfs-3g                                                                                                                                                                                          
       8163 master    20   0   21,3g 173424   3840 R  13,0   2,2   3:40.09 node          

```

   
I searched and found some proposals to explain/solve this problem. 
like   
[https://community.toradex.com/t/kswapd0-hogging-cpu-freezing-device/20467](https://community.toradex.com/t/kswapd0-hogging-cpu-freezing-device/20467)   


Which settings can I try to use to solve the issue? Why so much memory is used by Firefox and kswapd0 services ?

```

    uname -a
    Linux master-at-home 6.5.0-35-generic #35~22.04.1-Ubuntu SMP PREEMPT_DYNAMIC Tue May  7 09:00:52 UTC 2 x86_64 x86_64 x86_64 GNU/Linux
    
    free
                   total        used        free      shared  buff/cache   available
    Mem:         8040236     5871204      577576      582876     1591456     1295780
    Swap:        2104476     2101828        2648
```

---

### Post by TheFu on 2024-08-18
You are misinterpreting what **top** is saying.  In the **top** manpage, it will layout what those columns mean.  Read the section on _Linux Memory Types_.

After all, how can a system with 10G of combined real and virtual memory allow any process to grab more than 11G?  It isn't possible.
BTW, if you have an iGPU, that RAM would be removed from the totals shown above.

Of course, Firefox is a hog.  It allocates RAM then doesn't actually use it.  

Linux memory management has made some choices over the last few decades.  One of those choices is not to actually verify that RAM allocated is available. The malloc() call always returns 0 (all is fine), even when RAM is theoretically gone.  Plus, by default, firefox runs inside a snap container, so there is that overhead.  

With other containers, we can limit the amount of RAM any process actually sees.  I use firejail and limit FF to seeing about 10G (1/3rd of the RAM in the system).  I started with a 4GB limit, but FF kept crashing after a few days.  I increased it to 6G - it lasted a few more days.  8G - it lasted almost a week.  Finally, I set it to 10G and FF hasn't crashed for out of RAM situations in a few years, since I decided FF was a RAM hog for no reason.

I'm using FF-ESR, not the default installed by snaps. This is mainly to avoid the snap package and have FF managed by the Mozilla Team's PPA.  I avoid snap packaged software since it interferes with my ability to control things, though I do use snaps for a few special things because the snap package actually makes my life easier.  Of 20 things on a system that Canonical wants installed as a snap, I want zero.  Across my 10 systems, 1 - - just 1 - has a snap package that actually makes my life better.

---

### Post by dragonfly41 on 2024-08-18
Understand that each tab that you have open consume RAM. I see many users (including myself) having multiple tabs open. To see the consumption per tab use the Linux monitoring tool Stacer (fifth button down in docking bar > Processes > search firefox).  View Processes and memory consumption. Another test is to use ProfileManager feature in Firefox (firefox --help) to try a slimmed down profile. Some extensions such as OneTab allow you to dump tabs. I would create a number of profiles (each with few tabs) and switch profiles.

---

### Post by currentshaft on 2024-08-18
we

---

### Post by TheFu on 2024-08-18
> **currentshaft said:**
> You need more than 8 gigabytes of RAM to use a modern OS and the Internet efficiently in 2024.

Perhaps.  Perhaps not.  Here's my main desktop system:
```
$ inxi -bz
System:
  Kernel: 5.15.0-118-generic x86_64 bits: 64 Desktop: N/A
    Distro: Linux Mint 21.3 Virginia
Machine:
  Type: Kvm System: QEMU product: Standard PC (i440FX + PIIX, 1996)
    v: pc-i440fx-focal serial: <superuser required>
  Mobo: N/A model: N/A serial: N/A BIOS: SeaBIOS v: 1.13.0-1ubuntu1.1
    date: 04/01/2014
CPU:
  Info: 2x 1-core AMD EPYC-Rome [SMP] speed (MHz): avg: 4200
Graphics:
  Device-1: Red Hat QXL paravirtual graphic card driver: qxl v: kernel
  Display: server: X.Org v: 1.20.13 driver: X: loaded: N/A
    unloaded: fbdev,modesetting,vesa gpu: qxl note:  X driver n/a
    resolution: 1920x1200~60Hz
  OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits)
    v: 4.5 Mesa 23.2.1-1ubuntu3.1~22.04.2
Network:
  Device-1: Intel 82371AB/EB/MB PIIX4 ACPI type: network bridge
    driver: piix4_smbus
  Device-2: Red Hat Virtio network driver: virtio-pci
Drives:
  Local Storage: total: raw: 40 GiB usable: 76.16 GiB used: 22.4 GiB (29.4%)
Info:
  Processes: 264 Uptime: 7d 23h 39m Memory: 5.74 GiB used: 5.26 GiB (91.6%)
  Shell: Bash inxi: 3.3.13

```
It is stable. Up for the last nearly 8 days.  While 4GB is very tight for most users.  8GB is not for everyone.  8 is the the minimum that I'd buy a seldom-used laptop containing, but I've had laptops with 2G, 4G, 6G and 8G.  8G was quite comfortable for my needs - which was browsing, fat email, and 1 or 2 VMs. 
Top output on that system:
```
top - 10:45:56 up 7 days, 23:37,  1 user,  load average: 0.17, 0.14, 0.09
Tasks: 260 total,   1 running, 259 sleeping,   0 stopped,   0 zombie
%Cpu(s):  3.8 us,  1.0 sy,  0.0 ni, 95.0 id,  0.2 wa,  0.0 hi,  0.0 si,  0.0 st
MiB Mem :   5873.9 total,    175.9 free,   5084.0 used,    614.0 buff/cache
MiB Swap:   1873.0 total,   1872.2 free,      0.8 used.    420.9 avail Mem

    PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND
 814003 tf        20   0 3373688 577076  96208 S   0.7   9.6  75:37.85 **thunderbird**
2896784 tf        20   0 2875376 285176 105044 S   0.7   4.7   0:04.30 **firefox-bin**
2896921 tf        20   0 2454088  99888  64028 S   0.7   1.7   0:00.47 Privileged Cont
   1448 tf        20   0   17476   8288   6224 S   0.0   0.1   0:44.69 systemd
   1468 tf        20   0  106060   4204      0 S   0.0   0.1   0:00.00 (sd-pam)
   1718 tf        20   0   39288   4112   3136 S   0.0   0.1   0:03.50 pipewire
   1750 tf        20   0    8436   2648   2272 S   0.0   0.0   0:14.96 dbus-daemon
   3482 tf        20   0   83988   1784   1480 S   0.0   0.0   0:00.00 gpg-agent
  61057 tf        20   0  536908   5164   4404 S   0.0   0.1   0:16.88 xdg-document-po
  61060 tf        20   0  236156   3684   3288 S   0.0   0.1   0:00.00 xdg-permission-
  61188 tf        20   0  309776   5100   4516 S   0.0   0.1   0:00.00 at-spi-bus-laun
 813103 tf        20   0   19512   6872   3932 S   0.0   0.1   0:00.81 sshd   
 813104 tf        20   0   13120   4680   2500 S   0.0   0.1   0:00.22 bash   
 813990 tf        20   0   23200  10512   3760 S   0.0   0.2   1:23.56 sshd   
 813991 tf        20   0    5388   2032   1608 S   0.0   0.0   0:00.00 firejail
 813994 tf        20   0    5400   1680   1192 S   0.0   0.0   0:00.10 firejail
 814175 tf        20   0 2429644  78592  50760 S   0.0   1.3   0:01.77 WebExtensions
 814242 tf        20   0 2410580  60416  47092 S   0.0   1.0   0:00.77 Web Content
2896762 tf        20   0   23020  11020   4444 S   0.0   0.2   0:01.59 sshd   
2896763 tf        20   0    9972   2608   2352 S   0.0   0.0   0:00.00 firefox.sh

```

Of course, some people can't seem to run their applications with 128GB of RAM either.  Just depends.  If you do LLM work, more RAM is needed.  OTOH, chromebooks were fast and capable with 4GB for the last 10 yrs.  Just depends on what you need.

YMMV.

---

### Post by kinddolphin8827 on 2024-08-18
I've got 16gb physical ram (15GB  usable) on the HP Z420 workstation that I'm writing this response on as we speak .


```

free -h
               total        used        free      shared  buff/cache   available
Mem:            15Gi       2.7Gi        11Gi       111Mi       2.0Gi        12Gi
Swap:          976Mi          0B       976Mi



```

---

