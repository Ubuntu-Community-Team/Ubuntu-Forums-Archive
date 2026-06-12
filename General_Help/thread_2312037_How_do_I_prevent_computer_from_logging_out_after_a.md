---
title: "How do I prevent computer from logging out after a certain time?"
date: 2016-02-01
forum: General Help
---

### Post by iuval on 2016-02-01
I have a long computation--probably 10 hours. But the computer logs out and terminates the computation (probably terminates other processes as well) after a certain time, not sure exactly how long. I've tried changing the power manager settings to tell it to never shut off. It doesn't shut off, just logs me out and kills Mathematica (the software I use for the computation). Please advise.
Thanks,
Iuval

---

### Post by QDR06VV9 on 2016-02-01
"Light Lock". It's annoyingly on by default.
For a temporary fix: in the terminal:
```
xset s 0 0
```
this should stop the 10 minute blanking problem, to make it more permanent, insert a line with the same command at the start of the /home/username/.profile file.
Kind Regards

---

### Post by Dennis N on 2016-02-01
Since the display is not blanking or sleeping, it could be a system failure of some kind to kill running processes and exit to the login screen. First thing I would do would be to look at the systemd journal for signs of a cause. Check the journal after you are kicked out to login screen.

```
[dmn@Zotac ~]$ journalctl -b
```

There will be lots of lines of output. Near the end, you should see the new lightdm session start. That is where the login screen is opened. You would see something like this:

```
Jan 15 07:46:06 Sydney systemd[1092]: pam_unix(systemd-user:session): session opened for user lightdm by (uid=0)
Jan 15 07:46:06 Sydney systemd-logind[449]: New session c3 of user lightdm.

```
Examine events occuring within 1 second or so before the login session begins and you may see what initiated the logout. (Probably something with the word "fatal" or "failed" in it.)

(Note: I have seen this before. It that case, it was related to X server. Went away after some updates).

---

### Post by ian-weisser on 2016-02-01
> **iuval said:**
> But the computer logs out and terminates the computation (probably terminates other processes as well) after a certain time, not sure exactly how long.

Denns N is right.
Ubuntu doesn't use timed logouts nor power-manager logouts. You can create those if you wish...but you would remember coding them.
An "unexpected logout" is usually caused by a crash of the display server.

---

### Post by Dennis N on 2016-02-01
A tip for examining the journal output more easily - direct the output to a file:

```
[dmn@Zotac ~]$ journalctl -b > ~/Desktop/journal-out.txt
```

This directs the output to a file I chose to be named journal-out.txt  saved on the Desktop. Easy searching, and a permanent record of the event is made.

---

### Post by QDR06VV9 on 2016-02-01
> **ian-weisser said:**
> Denns N is right.
Ubuntu doesn't use timed logouts nor power-manager logouts. You can create those if you wish...but you would remember coding them.
An "unexpected logout" is usually caused by a crash of the display server.
Thanks ian-weisser Sometime's I assume the poster is leading to other problem's with screen blanking(s) or screen-savers.
But yes I too agree that Ubuntu has no default method set for Auto -Log Outs.

> **Dennis N said:**
> A tip for examining the journal output more easily - direct the output to a file:

```
[dmn@Zotac ~]$ journalctl -b > ~/Desktop/journal-out.txt
```

This directs the output to a file I chose to be named journal-out.txt  saved on the Desktop. Easy searching, and a permanent record of the event is made.
I too do something like this,it is very helpful tracking down unexpected mis-haps!
Regards

---

### Post by iuval on 2016-02-01
I don't have that command (journalctl). How do I get it?

I have lubuntu 12.04, but that command is not there.

---

### Post by Dennis N on 2016-02-01
> **iuval said:**
> I have lubuntu 12.04, but that command is not there.

I see. systemd,  needed for that command, did not appear until 15.04. So to get the improvements and benefits of systemd you need to upgrade to 15.10, the current release. The newer OS may even fix your problem. Lubuntu's LXDE components are much better now than in 12.04. That would be my next move if it was my decision.

If you want to examine the log files in 12.04, they are in /var/log and there are multiple logs. Of those logs, kernel.log may have something in it, or perhaps dmesg. You won't find reference to lightdm, as it was not in use way back then.

---

