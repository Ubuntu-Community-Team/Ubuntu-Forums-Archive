---
title: "System unresponsive hours after reboot, Upgrade to 19.04"
date: 2019-05-24
forum: General Help
---

### Post by crono1412 on 2019-05-24
Hey all.  I'm having a huge problem with my home Ubuntu server after upgrading to 19.04.  There are a lot of things this server is doing, and a couple of things that are going wrong from a hardware side, so I can't say for sure that its because of the upgrade, but things didn't grind to a near halt until after the upgrade.

I am running a media server with Emby, mythtv, and an 8tb raidz1 file server.  Everything was working fine, though I began to have concerns that one of the drives in the zpool was failing before the issue presented itself.  We would stream movies from emby through the internet to my in-laws when we were over there, and use the file server to store all the movies and important documents.  I also run a few game servers on this for my local friends, such as starbound, Trinity, and Ark.

Hardware is kinda old but has served me well enough.  Its a 6 core AMD FX-6300 with 8gb of ram.  I have a cheap Geforce 710 PCI card for the rare times I need to connect a monitor.  There is a Happauge TV capture card also.

This is a headless server, so all work I do on it is either through ssh or chrome remote desktop.  All services connect via gigabit ethernet.  And as I said initially, things were working relatively smoothly until just after the upgrade to 19.04.

After the upgrade, the server would run fine for probably an hour or 2 after a reboot, and then suddenly become almost unresponsive.  I say almost, because I can still ssh into it, but it takes 5 to 10 minutes to get from login to terminal.  A reboot clears the issue (though I actually have to physically hit the reset button, since I'm not able to issue the reboot command successfully), until it suddenly, for no clear reason, grinds to a halt a few hours later.

I've tried hooking up a monitor to the machine while it is in this state, but it never displays anything.  I saw the HDD light on solid for a good day or so straight, so I thought there must be some disk activity that is causing things to slow down.  I checked the health of my zpool and found that it was resilvering a disk at a very very slow speed (max 250k/s).  This lead me to check the smart status of the drives, and at least one was in pre-failure.  After a few more reboots the whole pool ceased to be present without manually doing an import.  So I thought I had found the source of the problem.  I left the pool in a disconnected state and ran off a backup for today, and that seemed to fix things...

Except it didn't.  A few hours later we are back at the nearly unresponsive state.  The drives are still physically attached to the system, but the OS shouldn't be studying about them because they aren't mounted.  I guess I can unplug the drives to see if this helps, as I haven't done that yet, but I figured if the problem was a bad drive that detaching the zpool would work around that problem.

Anyway, I'm at a loss as to how to proceed with troubleshooting.  I've been running this server for years, but in a more set it and forget it sort of way.  I've never had major problems that required me to dive into syslogs or anything, so I'm not sure what information I need to look for to help me figure out what is happening.  I would appreciate any help or direction that the community can provide.

Thanks in advance.

---

### Post by DuckHook on 2019-05-24
In these sorts of scenarios, your logs are your best friends You *must* go through *syslog*. Also look at *dmesg*, although this one is only for current session. Chances are, *syslog* will show you the problem right there.

You mentioned one drive is pre-failure. That may be your problem right there. HDDs are referenced by your CPU if connected, even if they are not actively used. I had a pre-failure drive that would spam the CPU with iowait states despite having all symlinks deleted.

Also, don't run servers on standard releases. Use only LTS, the latest of which was Bionic (18.04). Once they are past their first point release, they are far more stable than standard releases. My hard rule with servers is: don't fix what ain't broken.

I haven't run raid for years so my help is of little value on the technical front. There are server gurus who frequent these forums who might be able to help you with raid. My only observation with RAID is that, in general, it is far too troublesome for home use. If you must amalgamate HDDs try LVM which is simpler and easier to troubleshoot.

If you like, post your *syslog*, *dmesg* and *smartctl* results to this thread. Please be sure to post your output between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by crono1412 on 2019-05-25
Hey, thanks for the quick response.

I went ahead and replaced the disk which I thought was faulty, and my zfs pool is currently resilvering at a pretty rapid pace.  I have the feeling that this was the culprit.

You mentioned using LVM to combine storage.  I'm pretty happy with my zfs pool for data storage and redundancy, but I was curious about how to use LVM as part of a backup solution.  I have a separate device (raspberry pi) with an 8T external usb drive connected for use as backup for the data server.  I'm going to expand my server up to 16TB in the near future, but obviously need more storage for data backup.  Can LVM striped volumes be relocated to other devices without losing the logical volume information?  Would a backup LVM consisting of 2 external USB disks be portable?

---

### Post by DuckHook on 2019-05-25
Glad to hear confirmation that the culprit was the failing HDD and that you have solved it.

As per previous post, don't fix what ain't broken. Now that you've got your ZFS pool running nicely again, it is best to keep dancing with the one who brought you (I really have to do something about my penchant for clichés today).

Also as mentioned, I'm not remotely well versed with RAID and only slightly more so with LVM. While I do use both ZFS and LVM, it is only in a very perfunctory fashion. I have successfully ported whole LVM logical volumes to replacement disks (that's how I painlessly salvaged a whole set of OS partitions from that pre-fail HDD mentioned above), but it was an internal SSD. I don't see why it wouldn't work with external USB disks, but I haven't tried. However, if you are versed in using ZFS over LVM and they duplicate each others' features, why add complexity? Stick with ZFS. Backups should be done using simplest tools possible—it would be unwise to complicate it with ZFS, LVMs or anything else.

