---
title: "ubuntu freezes and the most stable/freeze-proof graphics driver"
date: 2020-06-21
forum: General Help
---

### Post by Ranbunta_Bantubunt on 2020-06-21
To all,

I was delighted recently to switch to linux on a razer blade pro 17" early 2019. It's great, love everything about it and love the community as well. 

Having a minor issue, twice so far it has frozen up on me unexpectedly and I had to force-power off and reboot. The first time it happened I ignored it, second time I thought I should troubleshoot.

Ok, so I looked in syslog and to make a long story short, it appears to me that the failure is related to the nvidia graphics driver. As to why I think so, this is what happens right before it freezes up:

```

[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:15 computer openrazer-daemon[51818]: 2020-06-21 06:16:15 | razer.device0                  | INFO     | Suspending RazerBladePro2019[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489146] Xorg: page allocation failure: order:4, mode:0x40cc0(GFP_KERNEL|__GFP_COMP), nodemask=(null),cpuset=/,mems_allowed=0[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489153] CPU: 5 PID: 51339 Comm: Xorg Tainted: P           OE     5.4.0-37-generic #41-Ubuntu[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489154] Hardware name: Razer Blade Pro 17 (2019)/DA720, BIOS 1.04 06/19/2019[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489155] Call Trace:[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489162]  dump_stack+0x6d/0x9a[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489165]  warn_alloc.cold+0x7b/0xdf[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489168]  __alloc_pages_slowpath+0xe07/0xe50[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489172]  ? wakeup_kswapd+0xa1/0x1b0[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489174]  ? rmqueue+0x1d6/0xf00[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489176]  ? get_page_from_freelist+0x6b/0x390[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489178]  __alloc_pages_nodemask+0x2d0/0x320[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489180]  alloc_pages_current+0x87/0xe0[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489182]  kmalloc_order+0x1f/0x80[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489184]  kmalloc_order_trace+0x24/0xa0[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489205]  ? _nv000491kms+0x50/0x50 [nvidia_modeset][/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489207]  __kmalloc+0x220/0x280[/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489218]  ? _nv000491kms+0x50/0x50 [nvidia_modeset][/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489227]  nvkms_alloc+0x24/0x60 [nvidia_modeset][/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489241]  _nv002521kms+0x16/0x30 [nvidia_modeset][/SIZE][/FONT][/COLOR]
[COLOR=#2e3436][FONT=monospace][SIZE=2]Jun 21 06:16:24 computer kernel: [78872.489244] WARNING: kernel stack frame pointer at 0000000057e04370 in Xorg:51339 has bad value 00000000cfa7edf2[/SIZE][/FONT][/COLOR]

  
```

The log claims that it was suspending, but actually it just froze and was entirely unresponsive, requiring a reboot.

Also this:

```

~$ lspci -vnn | grep -i VGA -A 12
00:02.0 VGA compatible controller [0300]: Intel Corporation UHD Graphics 630 (Mobile) [8086:3e9b] (prog-if 00 [VGA controller])
    DeviceName: Onboard - Video
    Subsystem: Razer USA Ltd. UHD Graphics 630 (Mobile) [1a58:3000]
    Flags: bus master, fast devsel, latency 0, IRQ 157
    Memory at 6043000000 (64-bit, non-prefetchable) [size=16M]
    Memory at 4000000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 5000 [size=64]
    Expansion ROM at 000c0000 [virtual] [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:04.0 Signal processing controller [1180]: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem [8086:1903] (rev 07)
--
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation TU104M [GeForce RTX 2080 Mobile] [10de:1e90] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Razer USA Ltd. TU104M [GeForce RTX 2080 Mobile] [1a58:3000]
    Flags: bus master, fast devsel, latency 0, IRQ 194
    Memory at 57000000 (32-bit, non-prefetchable) [size=16M]
    Memory at 6030000000 (64-bit, prefetchable) [size=256M]
    Memory at 6040000000 (64-bit, prefetchable) [size=32M]
    I/O ports at 4000 [size=128]
    Expansion ROM at 58000000 [virtual] [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia

01:00.1 Audio device [0403]: NVIDIA Corporation TU104 HD Audio Controller [10de:10f8] (rev a1)


~$ nvidia-settings --version

nvidia-settings:  version 440.64


``` 

So google tells me that graphics card-related freezes are unfortunately a thing for ubuntu, so I'm wondering what the best driver would be if stability is my #1 concern.

I see three choices offered to me in "Additional drivers":
1) Nvidia driver metapackage from nvidia-driver-400 (proprietary, tested)  <<<== this is active
2) Nvidia driver metapackage from nvidia-driver-435 (proprietary)
3) Using X.Org X sever -- Nouveau display driver from xserver-xorg-video-nouveau (open source)

I dont have a need for heavy duty GPU acceleration, I mean, of course I would like as much as possible as long as it doesnt bring on instability, but I'm really not a gamer.

So at any rate, any advice on which driver I should choose - one of these three options, or maybe something else entirely? Maybe some old driver that is rock stable but doesnt have as much whizbangs and speed as the current driver?

Thanks!

Ran

---