### Post by iuval on 2016-02-02
Thanks everybody. I think the process ran out of memory. Should I get more DRAM? Or free up space on the hard drive? Here is the log from the relevant time:
```
Feb  2 03:31:13 iuval-LT27 kernel: [67628.035972] MathKernel invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0, oom_score_adj=0
Feb  2 03:31:14 iuval-LT27 kernel: [67628.035985] MathKernel cpuset=/ mems_allowed=0
Feb  2 03:31:14 iuval-LT27 kernel: [67628.035993] Pid: 3525, comm: MathKernel Not tainted 3.2.0-75-generic #110-Ubuntu
Feb  2 03:31:14 iuval-LT27 kernel: [67628.036041] Call Trace:
Feb  2 03:31:14 iuval-LT27 kernel: [67628.036064]  [<c10eb905>] dump_header.isra.6+0x85/0xc0
Feb  2 03:31:14 iuval-LT27 kernel: [67628.036077]  [<c10ebb5c>] oom_kill_process+0x5c/0x80
Feb  2 03:31:14 iuval-LT27 kernel: [67628.036088]  [<c10ebf75>] out_of_memory+0xc5/0x1c0
Feb  2 03:31:14 iuval-LT27 kernel: [67628.036107]  [<c10efdec>] __alloc_pages_nodemask+0x72c/0x740
Feb  2 03:31:14 iuval-LT27 kernel: [67628.036122]  [<c10eac58>] filemap_fault+0x1f8/0x370
Feb  2 03:31:14 iuval-LT27 kernel: [67628.036135]  [<c110640a>] __do_fault+0x5a/0x4d0
Feb  2 03:31:14 iuval-LT27 kernel: [67628.036148]  [<c1109b3c>] handle_pte_fault+0xec/0x220
Feb  2 03:31:14 iuval-LT27 kernel: [67628.036160]  [<c1109dc7>] handle_mm_fault+0x157/0x210
Feb  2 03:31:14 iuval-LT27 kernel: [67628.036174]  [<c15800c0>] ? vmalloc_fault+0xf4/0xf4
Feb  2 03:31:14 iuval-LT27 kernel: [67628.036185]  [<c1580218>] do_page_fault+0x158/0x4b0
Feb  2 03:31:14 iuval-LT27 kernel: [67628.036200]  [<c1146a54>] ? poll_select_set_timeout+0x64/0x80
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036211]  [<c11477da>] ? sys_poll+0x5a/0xd0
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036223]  [<c15800c0>] ? vmalloc_fault+0xf4/0xf4
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036235]  [<c157d5b3>] error_code+0x67/0x6c
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036248]  [<c1570000>] ? construct_key+0x28/0xcf
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036256] Mem-Info:
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036262] DMA per-cpu:
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036269] CPU    0: hi:    0, btch:   1 usd:   0
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036277] CPU    1: hi:    0, btch:   1 usd:   0
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036283] Normal per-cpu:
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036290] CPU    0: hi:  186, btch:  31 usd:   0
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036298] CPU    1: hi:  186, btch:  31 usd:   0
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036304] HighMem per-cpu:
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036311] CPU    0: hi:  186, btch:  31 usd:   0
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036319] CPU    1: hi:  186, btch:  31 usd:  22
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036334] active_anon:312941 inactive_anon:167042 isolated_anon:0
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036339]  active_file:0 inactive_file:89 isolated_file:0
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036342]  unevictable:0 dirty:0 writeback:1 unstable:0
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036346]  free:22468 slab_reclaimable:2030 slab_unreclaimable:2873
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036350]  mapped:20 shmem:2818 pagetables:1676 bounce:0
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036374] DMA free:8796kB min:784kB low:980kB high:1176kB active_anon:3536kB inactive_anon:3580kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:0kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:4kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036394] lowmem_reserve[]: 0 865 2007 2007
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036423] Normal free:80556kB min:44012kB low:55012kB high:66016kB active_anon:372624kB inactive_anon:372644kB active_file:0kB inactive_file:232kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:0kB mapped:4kB shmem:0kB slab_reclaimable:8120kB slab_unreclaimable:11492kB kernel_stack:2264kB pagetables:836kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:12977 all_unreclaimable? yes
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036445] lowmem_reserve[]: 0 0 9134 9134
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036469] HighMem free:520kB min:512kB low:15032kB high:29556kB active_anon:875604kB inactive_anon:291944kB active_file:24kB inactive_file:124kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:1169232kB mlocked:0kB dirty:0kB writeback:4kB mapped:76kB shmem:11272kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:5864kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:765 all_unreclaimable? yes
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036489] lowmem_reserve[]: 0 0 0 0
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036501] DMA: 3*4kB 8*8kB 3*16kB 3*32kB 4*64kB 1*128kB 2*256kB 1*512kB 1*1024kB 1*2048kB 1*4096kB = 8796kB
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036533] Normal: 323*4kB 304*8kB 110*16kB 54*32kB 15*64kB 8*128kB 5*256kB 3*512kB 5*1024kB 3*2048kB 14*4096kB = 80620kB
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036566] HighMem: 73*4kB 2*8kB 4*16kB 5*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 532kB
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036598] 4379 total pagecache pages
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036604] 1459 pages in swap cache
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036611] Swap cache stats: add 3340202, delete 3338743, find 1157805/1414295
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036617] Free swap  = 0kB
Feb  2 03:31:15 iuval-LT27 kernel: [67628.036621] Total swap = 1036284kB
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050613] 521920 pages RAM
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050620] 294610 pages HighMem
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050624] 8799 pages reserved
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050628] 2985 pages shared
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050631] 487431 pages non-shared
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050636] [ pid ]   uid  tgid total_vm      rss cpu oom_adj oom_score_adj name
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050660] [  305]     0   305      710        0   0       0             0 upstart-udev-br
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050670] [  308]     0   308      811        1   0     -17         -1000 udevd
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050680] [  530]   102   530      965      109   1       0             0 dbus-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050690] [  561]     0   561     1187        0   0       0             0 bluetoothd
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050700] [  576]   101   576     7766        0   0       0             0 rsyslogd
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050711] [  605]   105   605      891        0   0       0             0 avahi-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050720] [  609]   105   609      865        0   0       0             0 avahi-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050731] [  614]     0   614     4470       21   1       0             0 cupsd
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050740] [  651]   103   651    13338        0   0       0             0 colord
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050750] [  772]     0   772     1806        0   0       0             0 modem-manager
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050760] [  784]     0   784     7995        0   0       0             0 NetworkManager
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050770] [  802]     0   802     6302        0   0       0             0 polkitd
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050780] [  809]     0   809      713        0   0       0             0 upstart-socket-
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050790] [  915]     0   915     1158        0   1       0             0 getty
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050799] [  921]     0   921     1158        0   1       0             0 getty
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050809] [  935]     0   935     1158        0   1       0             0 getty
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050818] [  938]     0   938     1158        0   1       0             0 getty
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050828] [  945]     0   945     1158        0   1       0             0 getty
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050838] [  962]     0   962      577        0   0       0             0 acpid
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050847] [  963]     0   963     4441       25   0       0             0 winbindd
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050857] [  965]     0   965      901       18   0       0             0 irqbalance
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050867] [  967]     0   967      655        1   1       0             0 cron
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050876] [  968]     0   968      618        0   1       0             0 atd
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050886] [  976]     0   976     4441       31   0       0             0 winbindd
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050895] [  979]     0   979     8511        0   1       0             0 lightdm
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050905] [ 1037]   109  1037    79379      120   0       0             0 mysqld
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050915] [ 1066]     0  1066     8520        7   0       0             0 apache2
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050924] [ 1091]    33  1091     8526        0   0       0             0 apache2
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050934] [ 1092]    33  1092     8526        0   1       0             0 apache2
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050943] [ 1093]    33  1093     8526        0   1       0             0 apache2
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050953] [ 1094]    33  1094     8526        0   0       0             0 apache2
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050963] [ 1096]    33  1096     8526        0   0       0             0 apache2
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050973] [ 1112]     0  1112     7532        0   0       0             0 console-kit-dae
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050983] [ 1186]     0  1186     3959       26   0       0             0 accounts-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67628.050992] [ 1316]     7  1316     1986        0   0       0             0 gstoraster
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051002] [ 1317]     7  1317     6070        1   1       0             0 rastertogutenpr
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051012] [ 1318]     0  1318     1580       22   0       0             0 usb
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051021] [ 1332]     0  1332     1158        0   0       0             0 getty
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051031] [ 1378]     0  1378     7218        0   0       0             0 upowerd
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051041] [ 1413]     7  1413    34091        0   1       0             0 gs
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051050] [ 1714]   108  1714     5335        0   1       0             0 rtkit-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051060] [ 1726]  1000  1726     1664        5   0       0             0 menu-cached
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051070] [ 1774]     0  1774     6309       82   1       0             0 udisks-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051079] [ 1775]     0  1775     1640        0   1       0             0 udisks-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051089] [ 2437]     0  2437     7499      430   0       0             0 Xorg
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051098] [ 2496]     0  2496     4162        0   1       0             0 lightdm
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051108] [ 2551]  1000  2551    10756        0   0       0             0 gnome-keyring-d
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051118] [ 2562]  1000  2562     7267        0   0       0             0 lxsession
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051128] [ 2591]  1000  2591     1021        0   0       0             0 ssh-agent
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051137] [ 2594]  1000  2594      985        0   0       0             0 dbus-launch
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051147] [ 2595]  1000  2595      874        0   0       0             0 dbus-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051156] [ 2605]  1000  2605     4411       22   0       0             0 openbox
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051166] [ 2609]  1000  2609    53676      284   0       0             0 lxpanel
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051176] [ 2610]  1000  2610     1944       31   1       0             0 xscreensaver
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051185] [ 2612]  1000  2612    43444        0   0       0             0 pcmanfm
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051195] [ 2613]  1000  2613     7552        0   0       0             0 polkit-gnome-au
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051205] [ 2618]  1000  2618     2103        0   0       0             0 gvfsd
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051214] [ 2620]  1000  2620     8691        0   1       0             0 gvfs-fuse-daemo
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051224] [ 2631]  1000  2631    16781       55   1       0             0 xfce4-power-man
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051234] [ 2632]  1000  2632    24846        0   1       0             0 nm-applet
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051244] [ 2633]  1000  2633     5196        0   0       0             0 xfce4-power-man
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051253] [ 2639]  1000  2639     1603        0   0       0             0 xfconfd
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051263] [ 2644]  1000  2644    33960        0   0       0             0 gnome-sound-app
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051273] [ 2651]  1000  2651    24855        0   0       0             0 pulseaudio
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051282] [ 2653]  1000  2653     2220        0   0       0             0 gconfd-2
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051292] [ 2688]  1000  2688     2468       73   1       0             0 gvfs-gdu-volume
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051302] [ 2696]  1000  2696     5125        0   1       0             0 gvfs-afc-volume
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051311] [ 2699]  1000  2699     2304        0   1       0             0 gvfs-gphoto2-vo
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051322] [ 2783]     0  2783     1494        0   1       0             0 wpa_supplicant
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051331] [ 2803] 65534  2803     1352        0   1       0             0 dnsmasq
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051341] [ 3280]  1000  3280      559        1   0       0             0 Mathematica
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051350] [ 3352]  1000  3352    57703     1431   0       0             0 Mathematica
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051360] [ 3361]  1000  3361   693235   472470   1       0             0 MathKernel
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051370] [ 3526]  1000  3526   123422        0   1       0             0 java
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051380] [ 3948]     0  3948      810        0   0     -17         -1000 udevd
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051390] [ 3949]     0  3949      810        0   0     -17         -1000 udevd
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051400] Out of memory: Kill process 3361 (MathKernel) score 837 or sacrifice child
Feb  2 03:31:15 iuval-LT27 kernel: [67628.051414] Killed process 3526 (java) total-vm:493688kB, anon-rss:0kB, file-rss:0kB
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731704] lxpanel invoked oom-killer: gfp_mask=0x201da, order=0, oom_adj=0, oom_score_adj=0
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731720] lxpanel cpuset=/ mems_allowed=0
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731732] Pid: 2609, comm: lxpanel Not tainted 3.2.0-75-generic #110-Ubuntu
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731740] Call Trace:
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731761]  [<c10eb905>] dump_header.isra.6+0x85/0xc0
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731775]  [<c10ebb5c>] oom_kill_process+0x5c/0x80
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731787]  [<c10ebf75>] out_of_memory+0xc5/0x1c0
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731801]  [<c10efdec>] __alloc_pages_nodemask+0x72c/0x740
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731815]  [<c10eac58>] filemap_fault+0x1f8/0x370
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731827]  [<c110640a>] __do_fault+0x5a/0x4d0
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731840]  [<c1109b3c>] handle_pte_fault+0xec/0x220
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731852]  [<c1109dc7>] handle_mm_fault+0x157/0x210
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731865]  [<c15800c0>] ? vmalloc_fault+0xf4/0xf4
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731876]  [<c1580218>] do_page_fault+0x158/0x4b0
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731889]  [<c1146a54>] ? poll_select_set_timeout+0x64/0x80
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731900]  [<c11477da>] ? sys_poll+0x5a/0xd0
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731911]  [<c15800c0>] ? vmalloc_fault+0xf4/0xf4
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731923]  [<c157d5b3>] error_code+0x67/0x6c
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731935]  [<c1570000>] ? construct_key+0x28/0xcf
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731943] Mem-Info:
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731949] DMA per-cpu:
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731956] CPU    0: hi:    0, btch:   1 usd:   0
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731964] CPU    1: hi:    0, btch:   1 usd:   0
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731971] Normal per-cpu:
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731978] CPU    0: hi:  186, btch:  31 usd: 159
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731986] CPU    1: hi:  186, btch:  31 usd: 103
Feb  2 03:31:15 iuval-LT27 kernel: [67629.731992] HighMem per-cpu:
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732055] CPU    0: hi:  186, btch:  31 usd: 169
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732064] CPU    1: hi:  186, btch:  31 usd: 126
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732080] active_anon:312685 inactive_anon:166925 isolated_anon:0
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732084]  active_file:2 inactive_file:15 isolated_file:0
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732088]  unevictable:0 dirty:0 writeback:2 unstable:0
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732092]  free:22406 slab_reclaimable:2030 slab_unreclaimable:2837
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732096]  mapped:41 shmem:2818 pagetables:1676 bounce:0
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732119] DMA free:8736kB min:784kB low:980kB high:1176kB active_anon:3436kB inactive_anon:3640kB active_file:0kB inactive_file:0kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:15804kB mlocked:0kB dirty:0kB writeback:4kB mapped:0kB shmem:0kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:4kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:0 all_unreclaimable? yes
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732140] lowmem_reserve[]: 0 865 2007 2007
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732169] Normal free:80376kB min:44012kB low:55012kB high:66016kB active_anon:372332kB inactive_anon:372388kB active_file:20kB inactive_file:20kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:885944kB mlocked:0kB dirty:0kB writeback:4kB mapped:104kB shmem:0kB slab_reclaimable:8120kB slab_unreclaimable:11348kB kernel_stack:2088kB pagetables:836kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:5840 all_unreclaimable? yes
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732191] lowmem_reserve[]: 0 0 9134 9134
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732218] HighMem free:512kB min:512kB low:15032kB high:29556kB active_anon:874972kB inactive_anon:291672kB active_file:0kB inactive_file:40kB unevictable:0kB isolated(anon):0kB isolated(file):0kB present:1169232kB mlocked:0kB dirty:0kB writeback:0kB mapped:60kB shmem:11272kB slab_reclaimable:0kB slab_unreclaimable:0kB kernel_stack:0kB pagetables:5864kB unstable:0kB bounce:0kB writeback_tmp:0kB pages_scanned:5778 all_unreclaimable? yes
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732239] lowmem_reserve[]: 0 0 0 0
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732252] DMA: 8*4kB 10*8kB 3*16kB 3*32kB 4*64kB 1*128kB 2*256kB 1*512kB 1*1024kB 1*2048kB 1*4096kB = 8832kB
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732285] Normal: 280*4kB 315*8kB 114*16kB 57*32kB 16*64kB 7*128kB 4*256kB 3*512kB 5*1024kB 3*2048kB 14*4096kB = 80376kB
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732318] HighMem: 68*4kB 2*8kB 4*16kB 5*32kB 0*64kB 0*128kB 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 512kB
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732351] 3998 total pagecache pages
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732357] 1093 pages in swap cache
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732365] Swap cache stats: add 3340384, delete 3339291, find 1157828/1414343
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732372] Free swap  = 3724kB
Feb  2 03:31:15 iuval-LT27 kernel: [67629.732378] Total swap = 1036284kB
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750564] 521920 pages RAM
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750572] 294610 pages HighMem
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750578] 8799 pages reserved
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750583] 3000 pages shared
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750588] 486933 pages non-shared
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750595] [ pid ]   uid  tgid total_vm      rss cpu oom_adj oom_score_adj name
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750623] [  305]     0   305      710        0   0       0             0 upstart-udev-br
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750637] [  308]     0   308      811        1   0     -17         -1000 udevd
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750651] [  530]   102   530      965      109   1       0             0 dbus-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750665] [  561]     0   561     1187        0   0       0             0 bluetoothd
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750679] [  576]   101   576     7766        0   0       0             0 rsyslogd
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750693] [  605]   105   605      891        0   0       0             0 avahi-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750707] [  609]   105   609      865        0   0       0             0 avahi-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750721] [  614]     0   614     4470       21   1       0             0 cupsd
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750735] [  651]   103   651    13338        0   0       0             0 colord
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750749] [  772]     0   772     1806        0   0       0             0 modem-manager
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750762] [  784]     0   784     7995        0   0       0             0 NetworkManager
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750776] [  802]     0   802     6302        0   0       0             0 polkitd
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750789] [  809]     0   809      713        0   0       0             0 upstart-socket-
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750803] [  915]     0   915     1158        0   1       0             0 getty
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750816] [  921]     0   921     1158        0   1       0             0 getty
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750829] [  935]     0   935     1158        0   1       0             0 getty
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750843] [  938]     0   938     1158        0   1       0             0 getty
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750856] [  945]     0   945     1158        0   1       0             0 getty
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750870] [  962]     0   962      577        0   0       0             0 acpid
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750884] [  963]     0   963     4441       25   0       0             0 winbindd
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750897] [  965]     0   965      901       18   0       0             0 irqbalance
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750911] [  967]     0   967      655        1   1       0             0 cron
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750924] [  968]     0   968      618        0   1       0             0 atd
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750938] [  976]     0   976     4441       31   0       0             0 winbindd
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750952] [  979]     0   979     8511        0   1       0             0 lightdm
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750967] [ 1037]   109  1037    79379      160   0       0             0 mysqld
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750981] [ 1066]     0  1066     8520        7   0       0             0 apache2
Feb  2 03:31:15 iuval-LT27 kernel: [67629.750994] [ 1091]    33  1091     8526        0   0       0             0 apache2
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751008] [ 1092]    33  1092     8526        0   1       0             0 apache2
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751022] [ 1093]    33  1093     8526        0   1       0             0 apache2
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751036] [ 1094]    33  1094     8526        0   0       0             0 apache2
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751050] [ 1096]    33  1096     8526        0   0       0             0 apache2
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751065] [ 1112]     0  1112     7532        0   0       0             0 console-kit-dae
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751079] [ 1186]     0  1186     3959       26   0       0             0 accounts-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751092] [ 1316]     7  1316     1986        0   0       0             0 gstoraster
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751105] [ 1317]     7  1317     6070        1   1       0             0 rastertogutenpr
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751118] [ 1318]     0  1318     1580       22   0       0             0 usb
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751130] [ 1332]     0  1332     1158        0   0       0             0 getty
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751142] [ 1378]     0  1378     7218        0   0       0             0 upowerd
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751155] [ 1413]     7  1413    34091        0   1       0             0 gs
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751167] [ 1714]   108  1714     5335        0   1       0             0 rtkit-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751180] [ 1726]  1000  1726     1664       30   0       0             0 menu-cached
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751193] [ 1774]     0  1774     6309       82   1       0             0 udisks-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751206] [ 1775]     0  1775     1640        0   1       0             0 udisks-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751219] [ 2437]     0  2437     7499      430   0       0             0 Xorg
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751231] [ 2496]     0  2496     4162        0   1       0             0 lightdm
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751244] [ 2551]  1000  2551    10756        0   0       0             0 gnome-keyring-d
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751258] [ 2562]  1000  2562     7267        0   0       0             0 lxsession
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751270] [ 2591]  1000  2591     1021        0   0       0             0 ssh-agent
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751283] [ 2594]  1000  2594      985        0   0       0             0 dbus-launch
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751296] [ 2595]  1000  2595      874        0   0       0             0 dbus-daemon
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751309] [ 2605]  1000  2605     4411       22   0       0             0 openbox
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751321] [ 2609]  1000  2609    53676      292   0       0             0 lxpanel
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751334] [ 2610]  1000  2610     1944       31   1       0             0 xscreensaver
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751347] [ 2612]  1000  2612    43444        0   0       0             0 pcmanfm
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751360] [ 2613]  1000  2613     7552        0   0       0             0 polkit-gnome-au
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751373] [ 2618]  1000  2618     2103        0   0       0             0 gvfsd
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751386] [ 2620]  1000  2620     8691        0   1       0             0 gvfs-fuse-daemo
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751400] [ 2631]  1000  2631    16781       55   1       0             0 xfce4-power-man
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751413] [ 2632]  1000  2632    24846        0   1       0             0 nm-applet
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751427] [ 2633]  1000  2633     5196        0   0       0             0 xfce4-power-man
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751441] [ 2639]  1000  2639     1603        0   0       0             0 xfconfd
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751455] [ 2644]  1000  2644    33960        0   0       0             0 gnome-sound-app
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751469] [ 2651]  1000  2651    24855        0   0       0             0 pulseaudio
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751482] [ 2653]  1000  2653     2220        0   0       0             0 gconfd-2
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751496] [ 2688]  1000  2688     2468       73   1       0             0 gvfs-gdu-volume
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751509] [ 2696]  1000  2696     5125        0   1       0             0 gvfs-afc-volume
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751523] [ 2699]  1000  2699     2304        0   1       0             0 gvfs-gphoto2-vo
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751538] [ 2783]     0  2783     1494        0   1       0             0 wpa_supplicant
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751551] [ 2803] 65534  2803     1352        0   1       0             0 dnsmasq
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751565] [ 3280]  1000  3280      559        1   0       0             0 Mathematica
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751577] [ 3352]  1000  3352    57703     1431   0       0             0 Mathematica
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751591] [ 3361]  1000  3361   693235   472154   0       0             0 MathKernel
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751607] [ 3948]     0  3948      810        0   0     -17         -1000 udevd
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751621] [ 3949]     0  3949      810        0   0     -17         -1000 udevd
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751635] Out of memory: Kill process 3361 (MathKernel) score 838 or sacrifice child
Feb  2 03:31:15 iuval-LT27 kernel: [67629.751652] Killed process 3361 (MathKernel) total-vm:2772940kB, anon-rss:1888616kB, file-rss:0kB
```