Please mark thread "solved" if you consider problem solved.

Good Luck and Happy Ubuntu-ing!

---

### Post by crono1412 on 2019-05-26
Well, it sounds like things aren't as fixed as I would like.  I left an ssh session running and the computer entered into its problem state.  Because I wasn't trying to connect from scratch I was able to run some commands.  It looks like I'm running out of RAM, but not sure how or why.

Here's the dmesg tail.
```
[30104.280046] oom-kill:constraint=CONSTRAINT_NONE,nodemask=(null),cpuset=/,mems_allowed=0,global_oom,task_memcg=/system.slice/cron.service,task=node,pid=4294,uid=1001[30104.280053] Out of memory: Kill process 4294 (node) score 4 or sacrifice child
[30104.336047] Killed process 4294 (node) total-vm:937620kB, anon-rss:72856kB, file-rss:16kB, shmem-rss:0kB
[30104.405135] oom_reaper: reaped process 4294 (node), now anon-rss:0kB, file-rss:0kB, shmem-rss:0kB
[30122.879249] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
[30122.879707] caller os_map_kernel_space.part.10+0x84/0x90 [nvidia] mapping multiple BARs
[30124.329931] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
[30124.330247] caller os_map_kernel_space.part.10+0x84/0x90 [nvidia] mapping multiple BARs
[30126.247030] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
[30126.247482] caller os_map_kernel_space.part.10+0x84/0x90 [nvidia] mapping multiple BARs
[30127.261023] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
[30127.261498] caller os_map_kernel_space.part.10+0x84/0x90 [nvidia] mapping multiple BARs
[30128.658764] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
[30128.659144] caller os_map_kernel_space.part.10+0x84/0x90 [nvidia] mapping multiple BARs
[30130.046583] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
[30130.047474] caller os_map_kernel_space.part.10+0x84/0x90 [nvidia] mapping multiple BARs
[30131.750096] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
[30131.750481] caller os_map_kernel_space.part.10+0x84/0x90 [nvidia] mapping multiple BARs
[30133.521466] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
[30133.522478] caller os_map_kernel_space.part.10+0x84/0x90 [nvidia] mapping multiple BARs
[30134.736485] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
[30134.736832] caller os_map_kernel_space.part.10+0x84/0x90 [nvidia] mapping multiple BARs
[30136.025006] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
[30136.025460] caller os_map_kernel_space.part.10+0x84/0x90 [nvidia] mapping multiple BARs
[30137.311642] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
[30137.312031] caller os_map_kernel_space.part.10+0x84/0x90 [nvidia] mapping multiple BARs
[30138.549818] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
[30138.550661] caller os_map_kernel_space.part.10+0x84/0x90 [nvidia] mapping multiple BARs
[30140.230925] resource sanity check: requesting [mem 0x000c0000-0x000fffff], which spans more than PCI Bus 0000:00 [mem 0x000c0000-0x000dffff window]
[30140.231732] caller os_map_kernel_space.part.10+0x84/0x90 [nvidia] mapping multiple BARs
```

