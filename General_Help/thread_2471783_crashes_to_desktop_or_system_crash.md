---
title: "crashes to desktop or system crash"
date: 2022-02-09
forum: General Help
---

### Post by mastablasta on 2022-02-09
My kids PC started acting up. And i am not sure what is wrong. We have two things which i think might be separated or could also be connected -> occasional slow wi-fi speed on steam and crashes and freezes in certaing ames. 

First one is that Steam files transfer can be unreasonably slow. he is connected via wi-fi. changing regions does not have any effect. Youtube and Speedtest work fine and speeds are 25 Mbps+ over there. but on Steam he would get 70 kbps -150 kbps. and then it would jump up to 40 Mbps and then back down to 0,6 Mbps and then up again to about 30 Mbps or 40 Mps. really depends, sometimes it just stays low. i realise wi-fi is not as reliable as wire but he should be getting 15-20 Mbps relatively easily. he has 20.04 installed with original kernel. at the time i had to patch it with DKMS for realtek driver.   

then i noticed this line in DMESG:
```

WARNING: CPU: 0 PID: 816 at /var/lib/dkms/rtl8821ce/v5.5.2_34066.20200325/build/hal/hal_com.c:11447 rtw_lps_state_chk+0x39/0x41 [8821ce]


```

does this mean something is wrong with driver? should i do a kernel update to HWE and get fresh drivers in? i read that these can now be installed using additional drivers.

Next thing i had to do at the time is to add boot parameter iommu=soft, otherwise the RAM was not utilised properly resulting in PC being unable to boot. 

with that in mind i am now getting a crash to desktop or sometimes complete system freeze. i though it was caused by overheating. so a bit of cleaning and checking the temp by hand showed that the laptop is  not hot at all. fans did their job well it seems. i cought the last few crashes and Dmesg showed this and similar messages when crashes occured:

```
[30930.543581] oom-kill:constraint=CONSTRAINT_NONE,nodemask=(null),cpuset=/,mems_allowed=0,global_oom,task_memcg=/user.slice/user-1000.slice/session-1.scope,task=CrBrowserMain,pid=39611,uid=1000[30930.543901] Out of memory: Killed process 39611 (CrBrowserMain) total-vm:47513932kB, anon-rss:2374940kB, file-rss:0kB, shmem-rss:22444kB, UID:1000 pgtables:9540kB oom_score_adj:0
[30930.732985] oom_reaper: reaped process 39611 (CrBrowserMain), now anon-rss:0kB, file-rss:0kB, shmem-rss:22388kB
```

it looks like steam browser (steam overlay?) causes the crash, but it is hard to know if this is really the cause. the reaosn i've added the wi-fi here is because locally played games (native or run with proton) usually do not cause a crash. For example Subnautica, CS:GO, Team Fortress 2, Left 4 Dead 2, The Sims 4 , The Forest, Raft (kind of slow working after latest update, but it does work and does not crash)... all work fine. Sometimes subnautica could crash but this is rare. Most crashes he got in Garry's mod where they were very likely caused by adding too many entities and using various plugins. so it would really run out of ram. i have seen him do it on my ne wPC which has 32 GB RAM.  Deep Rock Galactic causes these crashes and sometimes he could not reconnect. he would get a notification that updates are available (shader precaching mostly) and then it would download large updates at this super slow speed (mentioned at the top). then again other days he can play for 4 hours and there is not a single crash.

here is the full dmesg: [https://pastebin.ubuntu.com/p/c9dr8XCSGf/](https://pastebin.ubuntu.com/p/c9dr8XCSGf/)

at the time when i installed the system the CPU was still relatively new as was the realtek chip.

his "gaming PC" is :
HP 255 G7 Notebook PC/85EA
8 GB RAM
Ryzen 5 3500U with Radeon Vega 8 graphics chip in it (using default AMDGPU driver)
nvme 256 GB disk + we added USB 3.0 connected external SATA SSD drive (it's inside an enclosure).


I guess what i need to know is this could just be some drivers issues and that it is worth to do a RAM & nvme disk upgrade when he saves up in 2 months or so.

i also probably need to make a hole to his room and get some network wiring in place.

---

### Post by Autodave on 2022-02-09
Don't know if this helps or not, but I have a laptop that worked fine.  Then, the wifi signal strength started being weak. ( the laptop is literally 5 feet away from the router.  Not a big deal at that moment.  But a few days later, laptop started running very slow for anything requiring internet access.  The laptop doesn't have an internet port, so I went to Amazon and bought a cheapie wifi USB stick.  I disabled the builtin wifi after downloading the driver I needed for the new Edimax adapter.  Installed the driver and all has been good since then.

My point is that even though I had a good enough wifi connection being only 5 feet away from the router, something else was slowing the system to a crawl when using wifi.  The new adapter fixed that.

---

### Post by mastablasta on 2022-02-16
bump.

also, no more free USB ports. all 3 are occupied (mouse, keyboard, external SSD drive).

---