### Post by CelticWarrior on 2020-06-21
Are you sure it's 400 and not 440? The latter is the recommended driver.

---

### Post by Ranbunta_Bantubunt on 2020-06-21
> **CelticWarrior said:**
> Are you sure it's 400 and not 440? The latter is the recommended driver.

The command $nvidia-settings yields 
version 440.64

However the "additional drivers" tab in software reports it as 400. 

Im assuming it really is 440.64 and just registers as 400 for some reason in that tab.

Now vis a vis "the recommended driver", does this mean, for one who wishes to maximize stability over other considerations, it would be the recommended driver?
I assume there are some upsides and downsides to each of the provided choices, or is the open source driver offered just out of principle and without benefits compared to Nvidia's besides not being proprietary?

---

### Post by CelticWarrior on 2020-06-21
I mean the recommended driver by Nvidia: [https://www.nvidia.co.uk/Download/driverResults.aspx/159370/en-uk](https://www.nvidia.co.uk/Download/driverResults.aspx/159370/en-uk)

---

### Post by Ranbunta_Bantubunt on 2020-06-21
yes, thank you. 

im just wondering which driver would be the most stable/least likely to crash. nvidia puts out new versions for various reasons, compatibility with new games, new features, etc. may not be the most stable/reliable.

but i appreciate the link. 

in particular i am curious as to whether it is felt that the open-source driver may be more stable. a google search was unclear, some people suggested it may be more stable, but also some people like google chrome engineers say it is less stable:

[https://www.phoronix.com/scan.php?page=news_item&px=Chrome-Blacklisting-Nouveau](https://www.phoronix.com/scan.php?page=news_item&px=Chrome-Blacklisting-Nouveau)

overall i'd prefer theoretically speaking, to use open-source drivers, but i'm not a purist, i just want my computer to not freeze :)

---

### Post by CelticWarrior on 2020-06-21
Any high-end and current Nvidia chipset works better with newer driver version. Your reasoning in favor of older versions is therefore debunked by reality.

---

### Post by Ranbunta_Bantubunt on 2020-06-22
> **CelticWarrior said:**
> Any high-end and current Nvidia chipset works better with newer driver version. Your reasoning in favor of older versions is therefore debunked by reality.

Actually I didn't offer any reasoning in favor of anything, I am asking a question. Thank you for providing this wisdom regarding reality. I shall proceed accordingly guided by your kind debunking.

---

### Post by lvm on 2020-06-22
> **Ranbunta_Bantubunt said:**
> ```
Jun 21 06:16:15 computer openrazer-daemon[51818]: 2020-06-21 06:16:15 | razer.device0                  | INFO     | Suspending RazerBladePro2019
Jun 21 06:16:24 computer kernel: [78872.489146] Xorg: page allocation failure: order:4, mode:0x40cc0(GFP_KERNEL|__GFP_COMP), nodemask=(null),cpuset=/,mems_allowed=0
```

The log claims that it was suspending, but actually it just froze and was entirely unresponsive, requiring a reboot.

Yes, logs you posted plainly state that it *was* suspending and then something went wrong. I don't see how you reached the conclusion that video drivers are to blame, for me this openrazer-daemon would be the first and obvious suspect - try removing or configuring it.

---

### Post by Ranbunta_Bantubunt on 2020-06-22
I may have been jumping to conclusions that it was the video driver that was at fault... it's just that I see an error related to the video drivers at basically the same time the system froze and there seem to have been issues with nvidia video drivers and ubuntu. 

I think you may be right that it is related to the system suspending... this has happened to me 4 times now, and each time, it is at the "lock" screen that it happened, eg., when the system thought I was idle.

I disabled "suspend when idle for..." thinking that may help, but it occurred again.

I could uninstall openrazer... I installed it for the nifty keyboard RGB effects, which I can live without since I am usually in clamshell mode anyway. I'm actually unsure why openrazer was involved in suspension anyway. As far as I can tell it's intended just for driving razer peripherals and not managing anything like power state. I will go ahead and uninstall that and see what happens.

Thanks for the suggestion, really appreciate it!

I really love this setup, I should have switched to linux a decade ago.

---

### Post by Ranbunta_Bantubunt on 2020-06-22
openrazer is gone! hopefully the problem not to recur again!

---

### Post by Ranbunta_Bantubunt on 2020-06-23
> **lvm said:**
> Yes, logs you posted plainly state that it *was* suspending and then something went wrong. I don't see how you reached the conclusion that video drivers are to blame, for me this openrazer-daemon would be the first and obvious suspect - try removing or configuring it.

Well, I believe you have diagnosed the problem correctly. I removed openrazer and it's been 2 days, problem has not recurred. Thank you!

---

### Post by Ranbunta_Bantubunt on 2020-06-28
just a follow-up for posterity, and to help anyone searching on this topic in the future. it's been 5 days now and this particular issue has not recurred. so it does appear to have been related to the openrazer drivers. again im not clear on why they would be involved in suspending or cause a failed suspension, as AFAICT openrazer provides just RGB razer device support, but after uninstalling openrazer I haven't had any further issues. thanks again to all for your help

---