Farther up the trail I noticed "hugepages" was called out.  I installed this recently as I was trying to proof of concept set up GPU passthrough to VM in order to run a headless game server.  This machine doesn't have the hardware to do it, but it was a proof of concept.  I never removed the hugepages software, so its possible its eating all my ram for breakfast.

```
[30088.311236] Out of memory: Kill process 14126 (Xvfb) score 5 or sacrifice child
[30088.340087] Killed process 14126 (Xvfb) total-vm:737772kB, anon-rss:57264kB, file-rss:0kB, shmem-rss:23032kB
[30088.373034] oom_reaper: reaped process 14126 (Xvfb), now anon-rss:0kB, file-rss:0kB, shmem-rss:23032kB
[30104.278868] systemd invoked oom-killer: gfp_mask=0x6200ca(GFP_HIGHUSER_MOVABLE), order=0, oom_score_adj=0
[30104.278871] CPU: 1 PID: 1 Comm: systemd Tainted: P           OE     5.0.0-15-generic #16-Ubuntu
[30104.278872] Hardware name: To Be Filled By O.E.M. To Be Filled By O.E.M./970 Extreme4, BIOS P2.80 08/05/2015
[30104.278873] Call Trace:
[30104.278880]  dump_stack+0x63/0x8a
[30104.278882]  dump_header+0x54/0x308
[30104.278884]  oom_kill_process.cold.29+0xb/0x1d6
[30104.278886]  out_of_memory+0x1bc/0x480
[30104.278888]  __alloc_pages_slowpath+0xb68/0xea0
[30104.278891]  __alloc_pages_nodemask+0x2c4/0x2e0
[30104.278894]  alloc_pages_current+0x81/0xe0
[30104.278896]  __page_cache_alloc+0x6a/0xa0
[30104.278897]  filemap_fault+0x403/0x8a0
[30104.278900]  ? xas_load+0xc/0x80
[30104.278901]  ? xas_find+0x157/0x190
[30104.278903]  ? filemap_map_pages+0x84/0x380
[30104.278905]  ext4_filemap_fault+0x31/0x44
[30104.278907]  __do_fault+0x3c/0x130
[30104.278909]  __handle_mm_fault+0xe49/0x1280
[30104.278911]  handle_mm_fault+0xe1/0x210
[30104.278913]  __do_page_fault+0x23a/0x4c0
[30104.278915]  do_page_fault+0x2e/0xe0
[30104.278916]  ? page_fault+0x8/0x30
[30104.278918]  page_fault+0x1e/0x30
[30104.278920] RIP: 0033:0x7f73a9dfc714
[30104.278922] Code: 00 00 00 00 66 90 48 85 ff 0f 84 b7 00 00 00 41 54 b9 09 00 00 00 b8 01 00 00 00 55 48 89 fd 48 8d 3d 26 4b 07 00 53 48 89 ee <f3> a6 0f 97 c2 80 da 00 84 d2 74 6b b9 05 00 00 00 48 8d 3d 0d 9a
[30104.278923] RSP: 002b:00007ffdf9b3adf0 EFLAGS: 00010202
[30104.278925] RAX: 0000000000000001 RBX: 000055860bf27775 RCX: 0000000000000009
[30104.278926] RDX: 00007ffdf9b3aeb0 RSI: 000055860bf27775 RDI: 00007f73a9e71236
[30104.278926] RBP: 000055860bf27775 R08: 0000000200000001 R09: 000055860d65e518
[30104.278927] R10: 0000000000000000 R11: 0000000000000000 R12: 00007ffdf9b3bb70
[30104.278928] R13: 0000000000000000 R14: 000000000000000d R15: 00000000000006cd
[30104.278930] Mem-Info:
[30104.278934] active_anon:1430408 inactive_anon:223711 isolated_anon:6
                active_file:1614 inactive_file:1267 isolated_file:225
                unevictable:0 dirty:0 writeback:1 unstable:0
                slab_reclaimable:18597 slab_unreclaimable:76122
                mapped:2313 shmem:61 pagetables:54327 bounce:0
                free:59680 free_pcp:106 free_cma:0
[30104.278937] Node 0 active_anon:5721632kB inactive_anon:894844kB active_file:6456kB inactive_file:5068kB unevictable:0kB isolated(anon):24kB isolated(file):900kB mapped:9252kB dirty:0kB writeback:4kB shmem:244kB shmem_thp: 0kB shmem_pmdmapped: 0kB anon_thp: 0kB writeback_tmp:0kB unstable:0kB all_unreclaimable? no
[30104.278938] Node 0 DMA free:15908kB min:132kB low:164kB high:196kB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB writepending:0kB present:15992kB managed:15908kB mlocked:0kB kernel_stack:0kB pagetables:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB
[30104.278942] lowmem_reserve[]: 0 3340 7802 7802 7802[30104.278944] Node 0 DMA32 free:105108kB min:93836kB low:101052kB high:108268kB active_anon:2462396kB inactive_anon:522216kB active_file:1468kB inactive_file:2464kB unevictable:0kB writepending:0kB present:3627100kB managed:3537264kB mlocked:0kB kernel_stack:33272kB pagetables:98632kB bounce:0kB free_pcp:28kB local_pcp:28kB free_cma:0kB[30104.278947] lowmem_reserve[]: 0 0 4462 4462 4462
[30104.278949] Node 0 Normal free:117704kB min:125348kB low:134988kB high:144628kB active_anon:3258880kB inactive_anon:372628kB active_file:4648kB inactive_file:3124kB unevictable:0kB writepending:4kB present:4702204kB managed:4569588kB mlocked:0kB kernel_stack:45128kB pagetables:118676kB bounce:0kB free_pcp:396kB local_pcp:396kB free_cma:0kB
[30104.278952] lowmem_reserve[]: 0 0 0 0 0
[30104.278954] Node 0 DMA: 1*4kB (U) 0*8kB 0*16kB 1*32kB (U) 2*64kB (U) 1*128kB (U) 1*256kB (U) 0*512kB 1*1024kB (U) 1*2048kB (M) 3*4096kB (M) = 15908kB
[30104.278961] Node 0 DMA32: 2321*4kB (UMEH) 5645*8kB (UMEH) 2074*16kB (UMEH) 627*32kB (UMEH) 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 107692kB
[30104.278967] Node 0 Normal: 1465*4kB (UMEH) 3201*8kB (UMEH) 2713*16kB (UMEH) 1361*32kB (UMEH) 4*64kB (UH) 2*128kB (H) 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 118940kB
[30104.278975] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=1048576kB
[30104.278976] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
[30104.278976] 14034 total pagecache pages
[30104.278978] 10835 pages in swap cache
[30104.278979] Swap cache stats: add 8682931, delete 8671622, find 957935/3697774
[30104.278980] Free swap  = 0kB
[30104.278980] Total swap = 7258108kB
[30104.278981] 2086324 pages RAM
[30104.278981] 0 pages HighMem/MovableOnly
[30104.278982] 55634 pages reserved
[30104.278982] 0 pages cma reserved
[30104.278982] 0 pages hwpoisoned
[30104.278983] Tasks state (memory values in pages):

```