---

### Post by HermanAB on 2016-02-02
...or you can wiggle the mouse:
[http://www.aeronetworks.ca/2014/06/mouse-wiggler.html](http://www.aeronetworks.ca/2014/06/mouse-wiggler.html)

---

### Post by ian-weisser on 2016-02-02
'out of memory' means RAM/DRAM *and* swap space...which can have unexpected effects, (easily) including display server crash.
I think you have discovered the underlying problem.

You can add more RAM.
You can also increase the size of your swap partition (or create a swap file  overnight). Note that swap is easier and cheaper than RAM, but much, much slower.
They are not exclusive - you can add swap right now (or for a day or two), then decide if RAM is needed...or while RAM is traveling to you. We don't know how quickly you need to complete your task, nor your budget.

Had the problem been hard drive file storage, the error would have been 'no space left on device' or 'i/o error'.

---

### Post by Dennis N on 2016-02-02
> I think the process ran out of memory. Should I get more DRAM?

Good detective work with the log. With the intensive Mathematica computation being carried out, adding more RAM (if possible) to the system would be what I would do to fix the problem.

---

### Post by iuval on 2016-02-03
> **Dennis N said:**
> Good detective work with the log. With the intensive Mathematica computation being carried out, adding more RAM (if possible) to the system would be what I would do to fix the problem.

Thanks. Is there a way to find out how much RAM I have already before opening up the laptop? I looked at the system profiler and benchmark utility, which says I have about 2GBytes of total memory (I assume that is mostly on the hard drive) and about 2.5MBytes of "Kernel Stack" memory. By "Kernel Stack" do they mean RAM? If so, then I wonder if that is already alot of RAM? I wonder if I even have room for more on this tiny inspiron mini 10? I will look, but trying to find out as much as possible before opening it up.

---

### Post by QDR06VV9 on 2016-02-03
Well you could just put this in the terminal
```
free -t
```
This will also show the swap if you have one..
My output from the above is
```
free -t  
                  total        used        free      shared  buff/cache   available
Mem:           3870         882        1971         180        1016        2752
Swap:          3870           0        3870
Total:         7741         882        5842



```

So on mine I have 4 gigs of hardware memory and 4 gigs in swap.
Hope that makes sense

---

### Post by matt_symes on 2016-02-03
Hi

There's also 

```
sudo dmidecode -t memory
```

That'll tell you what you have installed in detail. It'll also tell you how much you can install; how much your motherboard can handle.

You may need to install it. If you do 

```
sudo apt-get install dmidecode
```

Kind regards

---

### Post by Dennis N on 2016-02-03
> I looked at the system profiler and benchmark utility, which says I have about 2GBytes of total memory

Lubuntu's System Profiler and Benchmark is reporting RAM memory (under Computer > Memory). So, if the specs I see when Googling "Inspiron Mini 10" are correct, 2 gB is the maximum you can install. But, be sure to verify this yourself.

---

### Post by matt_symes on 2016-02-03
Hi

> **Dennis N said:**
> Lubuntu's System Profiler and Benchmark is reporting RAM memory (under Computer > Memory). So, if the specs I see when Googling "Inspiron Mini 10" are correct, 2 gB is the maximum you can install.

Blimey ! The weren't joking when they penned it an "Inspiron Mini" were they :)

@OP. 

How much swap do you have ?

You can increase you swap space, either using a swap partition or extending an existing one, or using a swap file that you can create when you need it.

A package like swapspace may also be useful for you. 

```

matthew-xu-16-04:/home/matthew:4 % acse swapspace
swapspace - dynamic swap space manager
matthew-xu-16-04:/home/matthew:4 %
```

While swapping in and out your system will be slow though, and there's always the possibility of swap thrashing occurring.

Kind regards

---

### Post by iuval on 2016-02-03
You mean 2GB is not very much for RAM nowadays? I got the computer really cheap and maybe it is not the best thing for intensive computation. It has a dual processor

I don't know how much swap space I have, will double check. Now i am trying to install 14.04, which is taking forever (more than 4 hours now) and having tons of errors so I can't use that computer. Is 14.04 really worth it? I am using another computer now to type this in.

As far as increasing swap space, it seems like a bad idea, since this is a CPU intensive computation. I don't care if anything else slows down though, I want the computer to do nothing else in fact but this computation.

Oh no! It finished installing, but I am getting a blank desktop upon startup! I can't do anything! WTF! Can I go back to 12.04? It said "system problem" and asked me if I want to report it. Before that it said "error:file not found. Press any key to continue" when starting up.

> **matt_symes said:**
> Hi



Blimey ! The weren't joking when they penned it an "Inspiron Mini" were they :)

@OP. 

How much swap do you have ?

You can increase you swap space, either using a swap partition or extending an existing one, or using a swap file that you can create when you need it.

A package like swapspace may also be useful for you. 

```

matthew-xu-16-04:/home/matthew:4 % acse swapspace
swapspace - dynamic swap space manager
matthew-xu-16-04:/home/matthew:4 %
```

While swapping in and out your system will be slow though, and there's always the possibility of swap thrashing occurring.

Kind regards

---

### Post by matt_symes on 2016-02-03
Hi

> **iuval said:**
> You mean 2GB is not very much for RAM nowadays? I got the computer really cheap and maybe it is not the best thing for intensive computation. It has a dual processor

2GB is not much ram in this day and age. You're running a good spin for a low memory system though, if you're running Lubuntu.

> I don't know how much swap space I have, will double check. Now i am trying to install 14.04, which is taking forever (more than 4 hours now) and having tons of errors so I can't use that computer. Is 14.04 really worth it? I am using another computer now to type this in.

You're installing Ubuntu ?

If it's Ubuntu, you don't really want to be installing Ubuntu on that laptop as it has much heavier in memory usage than Lubuntu and you are having issues with memory anyway.

> As far as increasing swap space, it seems like a bad idea, since this is a CPU intensive computation. I don't care if anything else slows down though, I want the computer to do nothing else in fact but this computation.

You're missing the point. Your system is crashing and logging you out because you don't have enough memory. This has nothing to do with CPU.

You need to increase your memory and (if you have maxed out your laptop with memory) the only way to do this is by increasing virtual memory. To to that you need to add more swap.

There's no other option for you.

> Oh no! It finished installing, but I am getting a blank desktop upon startup! I can't do anything! WTF! Can I go back to 12.04? It said "system problem" and asked me if I want to report it. Before that it said "error:file not found. Press any key to continue" when starting up.

Which flavour of Ubuntu is this ?

Kind regards

---

### Post by iuval on 2016-02-03
I have a bigger problem now that I "upgraded" to 14.04. Nothing works. Blank screen. I started a new thread. Thanks for all the help.

---

### Post by iuval on 2016-02-11
So I was able to get live debian linux onto a usb stick and then boot from it. But just like lububtu 14.04, it can't boot. It gets stalled on partitioning the hard drive. I am trying to find out what is wrong. The hard drive was fine before that. This is what it said for memory:
user@debian:~$ sudo dmidecode -t memory
# dmidecode 2.12
SMBIOS 2.5 present.

Handle 0x000F, DMI type 16, 15 bytes
Physical Memory Array
    Location: System Board Or Motherboard
    Use: System Memory
    Error Correction Type: None
    Maximum Capacity: 2 GB
    Error Information Handle: Not Provided
    Number Of Devices: 1

Handle 0x0010, DMI type 17, 27 bytes
Memory Device
    Array Handle: 0x000F
    Error Information Handle: No Error
    Total Width: 32 bits
    Data Width: 32 bits
    Size: 2048 MB
    Form Factor: SODIMM
    Set: 1
    Locator: M1
    Bank Locator: Bank 0
    Type: DDR2
    Type Detail: Synchronous
    Speed: 533 MHz
    Manufacturer:                 
    Serial Number:         
    Asset Tag:       
    Part Number:                   

It also shows the hard drive as partitioned into a 4Gb and a 246Gb partitions, with the 4Gb partition behaving nicely. But the 246Gb partition gives the following error when I try to open it in the file manager:
Error mounting /dev/sda1 at /media/user/36f962f5-e6cf-4302-b71e-8eb44f83093f: Command-line `mount -t "ext4" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda1" "/media/user/36f962f5-e6cf-4302-b71e-8eb44f83093f"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.

Any ideas on what to do next? I would like to avoid buying another hard drive. I actually have an extra one but in another state.

---

### Post by furtom on 2016-02-11
I bet you are not suffering from *not enough *memory, but rather **bad memory chips**. Hey, they degrade over time like anything else.

There is a reason there is an option to test RAM before installs. Bad memory is a show stopper.

---

### Post by matt_symes on 2016-02-11
Hi

Test your memory as per furtom's suggestion

For the hard drive, try writing zeros to the entire hard drive before installing Linux.

You can do this from the same LiveCD/USB before you install and it will take a while.

You use ddrescue to do this.

Kind regards

---

### Post by iuval on 2016-02-14
Is there an equivalent command in debian linux to ddrescue?

---

### Post by iuval on 2016-02-14
The hard drive looks good right now from the file manager. I look in /media/usr/boot on it and I find all sorts of programs including memtest86+.bin, but I cant type that in a terminal (I guess it is not in /bin on the usb or the hard drive). Should I make it an executable in the boot directory and try to run it?

---

### Post by ian-weisser on 2016-02-14
The 'ddrescue' command is provided by the gddrescue package. The package description explains much.

The file manager does not tell you anything about the state of the hard drive. Use proper diagnostics (SMART and fsck )

Run memtest from the boot menu, not from within an active system.

---

### Post by iuval on 2016-02-14
Is there a debian alternative to ddrescue?

---

### Post by ian-weisser on 2016-02-14
See post #26

---

### Post by iuval on 2016-02-14
None of these (gddrescue, SMART or fsck) are to be found.

---

### Post by ian-weisser on 2016-02-14
> **iuval said:**
> None of these (gddrescue, SMART or fsck) are to be found.

Where and how are you looking?
fsck is in the 'Try Ubuntu' environment. Open a terminal. 'man fsck'
SMART and gddrescue are packages that must be downloaded and installed.

---

### Post by iuval on 2016-02-15
> **ian-weisser said:**
> Where and how are you looking?
fsck is in the 'Try Ubuntu' environment. Open a terminal. 'man fsck'
SMART and gddrescue are packages that must be downloaded and installed.

I was typing fsck into the terminal cmd line. Also looked in lib and root. On both usb and hard drive. But maybe it only comes with ububutu, not debian. I just got another usb stick which I loaded from a mac with the debian bootable distribution (not the live one) and will try to boot later. I tried the non-live boot with my old usb and it snagged at a different point than before, saying it couldn't find the kernel file. It's an old USB, maybe only 4GB or so, so maybe that's the problem. If this time the installation doesn't work, it would be nice to check the hard drive with one of the packages you suggested. The network wasn't working either, so downloading directly might be a problem. I have a usb wireless stick, so maybe that's a problem.

---

### Post by iuval on 2016-02-29
[COLOR=#000000]t was not a hardware problem. It was something about the BIOS that was confusing all the installers. I'm not sure what it was but I changed a few things and was able to install lubuntu 15.02. What a waste of my time.[/COLOR]

---