I've removed hugepages, but not sure if I need to reboot or not for changes to take affect.  TOP still shows that all the ram is used, but I know linux handles ram differently than windows and that being out of ram isn't necessarily indicative of a problem.

```

top - 19:32:56 up  8:29, 87 users,  load average: 42.87, 31.51, 25.14
Tasks: 941 total,   1 running, 940 sleeping,   0 stopped,   0 zombie
%Cpu(s): 15.8 us, 53.3 sy,  0.0 ni,  4.4 id, 24.9 wa,  0.0 hi,  1.5 si,  0.0 st
MiB Mem :   7932.4 total,    237.3 free,   7613.8 used,     81.2 buff/cache
MiB Swap:   7088.0 total,      0.0 free,   7088.0 used.    145.8 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                      
 1969 plex      20   0 2502876   2796      0 S  98.3   0.0 179:04.80 Plex Media Serv                              
   70 root      20   0       0      0      0 S  43.6   0.0 126:45.29 kswapd0                                      
 1506 root      20   0 1527568   6628      0 S  29.5   0.1  37:45.13 snapd                                        
 1904 mythtv    20   0 5285216   2000      0 S  20.4   0.0  20:39.63 mythbackend                                  
  814 root       0 -20       0      0      0 S  15.1   0.0  11:51.32 loop0                                        
 6063 master    20   0  388552   4424      0 D  12.5   0.1   0:11.12 snap                                         
 5882 master    20   0   66184   4756      0 D  10.8   0.1   0:09.00 nvidia-settings                              
  668 steam     20   0  146316  72828      0 D   9.1   0.9   0:53.48 starbound_serve                              
 1177 root      20   0       0      0      0 D   6.2   0.0  39:29.97 txg_sync                                     
 1044 root       0 -20       0      0      0 S   5.8   0.0  25:00.56 z_rd_int_2                                   
 1741 debian-+  20   0  269828    264      0 S   5.8   0.0   4:56.10 transmission-da                              
    1 root      20   0  165908   2272      0 D   5.0   0.0   7:25.87 systemd                                      
   54 root      20   0       0      0      0 S   5.0   0.0   2:15.75 kcompactd0                                   
 1043 root       0 -20       0      0      0 S   4.6   0.0  25:02.32 z_rd_int_1                                   
 1049 root       0 -20       0      0      0 S   4.6   0.0  25:08.91 z_rd_int_7                                   
 5765 master    20   0  359488   6660      0 D   4.6   0.1   0:04.81 brisk-menu                                   
  382 root      19  -1  242280    464     16 D   4.3   0.0   9:31.81 systemd-journal                              
 1045 root       0 -20       0      0      0 S   4.3   0.0  25:07.54 z_rd_int_3                                   
 1047 root       0 -20       0      0      0 S   4.3   0.0  25:07.00 z_rd_int_5                                   
 5629 master    20   0 1081420   7872      4 D   4.3   0.1   0:01.86 mate-settings-d                              
12124 root      20   0   11680    316      0 D   4.3   0.0   0:00.18 sshd                                         
11856 root      20   0   11680    316      0 D   3.8   0.0   0:00.42 sshd                                         
26120 steam     20   0 1225736  30268      0 S   3.8   0.4   0:25.66 node                                         
 5769 master    20   0  372616   6220      0 D   3.6   0.1   0:03.89 clock-applet                                 
 6850 master    20   0  174340   1476      0 D   3.6   0.0   0:03.01 goa-daemon                                   
 2403 plex      35  15 1843656    216      0 S   3.4   0.0   3:20.54 Plex Script Hos                              
 9342 master    20   0   17292   3192      0 D   3.4   0.0   0:01.43 recoverable_pro                              
11041 mythtv    20   0   79772    320      0 D   3.4   0.0   0:00.66 mythfilldatabas                              
 5874 master    20   0  195340   1724      0 D   3.1   0.0   0:02.81 evolution-alarm                              
 6630 master    20   0  245204   1264      0 D   3.1   0.0   0:02.32 xdg-desktop-por                              
 1042 root       0 -20       0      0      0 S   2.9   0.0  25:01.59 z_rd_int_0                                   
 1046 root       0 -20       0      0      0 S   2.9   0.0  25:05.78 z_rd_int_4                                   
 1048 root       0 -20       0      0      0 S   2.9   0.0  25:08.30 z_rd_int_6                                   
    2 root      20   0       0      0      0 S   2.6   0.0  15:24.32 kthreadd                                     
 5749 master    20   0  218408   2468      0 D   2.6   0.0   0:01.71 caja                                         
12463 root      20   0   52892    276      0 S   2.6   0.0   0:08.94 smbd                                         
 1492 root      20   0  274616  34012      0 S   2.4   0.4   6:38.77 accounts-daemon                              
 5676 master    20   0  373728   6768     24 D   2.4   0.1   0:03.04 mate-panel                                   
 1500 message+  20   0   11172   3376      0 D   2.2   0.0   2:19.53 dbus-daemon                                  
 1774 master    20   0  348644  14056      0 S   2.2   0.2   0:00.98 chrome-remote-d                              
 2727 plex      20   0  936820    160      0 S   2.2   0.0   2:10.80 Plex Script Hos                              
 5797 master    20   0   12948   2084    676 R   2.2   0.0   0:02.28 top                                          
 5853 master    20   0   65512  13780      0 D   2.2   0.2   0:03.23 applet.py                                    
 7589 root      20   0   52792    416      0 D   2.2   0.0   0:00.15 smbd                                         
 9107 master    30  10   16920   2592      0 D   2.2   0.0   0:01.30 lsb_release                                  
 1934 root      20   0   37936    184      0 S   1.9   0.0   0:52.40 nmbd                                         
 2659 plex      20   0  839104    108      0 S   1.9   0.0   1:58.94 Plex Tuner Serv                              
 7497 steam     20   0  937784  29696      0 D   1.9   0.4   0:12.73 node      

```

I'm hoping that now that I've dumped hugepages and reboot that my problems will be behind me.  If not, I'll need to see whats eating all my ram.  Something must have a memory leak for it to consistently get this bad after a set amount of time.  Any advise on tracking down memory leaks?

EDIT:  I ran TOP and sorted by RAM usage.  No single process is using more than 1%, but I"ve got probably 50 "node" processes each using between 0.5 and 1% of memory.  No clue whats spawning them.

```
top - 19:52:03 up  8:48, 89 users,  load average: 28.39, 32.13, 31.87Tasks: 953 total,  13 running, 940 sleeping,   0 stopped,   0 zombie
%Cpu(s):  0.6 us, 79.3 sy,  0.0 ni,  2.3 id, 15.7 wa,  0.0 hi,  2.0 si,  0.0 st
MiB Mem :   7932.4 total,    242.3 free,   7588.6 used,    101.5 buff/cache
MiB Swap:   7088.0 total,      0.0 free,   7088.0 used.    157.1 avail Mem 


  PID USER      PR  NI    VIRT    RES    SHR S  %CPU  %MEM     TIME+ COMMAND                                      
28715 steam     20   0 1252024  70500      0 S   0.9   0.9   0:03.30 node                                         
32717 steam     20   0  651216  54960      0 S   0.0   0.7   0:03.78 node                                         
10168 steam     20   0   95836  48436      0 S  14.8   0.6   0:44.67 starbound_serve                              
 9447 steam     20   0  949544  48236      0 S   0.0   0.6   0:09.31 node                                         
 2120 master    20   0  652396  48076   7520 S   0.0   0.6   0:01.35 Xvfb                                         
  485 steam     20   0  949460  47512      0 S   0.0   0.6   0:05.53 node                                         
21343 steam     20   0  638312  44752      0 S   0.0   0.6   0:11.38 node                                         
23868 steam     20   0 1225000  43040      0 S   0.6   0.5   0:10.56 node                                         
 4202 steam     20   0 1224732  42540      0 S   0.0   0.5   0:09.13 node                                         
 6372 steam     20   0  643584  41688      0 S   0.0   0.5   0:13.59 node                                         
22744 steam     20   0  642044  41456      0 S   0.0   0.5   0:10.66 node                                         
20533 steam     20   0  649144  41004      0 S   0.0   0.5   0:10.61 node                                         
21145 steam     20   0  642592  40360      0 S   0.0   0.5   0:11.90 node                                         
11984 steam     20   0  642072  40064      0 S   0.0   0.5   0:09.40 node                                         
24305 steam     20   0  642080  40016      0 S   0.0   0.5   0:10.95 node                                         
16404 steam     20   0  644508  39604      0 S   0.0   0.5   0:18.54 node                                         
 6287 steam     20   0  949468  39376      0 S   0.0   0.5   0:15.86 node                                         
 1647 steam     20   0  942872  39080      0 S   0.0   0.5   0:14.17 node                                         
31676 steam     20   0  641544  38704      0 S   0.0   0.5   0:11.71 node                                         
16012 steam     20   0  643072  38668      0 S   0.0   0.5   0:12.70 node                                         
 9858 steam     20   0  642584  38612      0 S   0.0   0.5   0:11.54 node                                         
16953 steam     20   0  645664  38528      0 S   0.0   0.5   0:13.80 node                                         
20227 steam     20   0  642076  38384      0 S   0.0   0.5   0:11.74 node                                         
21692 steam     20   0  644508  38336      0 S   0.0   0.5   0:11.71 node                                         
31571 steam     20   0  641520  38180      0 S   0.0   0.5   0:10.04 node                                         
32290 steam     20   0  802508  37564      0 S   0.0   0.5   0:07.73 node                                         
23041 steam     20   0  642064  37532      0 S   0.0   0.5   0:15.47 node                                         
20838 steam     20   0  642060  37312      0 S   0.0   0.5   0:13.23 node                                         
22010 steam     20   0  948944  36744      0 S   0.0   0.5   0:19.01 node                                         
27430 steam     20   0  643588  36568      0 S   0.0   0.5   0:12.56 node                                         
28846 steam     20   0  641504  36476      0 S   0.0   0.4   0:12.27 node                                         
10416 steam     20   0  949460  36448      0 S   0.0   0.4   0:15.49 node                                         
22973 steam     20   0  642576  36392      0 S   0.0   0.4   0:14.35 node                                         
 5451 steam     20   0  642016  36260      0 S   0.0   0.4   0:13.84 node                                         
10734 steam     20   0  641948  35848      0 S   0.0   0.4   0:13.37 node                                         
 1492 root      20   0  274616  35476      0 S   0.0   0.4   7:07.64 accounts-daemon                              
19950 steam     20   0  649936  34384      0 S   0.0   0.4   0:03.73 node                                         
 3572 steam     20   0  641504  33960      0 S   0.0   0.4   0:12.29 node                                         
16546 steam     20   0 1221928  31064      0 S   0.0   0.4   0:31.00 node                                         
12516 steam     20   0 1221908  31052      0 S   0.0   0.4   0:17.39 node                                         
19570 steam     20   0  872300  30344      0 S   0.0   0.4   0:17.88 node                                         
23610 steam     20   0  937824  30228      0 S   0.0   0.4   0:07.55 node                                         
 5236 steam     20   0  632280  29176      0 S   0.0   0.4   0:13.99 node                                         
20963 steam     20   0  933980  28960      0 S   0.0   0.4   0:25.11 node                                         
26120 steam     20   0 1225736  28596      0 S   0.3   0.4   0:28.48 node                                         
 3539 master    39  19  102708  28588      0 R   4.4   0.4   0:05.62 apt-check                                    
 7497 steam     20   0  937784  28216      0 S   0.0   0.3   0:14.09 node                                         
13217 steam     20   0 1217628  27960      0 S   0.0   0.3   0:50.08 node                                         
 8274 steam     20   0  631300  27188      0 S   0.0   0.3   0:15.50 node 
```

Edit again:  I think I solved it.  I had a server for the game "pokemon showdown" running, and for some reason it was spawning all these node processes.  I killed all the nodes, and it freed up 90% of my ram.  I'm thinking there must have been some change from 18.10 to 19.04 in how node.js behaves for this behavior to have presented itself.  In any case, I've removed the offending software (never used it anyway), and it looks like we're good to go.  I'll post a follow up if issues arise again.  Thanks for the help and being a sounding board.

---

