---
title: "Orphaned inodes on boot"
date: 2013-02-01
forum: General Help
---

### Post by vajorie on 2013-02-01
I'm not sure for how long (as I accidentally saw the messages recently), but for a while now, I get a "filesystem busy" error for both / and /home partitions on shutdowns and reboots, and on every boot, my encrypted /home partition (but not the unencrypted / partition) gets an fsck scan which throws up "cleared orphaned inode" messages. Can you help?

This is an up-to-date Ubuntu 12.04 installation (clean install, installed about 4-5 months ago). The /home partition is encrypted. The hard disk passes the smart tests. 

Here's the relevant part of my boot.log (this one has a single node while it usually has 5-10 on every boot):
```

fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
/dev/sda1: clean, 256304/610800 files, 1602164/2441216 blocks 
#sda1 is /
/dev/sda6: Clearing orphaned inode 9654965 (uid=1000, gid=1000, mode=0100600, size=86016) 
/dev/sda6: clean, 83844/28999680 files, 30462186/115992576 blocks
#sda6 is /home

```

I put /bin/ps and /bin/lsof into /etc/init.d/umountroot as per a link, which provides the following output
```

  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    6 ?        00:00:01 migration/0
    7 ?        00:00:00 watchdog/0
    8 ?        00:00:00 migration/1
   10 ?        00:00:00 ksoftirqd/1
   12 ?        00:00:00 watchdog/1
   13 ?        00:00:00 migration/2
   15 ?        00:00:00 ksoftirqd/2
   16 ?        00:00:00 watchdog/2
   17 ?        00:00:00 migration/3
   19 ?        00:00:00 ksoftirqd/3
   20 ?        00:00:00 watchdog/3
   21 ?        00:00:00 cpuset
   22 ?        00:00:00 khelper
   23 ?        00:00:00 kdevtmpfs
   24 ?        00:00:00 netns
   26 ?        00:00:00 sync_supers
   27 ?        00:00:00 bdi-default
   28 ?        00:00:00 kintegrityd
   29 ?        00:00:00 kblockd
   30 ?        00:00:00 ata_sff
   31 ?        00:00:00 khubd
   32 ?        00:00:00 md
   35 ?        00:00:00 khungtaskd
   36 ?        00:00:00 kswapd0
   37 ?        00:00:00 ksmd
   38 ?        00:00:00 khugepaged
   39 ?        00:00:00 fsnotify_mark
   40 ?        00:00:00 ecryptfs-kthrea
   41 ?        00:00:00 crypto
   49 ?        00:00:00 kthrotld
   51 ?        00:00:00 scsi_eh_0
   52 ?        00:00:00 scsi_eh_1
   53 ?        00:00:00 scsi_eh_2
   54 ?        00:00:00 scsi_eh_3
   55 ?        00:00:00 scsi_eh_4
   80 ?        00:00:00 devfreq_wq
  215 ?        00:00:00 ttm_swap
  282 ?        00:00:00 kjournald
  300 ?        00:00:00 flush-8:0
  473 ?        00:00:00 irq/43-mei
  492 ?        00:00:00 kmemstick
  496 ?        00:00:00 cfg80211
  537 ?        00:00:00 kpsmoused
  589 ?        00:00:00 iwlwifi
  593 ?        00:00:00 hd-audio0
  721 ?        00:00:00 hd-audio1
  949 ?        00:00:01 kjournald
 1051 ?        00:00:00 krfcommd
 2686 ?        00:00:00 kworker/u:1
 2935 ?        00:00:00 flush-ecryptfs-
14894 ?        00:00:02 kworker/1:2
15793 ?        00:00:00 kworker/u:2
18202 ?        00:00:00 kworker/3:0
19014 ?        00:00:00 kworker/2:1
20456 ?        00:00:00 kworker/0:2
23323 ?        00:00:00 kworker/u:0
24059 ?        00:00:00 kworker/0:0
25054 ?        00:00:00 kworker/1:1
26242 ?        00:00:00 kworker/2:2
27835 ?        00:00:00 kworker/0:1
29289 ?        00:00:01 kworker/3:2
29834 ?        00:00:00 kworker/3:1
30053 ?        00:00:00 kworker/u:3
30054 ?        00:00:00 kworker/2:0
30367 ?        00:00:00 rc
30452 ?        00:00:00 plymouthd
30516 ?        00:00:00 kworker/0:3
30681 ?        00:00:00 S60umountroot
30696 ?        00:00:00 ps
COMMAND     PID USER   FD      TYPE             DEVICE SIZE/OFF    NODE NAME
init          1 root  cwd       DIR                8,1     4096       2 /
init          1 root  rtd       DIR                8,1     4096       2 /
init          1 root  txt       REG                8,1   167192  285261 /sbin/init
init          1 root  mem       REG                8,1    52120   17759 /lib/x86_64-linux-gnu/libnss_files-2.15.so
init          1 root  mem       REG                8,1    47680   17755 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
init          1 root  mem       REG                8,1    97248   17768 /lib/x86_64-linux-gnu/libnsl-2.15.so
init          1 root  mem       REG                8,1    35680   17760 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
init          1 root  mem       REG                8,1  1811128   17749 /lib/x86_64-linux-gnu/libc-2.15.so
init          1 root  mem       REG                8,1    31752   17753 /lib/x86_64-linux-gnu/librt-2.15.so
init          1 root  mem       REG                8,1   135366   17751 /lib/x86_64-linux-gnu/libpthread-2.15.so
init          1 root  mem       REG                8,1   276392   17209 /lib/x86_64-linux-gnu/libdbus-1.so.3.5.8
init          1 root  mem       REG                8,1    38888   17315 /lib/x86_64-linux-gnu/libnih-dbus.so.1.0.0
init          1 root  mem       REG                8,1    96240   17317 /lib/x86_64-linux-gnu/libnih.so.1.0.0
init          1 root  mem       REG                8,1   149280   17763 /lib/x86_64-linux-gnu/ld-2.15.so
init          1 root    0u      CHR                1,3      0t0    3156 /dev/null
init          1 root    1u      CHR                1,3      0t0    3156 /dev/null
init          1 root    2u      CHR                1,3      0t0    3156 /dev/null
init          1 root    3r     FIFO                0,8      0t0    9195 pipe
init          1 root    4w     FIFO                0,8      0t0    9195 pipe
init          1 root    5r     0000                0,9        0    8847 anon_inode
init          1 root    6r     0000                0,9        0    8847 anon_inode
init          1 root    7u     unix 0xffff8801b1374000      0t0    3518 socket
kthreadd      2 root  cwd       DIR                8,1     4096       2 /
kthreadd      2 root  rtd       DIR                8,1     4096       2 /
kthreadd      2 root  txt   unknown                                     /proc/2/exe
ksoftirqd     3 root  cwd       DIR                8,1     4096       2 /
ksoftirqd     3 root  rtd       DIR                8,1     4096       2 /
ksoftirqd     3 root  txt   unknown                                     /proc/3/exe
migration     6 root  cwd       DIR                8,1     4096       2 /
migration     6 root  rtd       DIR                8,1     4096       2 /
migration     6 root  txt   unknown                                     /proc/6/exe
watchdog/     7 root  cwd       DIR                8,1     4096       2 /
watchdog/     7 root  rtd       DIR                8,1     4096       2 /
watchdog/     7 root  txt   unknown                                     /proc/7/exe
migration     8 root  cwd       DIR                8,1     4096       2 /
migration     8 root  rtd       DIR                8,1     4096       2 /
migration     8 root  txt   unknown                                     /proc/8/exe
ksoftirqd    10 root  cwd       DIR                8,1     4096       2 /
ksoftirqd    10 root  rtd       DIR                8,1     4096       2 /
ksoftirqd    10 root  txt   unknown                                     /proc/10/exe
watchdog/    12 root  cwd       DIR                8,1     4096       2 /
watchdog/    12 root  rtd       DIR                8,1     4096       2 /
watchdog/    12 root  txt   unknown                                     /proc/12/exe
migration    13 root  cwd       DIR                8,1     4096       2 /
migration    13 root  rtd       DIR                8,1     4096       2 /
migration    13 root  txt   unknown                                     /proc/13/exe
ksoftirqd    15 root  cwd       DIR                8,1     4096       2 /
ksoftirqd    15 root  rtd       DIR                8,1     4096       2 /
ksoftirqd    15 root  txt   unknown                                     /proc/15/exe
watchdog/    16 root  cwd       DIR                8,1     4096       2 /
watchdog/    16 root  rtd       DIR                8,1     4096       2 /
watchdog/    16 root  txt   unknown                                     /proc/16/exe
migration    17 root  cwd       DIR                8,1     4096       2 /
migration    17 root  rtd       DIR                8,1     4096       2 /
migration    17 root  txt   unknown                                     /proc/17/exe
ksoftirqd    19 root  cwd       DIR                8,1     4096       2 /
ksoftirqd    19 root  rtd       DIR                8,1     4096       2 /
ksoftirqd    19 root  txt   unknown                                     /proc/19/exe
watchdog/    20 root  cwd       DIR                8,1     4096       2 /
watchdog/    20 root  rtd       DIR                8,1     4096       2 /
watchdog/    20 root  txt   unknown                                     /proc/20/exe
cpuset       21 root  cwd       DIR                8,1     4096       2 /
cpuset       21 root  rtd       DIR                8,1     4096       2 /
cpuset       21 root  txt   unknown                                     /proc/21/exe
khelper      22 root  cwd       DIR                8,1     4096       2 /
khelper      22 root  rtd       DIR                8,1     4096       2 /
khelper      22 root  txt   unknown                                     /proc/22/exe
kdevtmpfs    23 root  cwd       DIR                0,5     4180    1025 /
kdevtmpfs    23 root  rtd       DIR                0,5     4180    1025 /
kdevtmpfs    23 root  txt   unknown                                     /proc/23/exe
netns        24 root  cwd       DIR                8,1     4096       2 /
netns        24 root  rtd       DIR                8,1     4096       2 /
netns        24 root  txt   unknown                                     /proc/24/exe
sync_supe    26 root  cwd       DIR                8,1     4096       2 /
sync_supe    26 root  rtd       DIR                8,1     4096       2 /
sync_supe    26 root  txt   unknown                                     /proc/26/exe
bdi-defau    27 root  cwd       DIR                8,1     4096       2 /
bdi-defau    27 root  rtd       DIR                8,1     4096       2 /
bdi-defau    27 root  txt   unknown                                     /proc/27/exe
kintegrit    28 root  cwd       DIR                8,1     4096       2 /
kintegrit    28 root  rtd       DIR                8,1     4096       2 /
kintegrit    28 root  txt   unknown                                     /proc/28/exe
kblockd      29 root  cwd       DIR                8,1     4096       2 /
kblockd      29 root  rtd       DIR                8,1     4096       2 /
kblockd      29 root  txt   unknown                                     /proc/29/exe
ata_sff      30 root  cwd       DIR                8,1     4096       2 /
ata_sff      30 root  rtd       DIR                8,1     4096       2 /
ata_sff      30 root  txt   unknown                                     /proc/30/exe
khubd        31 root  cwd       DIR                8,1     4096       2 /
khubd        31 root  rtd       DIR                8,1     4096       2 /
khubd        31 root  txt   unknown                                     /proc/31/exe
md           32 root  cwd       DIR                8,1     4096       2 /
md           32 root  rtd       DIR                8,1     4096       2 /
md           32 root  txt   unknown                                     /proc/32/exe
khungtask    35 root  cwd       DIR                8,1     4096       2 /
khungtask    35 root  rtd       DIR                8,1     4096       2 /
khungtask    35 root  txt   unknown                                     /proc/35/exe
kswapd0      36 root  cwd       DIR                8,1     4096       2 /
kswapd0      36 root  rtd       DIR                8,1     4096       2 /
kswapd0      36 root  txt   unknown                                     /proc/36/exe
ksmd         37 root  cwd       DIR                8,1     4096       2 /
ksmd         37 root  rtd       DIR                8,1     4096       2 /
ksmd         37 root  txt   unknown                                     /proc/37/exe
khugepage    38 root  cwd       DIR                8,1     4096       2 /
khugepage    38 root  rtd       DIR                8,1     4096       2 /
khugepage    38 root  txt   unknown                                     /proc/38/exe
fsnotify_    39 root  cwd       DIR                8,1     4096       2 /
fsnotify_    39 root  rtd       DIR                8,1     4096       2 /
fsnotify_    39 root  txt   unknown                                     /proc/39/exe
ecryptfs-    40 root  cwd       DIR                8,1     4096       2 /
ecryptfs-    40 root  rtd       DIR                8,1     4096       2 /
ecryptfs-    40 root  txt   unknown                                     /proc/40/exe
crypto       41 root  cwd       DIR                8,1     4096       2 /
crypto       41 root  rtd       DIR                8,1     4096       2 /
crypto       41 root  txt   unknown                                     /proc/41/exe
kthrotld     49 root  cwd       DIR                8,1     4096       2 /
kthrotld     49 root  rtd       DIR                8,1     4096       2 /
kthrotld     49 root  txt   unknown                                     /proc/49/exe
scsi_eh_0    51 root  cwd       DIR                8,1     4096       2 /
scsi_eh_0    51 root  rtd       DIR                8,1     4096       2 /
scsi_eh_0    51 root  txt   unknown                                     /proc/51/exe
scsi_eh_1    52 root  cwd       DIR                8,1     4096       2 /
scsi_eh_1    52 root  rtd       DIR                8,1     4096       2 /
scsi_eh_1    52 root  txt   unknown                                     /proc/52/exe
scsi_eh_2    53 root  cwd       DIR                8,1     4096       2 /
scsi_eh_2    53 root  rtd       DIR                8,1     4096       2 /
scsi_eh_2    53 root  txt   unknown                                     /proc/53/exe
scsi_eh_3    54 root  cwd       DIR                8,1     4096       2 /
scsi_eh_3    54 root  rtd       DIR                8,1     4096       2 /
scsi_eh_3    54 root  txt   unknown                                     /proc/54/exe
scsi_eh_4    55 root  cwd       DIR                8,1     4096       2 /
scsi_eh_4    55 root  rtd       DIR                8,1     4096       2 /
scsi_eh_4    55 root  txt   unknown                                     /proc/55/exe
devfreq_w    80 root  cwd       DIR                8,1     4096       2 /
devfreq_w    80 root  rtd       DIR                8,1     4096       2 /
devfreq_w    80 root  txt   unknown                                     /proc/80/exe
ttm_swap    215 root  cwd       DIR                8,1     4096       2 /
ttm_swap    215 root  rtd       DIR                8,1     4096       2 /
ttm_swap    215 root  txt   unknown                                     /proc/215/exe
kjournald   282 root  cwd       DIR                8,1     4096       2 /
kjournald   282 root  rtd       DIR                8,1     4096       2 /
kjournald   282 root  txt   unknown                                     /proc/282/exe
flush-8:0   300 root  cwd       DIR                8,1     4096       2 /
flush-8:0   300 root  rtd       DIR                8,1     4096       2 /
flush-8:0   300 root  txt   unknown                                     /proc/300/exe
irq/43-me   473 root  cwd       DIR                8,1     4096       2 /
irq/43-me   473 root  rtd       DIR                8,1     4096       2 /
irq/43-me   473 root  txt   unknown                                     /proc/473/exe
kmemstick   492 root  cwd       DIR                8,1     4096       2 /
kmemstick   492 root  rtd       DIR                8,1     4096       2 /
kmemstick   492 root  txt   unknown                                     /proc/492/exe
cfg80211    496 root  cwd       DIR                8,1     4096       2 /
cfg80211    496 root  rtd       DIR                8,1     4096       2 /
cfg80211    496 root  txt   unknown                                     /proc/496/exe
kpsmoused   537 root  cwd       DIR                8,1     4096       2 /
kpsmoused   537 root  rtd       DIR                8,1     4096       2 /
kpsmoused   537 root  txt   unknown                                     /proc/537/exe
iwlwifi     589 root  cwd       DIR                8,1     4096       2 /
iwlwifi     589 root  rtd       DIR                8,1     4096       2 /
iwlwifi     589 root  txt   unknown                                     /proc/589/exe
hd-audio0   593 root  cwd       DIR                8,1     4096       2 /
hd-audio0   593 root  rtd       DIR                8,1     4096       2 /
hd-audio0   593 root  txt   unknown                                     /proc/593/exe
hd-audio1   721 root  cwd       DIR                8,1     4096       2 /
hd-audio1   721 root  rtd       DIR                8,1     4096       2 /
hd-audio1   721 root  txt   unknown                                     /proc/721/exe
kjournald   949 root  cwd       DIR                8,1     4096       2 /
kjournald   949 root  rtd       DIR                8,1     4096       2 /
kjournald   949 root  txt   unknown                                     /proc/949/exe
krfcommd   1051 root  cwd       DIR                8,1     4096       2 /
krfcommd   1051 root  rtd       DIR                8,1     4096       2 /
krfcommd   1051 root  txt   unknown                                     /proc/1051/exe
kworker/u  2686 root  cwd       DIR                8,1     4096       2 /
kworker/u  2686 root  rtd       DIR                8,1     4096       2 /
kworker/u  2686 root  txt   unknown                                     /proc/2686/exe
flush-ecr  2935 root  cwd       DIR                8,1     4096       2 /
flush-ecr  2935 root  rtd       DIR                8,1     4096       2 /
flush-ecr  2935 root  txt   unknown                                     /proc/2935/exe
kworker/1 14894 root  cwd       DIR                8,1     4096       2 /
kworker/1 14894 root  rtd       DIR                8,1     4096       2 /
kworker/1 14894 root  txt   unknown                                     /proc/14894/exe
kworker/u 15793 root  cwd       DIR                8,1     4096       2 /
kworker/u 15793 root  rtd       DIR                8,1     4096       2 /
kworker/u 15793 root  txt   unknown                                     /proc/15793/exe
kworker/3 18202 root  cwd       DIR                8,1     4096       2 /
kworker/3 18202 root  rtd       DIR                8,1     4096       2 /
kworker/3 18202 root  txt   unknown                                     /proc/18202/exe
kworker/2 19014 root  cwd       DIR                8,1     4096       2 /
kworker/2 19014 root  rtd       DIR                8,1     4096       2 /
kworker/2 19014 root  txt   unknown                                     /proc/19014/exe
kworker/0 20456 root  cwd       DIR                8,1     4096       2 /
kworker/0 20456 root  rtd       DIR                8,1     4096       2 /
kworker/0 20456 root  txt   unknown                                     /proc/20456/exe
kworker/u 23323 root  cwd       DIR                8,1     4096       2 /
kworker/u 23323 root  rtd       DIR                8,1     4096       2 /
kworker/u 23323 root  txt   unknown                                     /proc/23323/exe
kworker/0 24059 root  cwd       DIR                8,1     4096       2 /
kworker/0 24059 root  rtd       DIR                8,1     4096       2 /
kworker/0 24059 root  txt   unknown                                     /proc/24059/exe
kworker/1 25054 root  cwd       DIR                8,1     4096       2 /
kworker/1 25054 root  rtd       DIR                8,1     4096       2 /
kworker/1 25054 root  txt   unknown                                     /proc/25054/exe
kworker/2 26242 root  cwd       DIR                8,1     4096       2 /
kworker/2 26242 root  rtd       DIR                8,1     4096       2 /
kworker/2 26242 root  txt   unknown                                     /proc/26242/exe
kworker/0 27835 root  cwd       DIR                8,1     4096       2 /
kworker/0 27835 root  rtd       DIR                8,1     4096       2 /
kworker/0 27835 root  txt   unknown                                     /proc/27835/exe
kworker/3 29289 root  cwd       DIR                8,1     4096       2 /
kworker/3 29289 root  rtd       DIR                8,1     4096       2 /
kworker/3 29289 root  txt   unknown                                     /proc/29289/exe
kworker/3 29834 root  cwd       DIR                8,1     4096       2 /
kworker/3 29834 root  rtd       DIR                8,1     4096       2 /
kworker/3 29834 root  txt   unknown                                     /proc/29834/exe
kworker/u 30053 root  cwd       DIR                8,1     4096       2 /
kworker/u 30053 root  rtd       DIR                8,1     4096       2 /
kworker/u 30053 root  txt   unknown                                     /proc/30053/exe
kworker/2 30054 root  cwd       DIR                8,1     4096       2 /
kworker/2 30054 root  rtd       DIR                8,1     4096       2 /
kworker/2 30054 root  txt   unknown                                     /proc/30054/exe
rc        30367 root  cwd       DIR                8,1     4096       2 /
rc        30367 root  rtd       DIR                8,1     4096       2 /
rc        30367 root  txt       REG                8,1   109768  114044 /bin/dash
rc        30367 root  mem       REG                8,1  1811128   17749 /lib/x86_64-linux-gnu/libc-2.15.so
rc        30367 root  mem       REG                8,1   149280   17763 /lib/x86_64-linux-gnu/ld-2.15.so
rc        30367 root    0u      CHR                5,1      0t0    3165 /dev/console
rc        30367 root    1u      CHR                5,1      0t0    3165 /dev/console
rc        30367 root    2u      CHR                5,1      0t0    3165 /dev/console
rc        30367 root   10r      REG                8,1     8635  148196 /etc/init.d/rc
plymouthd 30452 root  cwd       DIR                8,1     4096       2 /
plymouthd 30452 root  rtd       DIR                8,1     4096       2 /
plymouthd 30452 root  txt       REG                8,1    64752  285095 /sbin/plymouthd
plymouthd 30452 root  mem       REG                8,1    14600   16587 /lib/plymouth/details.so
plymouthd 30452 root  mem       CHR              226,0             9032 /dev/dri/card0
plymouthd 30452 root  mem       REG                8,1    10872  399255 /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
plymouthd 30452 root  mem       REG                8,1    52120   17759 /lib/x86_64-linux-gnu/libnss_files-2.15.so
plymouthd 30452 root  mem       REG                8,1    47680   17755 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
plymouthd 30452 root  mem       REG                8,1    97248   17768 /lib/x86_64-linux-gnu/libnsl-2.15.so
plymouthd 30452 root  mem       REG                8,1    35680   17760 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
plymouthd 30452 root  mem       REG                8,1    22504  228117 /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
plymouthd 30452 root  mem       REG                8,1    10328  228106 /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
plymouthd 30452 root  mem       REG                8,1   170024   17291 /lib/x86_64-linux-gnu/libexpat.so.1.5.2
plymouthd 30452 root  mem       REG                8,1   247896   17346 /lib/x86_64-linux-gnu/libpcre.so.3.12.1
plymouthd 30452 root  mem       REG                8,1    30896  228291 /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
plymouthd 30452 root  mem       REG                8,1  1260960  228104 /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
plymouthd 30452 root  mem       REG                8,1    39336  228139 /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
plymouthd 30452 root  mem       REG                8,1   121232  342187 /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
plymouthd 30452 root  mem       REG                8,1    38960  228065 /usr/lib/x86_64-linux-gnu/libxcb-render.so.0.0.0
plymouthd 30452 root  mem       REG                8,1    10272  228093 /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0.0.0
plymouthd 30452 root  mem       REG                8,1   551176  228548 /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.24.4
plymouthd 30452 root  mem       REG                8,1    14528  228338 /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3200.3
plymouthd 30452 root  mem       REG                8,1   220896  228293 /usr/lib/x86_64-linux-gnu/libfontconfig.so.1.4.4
plymouthd 30452 root  mem       REG                8,1   637160  342809 /usr/lib/x86_64-linux-gnu/libfreetype.so.6.8.0
plymouthd 30452 root  mem       REG                8,1   171984  228532 /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0.3000.0
plymouthd 30452 root  mem       REG                8,1  1000472   17298 /lib/x86_64-linux-gnu/libglib-2.0.so.0.3200.3
plymouthd 30452 root  mem       REG                8,1   322648  228352 /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3200.3
plymouthd 30452 root  mem       REG                8,1   766024  228203 /usr/lib/x86_64-linux-gnu/libcairo.so.2.11000.2
plymouthd 30452 root  mem       REG                8,1   298368  228528 /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0.3000.0
plymouthd 30452 root  mem       REG                8,1    48312  228530 /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0.3000.0
plymouthd 30452 root  mem       REG                8,1    10400   16586 /lib/plymouth/label.so
plymouthd 30452 root  mem       REG                8,1   162776   17350 /lib/x86_64-linux-gnu/libpng12.so.0.46.0
plymouthd 30452 root  mem       REG                8,1    35352   16593 /lib/libply-splash-graphics.so.2.0.0
plymouthd 30452 root  mem       REG                8,1    77176   16588 /lib/plymouth/script.so
plymouthd 30452 root  mem       REG                8,1    92720   17384 /lib/x86_64-linux-gnu/libz.so.1.2.3.4
plymouthd 30452 root  mem       REG                8,1    35096  228542 /usr/lib/x86_64-linux-gnu/libpciaccess.so.0.11.0
plymouthd 30452 root  mem       REG                8,1    22592  342180 /usr/lib/x86_64-linux-gnu/libdrm_nouveau.so.1.0.0
plymouthd 30452 root  mem       REG                8,1    43240  342056 /usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0
plymouthd 30452 root  mem       REG                8,1    39232  342319 /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1.0.1
plymouthd 30452 root  mem       REG                8,1   130936  342178 /usr/lib/x86_64-linux-gnu/libdrm_intel.so.1.0.0
plymouthd 30452 root  mem       REG                8,1    40024   49725 /lib/plymouth/renderers/drm.so
plymouthd 30452 root  mem       REG                8,1   135366   17751 /lib/x86_64-linux-gnu/libpthread-2.15.so
plymouthd 30452 root  mem       REG                8,1  1030512   17757 /lib/x86_64-linux-gnu/libm-2.15.so
plymouthd 30452 root  mem       REG                8,1    14768   16311 /lib/x86_64-linux-gnu/libdl-2.15.so
plymouthd 30452 root  mem       REG                8,1    31752   17753 /lib/x86_64-linux-gnu/librt-2.15.so
plymouthd 30452 root  mem       REG                8,1  1811128   17749 /lib/x86_64-linux-gnu/libc-2.15.so
plymouthd 30452 root  mem       REG                8,1    68464   16592 /lib/libply-splash-core.so.2.0.0
plymouthd 30452 root  mem       REG                8,1    89136   16590 /lib/libply.so.2.0.0
plymouthd 30452 root  mem       REG                8,1   149280   17763 /lib/x86_64-linux-gnu/ld-2.15.so
plymouthd 30452 root  mem       REG                8,1    26258  394744 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
plymouthd 30452 root  mem       REG                8,1   720856  440242 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
plymouthd 30452 root  mem       REG                8,1     1472  516995 /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le64.cache-3
plymouthd 30452 root  mem       REG                8,1    34128  516990 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3
plymouthd 30452 root  mem       REG                8,1     7224  516991 /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le64.cache-3
plymouthd 30452 root  mem       REG                8,1    14392  516977 /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le64.cache-3
plymouthd 30452 root  mem       REG                8,1     2984  517002 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le64.cache-3
plymouthd 30452 root  mem       REG                8,1     2984  516975 /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le64.cache-3
plymouthd 30452 root  mem       REG                8,1    22520  516992 /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le64.cache-3
plymouthd 30452 root  mem       REG                8,1    36360  516720 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le64.cache-3
plymouthd 30452 root  mem       REG                8,1    63840  516974 /var/cache/fontconfig/04aabc0a78ac019cf9454389977116d2-le64.cache-3
plymouthd 30452 root  mem       REG                8,1    12168  516980 /var/cache/fontconfig/385c0604a188198f04d133e54aba7fe7-le64.cache-3
plymouthd 30452 root  mem       REG                8,1     2128  516981 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le64.cache-3
plymouthd 30452 root  mem       REG                8,1    11560  516989 /var/cache/fontconfig/8801497958630a81b71ace7c5f9b32a8-le64.cache-3
plymouthd 30452 root  mem       REG                8,1   186864  518486 /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le64.cache-3
plymouthd 30452 root  mem       REG                8,1    19376  516978 /var/cache/fontconfig/3047814df9a2f067bd2d96a2b9c36e5a-le64.cache-3
plymouthd 30452 root  mem       REG                8,1     1624  516983 /var/cache/fontconfig/56cf4f4769d0f4abc89a4895d7bd3ae1-le64.cache-3
plymouthd 30452 root  mem       REG                8,1     2736  516994 /var/cache/fontconfig/b9d506c9ac06c20b433354fa67a72993-le64.cache-3
plymouthd 30452 root  mem       REG                8,1    17808  516993 /var/cache/fontconfig/b47c4e1ecd0709278f4910c18777a504-le64.cache-3
plymouthd 30452 root  mem       REG                8,1    63856  516998 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le64.cache-3
plymouthd 30452 root  mem       REG                8,1    77104  516986 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le64.cache-3
plymouthd 30452 root  mem       REG                8,1    12920  518487 /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le64.cache-3
plymouthd 30452 root    0u      CHR                4,7      0t0    3177 /dev/tty7
plymouthd 30452 root    1u      CHR                4,7      0t0    3177 /dev/tty7
plymouthd 30452 root    2u      CHR                4,7      0t0    3177 /dev/tty7
plymouthd 30452 root    3u     0000                0,9        0    8847 anon_inode
plymouthd 30452 root    4r     FIFO                0,8      0t0 1143638 pipe
plymouthd 30452 root    5w     FIFO                0,8      0t0 1143638 pipe
plymouthd 30452 root    6u     unix 0xffff88008996a700      0t0 1142416 socket
plymouthd 30452 root    8u      CHR              226,0      0t0    9032 /dev/dri/card0
plymouthd 30452 root    9u      CHR                4,7      0t0    3177 /dev/tty7
kworker/0 30516 root  cwd       DIR                8,1     4096       2 /
kworker/0 30516 root  rtd       DIR                8,1     4096       2 /
kworker/0 30516 root  txt   unknown                                     /proc/30516/exe
S60umount 30681 root  cwd       DIR                8,1     4096       2 /
S60umount 30681 root  rtd       DIR                8,1     4096       2 /
S60umount 30681 root  txt       REG                8,1   109768  114044 /bin/dash
S60umount 30681 root  mem       REG                8,1  1811128   17749 /lib/x86_64-linux-gnu/libc-2.15.so
S60umount 30681 root  mem       REG                8,1   149280   17763 /lib/x86_64-linux-gnu/ld-2.15.so
S60umount 30681 root    0u      CHR                5,1      0t0    3165 /dev/console
S60umount 30681 root    1w      REG                8,1     2498  516269 /var/log/mountdebug
S60umount 30681 root    2u      CHR                5,1      0t0    3165 /dev/console
S60umount 30681 root   10r      REG                8,1     3031  150567 /etc/init.d/umountroot
S60umount 30681 root   11u      CHR                5,1      0t0    3165 /dev/console
lsof      30697 root  cwd       DIR                8,1     4096       2 /
lsof      30697 root  rtd       DIR                8,1     4096       2 /
lsof      30697 root  txt       REG                8,1   131312  326399 /usr/bin/lsof
lsof      30697 root  mem       REG                8,1  1811128   17749 /lib/x86_64-linux-gnu/libc-2.15.so
lsof      30697 root  mem       REG                8,1   149280   17763 /lib/x86_64-linux-gnu/ld-2.15.so
lsof      30697 root    0u      CHR                5,1      0t0    3165 /dev/console
lsof      30697 root    1w      REG                8,1     2498  516269 /var/log/mountdebug
lsof      30697 root    2u      CHR                5,1      0t0    3165 /dev/console
lsof      30697 root    3r      DIR                0,3        0       1 /proc
lsof      30697 root    4r      DIR                0,3        0 1142547 /proc/30697/fd
lsof      30697 root    5w     FIFO                0,8      0t0 1142552 pipe
lsof      30697 root    6r     FIFO                0,8      0t0 1142553 pipe
lsof      30698 root  cwd       DIR                8,1     4096       2 /
lsof      30698 root  rtd       DIR                8,1     4096       2 /
lsof      30698 root  txt       REG                8,1   131312  326399 /usr/bin/lsof
lsof      30698 root  mem       REG                8,1  1811128   17749 /lib/x86_64-linux-gnu/libc-2.15.so
lsof      30698 root  mem       REG                8,1   149280   17763 /lib/x86_64-linux-gnu/ld-2.15.so
lsof      30698 root    4r     FIFO                0,8      0t0 1142552 pipe
lsof      30698 root    7w     FIFO                0,8      0t0 1142553 pipe

```


Any ideas what I may be dealing with?


PS. The relevant part of my umountroot, for reference: 
```

MOUNT_FORCE_OPT=
	[ "$(uname -s)" = "GNU/kFreeBSD" ] && MOUNT_FORCE_OPT=-f
	# This:
	#     mount -n -o remount,ro /
	# will act on a bind mount of / if there is one.
	# See #339023 and the comment in checkroot.sh
	/bin/ps > /var/log/mountdebug
	/usr/bin/lsof >> /var/log/mountdebug
	/bin/sync 
	/bin/sync 
	/bin/sync 
	mount    $MOUNT_FORCE_OPT -n -o remount,ro -t dummytype dummydev / 2>/dev/null \
	|| mount $MOUNT_FORCE_OPT -n -o remount,ro              dummydev / 2>/dev/null \
	|| mount $MOUNT_FORCE_OPT -n -o remount,ro                       /
	ES=$?
	[ "$VERBOSE" = no ] || log_action_end_msg $ES

```

---

### Post by vajorie on 2013-02-02
a quick update -- I found that if I log off and only then shutdown the computer (through lightdm's login screen), the system unmounts filesystems without problems and I don't get any orphaned inodes in the subsequent boot at my /home partition... 

any ideas as to what may be causing this issue?

---

### Post by vajorie on 2013-02-05
bump?

here's the log file from my umountroot file when there are no orphaned inodes (when the filesystem was unmounted cleanly), in case it might be significant:

```

  PID TTY          TIME CMD
    1 ?        00:00:00 init
    2 ?        00:00:00 kthreadd
    3 ?        00:00:00 ksoftirqd/0
    6 ?        00:00:00 migration/0
    7 ?        00:00:00 watchdog/0
    8 ?        00:00:00 migration/1
   10 ?        00:00:00 ksoftirqd/1
   12 ?        00:00:00 watchdog/1
   13 ?        00:00:00 migration/2
   15 ?        00:00:00 ksoftirqd/2
   16 ?        00:00:00 watchdog/2
   17 ?        00:00:00 migration/3
   19 ?        00:00:00 ksoftirqd/3
   20 ?        00:00:00 watchdog/3
   21 ?        00:00:00 cpuset
   22 ?        00:00:00 khelper
   23 ?        00:00:00 kdevtmpfs
   24 ?        00:00:00 netns
   26 ?        00:00:00 sync_supers
   27 ?        00:00:00 bdi-default
   28 ?        00:00:00 kintegrityd
   29 ?        00:00:00 kblockd
   30 ?        00:00:00 ata_sff
   31 ?        00:00:00 khubd
   32 ?        00:00:00 md
   35 ?        00:00:00 khungtaskd
   36 ?        00:00:00 kswapd0
   37 ?        00:00:00 ksmd
   38 ?        00:00:00 khugepaged
   39 ?        00:00:00 fsnotify_mark
   40 ?        00:00:00 ecryptfs-kthrea
   41 ?        00:00:00 crypto
   49 ?        00:00:00 kthrotld
   50 ?        00:00:00 scsi_eh_0
   51 ?        00:00:00 scsi_eh_1
   52 ?        00:00:00 scsi_eh_2
   53 ?        00:00:00 scsi_eh_3
   54 ?        00:00:00 scsi_eh_4
   55 ?        00:00:02 kworker/u:2
   80 ?        00:00:00 devfreq_wq
  213 ?        00:00:00 ttm_swap
  283 ?        00:00:00 kjournald
  743 ?        00:00:00 irq/43-mei
  744 ?        00:00:00 kpsmoused
  755 ?        00:00:00 kmemstick
  758 ?        00:00:00 cfg80211
  784 ?        00:00:00 iwlwifi
  862 ?        00:00:00 hd-audio0
  901 ?        00:00:00 hd-audio1
 1192 ?        00:00:00 krfcommd
 2574 ?        00:00:00 flush-8:0
 5351 ?        00:00:00 kworker/1:2
12725 ?        00:00:00 kworker/1:1
12733 ?        00:00:00 kworker/2:0
13245 ?        00:00:00 kworker/0:1
13772 ?        00:00:00 kworker/3:1
13978 ?        00:00:01 kworker/u:0
20936 ?        00:00:00 kworker/1:0
20937 ?        00:00:00 kworker/0:2
20938 ?        00:00:00 kworker/2:1
22978 ?        00:00:01 kworker/3:2
24079 ?        00:00:00 kworker/2:3
24112 ?        00:00:00 rc
24194 ?        00:00:00 plymouthd
24399 ?        00:00:00 S60umountroot
24414 ?        00:00:00 ps
29722 ?        00:00:01 kworker/0:0
30097 ?        00:00:00 kworker/2:2
30816 ?        00:00:00 kworker/u:1
COMMAND     PID USER   FD      TYPE             DEVICE SIZE/OFF   NODE NAME
init          1 root  cwd       DIR                8,1     4096      2 /
init          1 root  rtd       DIR                8,1     4096      2 /
init          1 root  txt       REG                8,1   167192 285261 /sbin/init
init          1 root  mem       REG                8,1    52120  17759 /lib/x86_64-linux-gnu/libnss_files-2.15.so
init          1 root  mem       REG                8,1    47680  17755 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
init          1 root  mem       REG                8,1    97248  17768 /lib/x86_64-linux-gnu/libnsl-2.15.so
init          1 root  mem       REG                8,1    35680  17760 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
init          1 root  mem       REG                8,1  1811128  17749 /lib/x86_64-linux-gnu/libc-2.15.so
init          1 root  mem       REG                8,1    31752  17753 /lib/x86_64-linux-gnu/librt-2.15.so
init          1 root  mem       REG                8,1   135366  17751 /lib/x86_64-linux-gnu/libpthread-2.15.so
init          1 root  mem       REG                8,1   276392  17209 /lib/x86_64-linux-gnu/libdbus-1.so.3.5.8
init          1 root  mem       REG                8,1    38888  17315 /lib/x86_64-linux-gnu/libnih-dbus.so.1.0.0
init          1 root  mem       REG                8,1    96240  17317 /lib/x86_64-linux-gnu/libnih.so.1.0.0
init          1 root  mem       REG                8,1   149280  17763 /lib/x86_64-linux-gnu/ld-2.15.so
init          1 root    0u      CHR                1,3      0t0   1029 /dev/null
init          1 root    1u      CHR                1,3      0t0   1029 /dev/null
init          1 root    2u      CHR                1,3      0t0   1029 /dev/null
init          1 root    3r     FIFO                0,8      0t0   9085 pipe
init          1 root    4w     FIFO                0,8      0t0   9085 pipe
init          1 root    5r     0000                0,9        0   8834 anon_inode
init          1 root    6r     0000                0,9        0   8834 anon_inode
init          1 root    7u     unix 0xffff8801ac2a8000      0t0   9086 socket
kthreadd      2 root  cwd       DIR                8,1     4096      2 /
kthreadd      2 root  rtd       DIR                8,1     4096      2 /
kthreadd      2 root  txt   unknown                                    /proc/2/exe
ksoftirqd     3 root  cwd       DIR                8,1     4096      2 /
ksoftirqd     3 root  rtd       DIR                8,1     4096      2 /
ksoftirqd     3 root  txt   unknown                                    /proc/3/exe
migration     6 root  cwd       DIR                8,1     4096      2 /
migration     6 root  rtd       DIR                8,1     4096      2 /
migration     6 root  txt   unknown                                    /proc/6/exe
watchdog/     7 root  cwd       DIR                8,1     4096      2 /
watchdog/     7 root  rtd       DIR                8,1     4096      2 /
watchdog/     7 root  txt   unknown                                    /proc/7/exe
migration     8 root  cwd       DIR                8,1     4096      2 /
migration     8 root  rtd       DIR                8,1     4096      2 /
migration     8 root  txt   unknown                                    /proc/8/exe
ksoftirqd    10 root  cwd       DIR                8,1     4096      2 /
ksoftirqd    10 root  rtd       DIR                8,1     4096      2 /
ksoftirqd    10 root  txt   unknown                                    /proc/10/exe
watchdog/    12 root  cwd       DIR                8,1     4096      2 /
watchdog/    12 root  rtd       DIR                8,1     4096      2 /
watchdog/    12 root  txt   unknown                                    /proc/12/exe
migration    13 root  cwd       DIR                8,1     4096      2 /
migration    13 root  rtd       DIR                8,1     4096      2 /
migration    13 root  txt   unknown                                    /proc/13/exe
ksoftirqd    15 root  cwd       DIR                8,1     4096      2 /
ksoftirqd    15 root  rtd       DIR                8,1     4096      2 /
ksoftirqd    15 root  txt   unknown                                    /proc/15/exe
watchdog/    16 root  cwd       DIR                8,1     4096      2 /
watchdog/    16 root  rtd       DIR                8,1     4096      2 /
watchdog/    16 root  txt   unknown                                    /proc/16/exe
migration    17 root  cwd       DIR                8,1     4096      2 /
migration    17 root  rtd       DIR                8,1     4096      2 /
migration    17 root  txt   unknown                                    /proc/17/exe
ksoftirqd    19 root  cwd       DIR                8,1     4096      2 /
ksoftirqd    19 root  rtd       DIR                8,1     4096      2 /
ksoftirqd    19 root  txt   unknown                                    /proc/19/exe
watchdog/    20 root  cwd       DIR                8,1     4096      2 /
watchdog/    20 root  rtd       DIR                8,1     4096      2 /
watchdog/    20 root  txt   unknown                                    /proc/20/exe
cpuset       21 root  cwd       DIR                8,1     4096      2 /
cpuset       21 root  rtd       DIR                8,1     4096      2 /
cpuset       21 root  txt   unknown                                    /proc/21/exe
khelper      22 root  cwd       DIR                8,1     4096      2 /
khelper      22 root  rtd       DIR                8,1     4096      2 /
khelper      22 root  txt   unknown                                    /proc/22/exe
kdevtmpfs    23 root  cwd       DIR                0,5     4180   1025 /
kdevtmpfs    23 root  rtd       DIR                0,5     4180   1025 /
kdevtmpfs    23 root  txt   unknown                                    /proc/23/exe
netns        24 root  cwd       DIR                8,1     4096      2 /
netns        24 root  rtd       DIR                8,1     4096      2 /
netns        24 root  txt   unknown                                    /proc/24/exe
sync_supe    26 root  cwd       DIR                8,1     4096      2 /
sync_supe    26 root  rtd       DIR                8,1     4096      2 /
sync_supe    26 root  txt   unknown                                    /proc/26/exe
bdi-defau    27 root  cwd       DIR                8,1     4096      2 /
bdi-defau    27 root  rtd       DIR                8,1     4096      2 /
bdi-defau    27 root  txt   unknown                                    /proc/27/exe
kintegrit    28 root  cwd       DIR                8,1     4096      2 /
kintegrit    28 root  rtd       DIR                8,1     4096      2 /
kintegrit    28 root  txt   unknown                                    /proc/28/exe
kblockd      29 root  cwd       DIR                8,1     4096      2 /
kblockd      29 root  rtd       DIR                8,1     4096      2 /
kblockd      29 root  txt   unknown                                    /proc/29/exe
ata_sff      30 root  cwd       DIR                8,1     4096      2 /
ata_sff      30 root  rtd       DIR                8,1     4096      2 /
ata_sff      30 root  txt   unknown                                    /proc/30/exe
khubd        31 root  cwd       DIR                8,1     4096      2 /
khubd        31 root  rtd       DIR                8,1     4096      2 /
khubd        31 root  txt   unknown                                    /proc/31/exe
md           32 root  cwd       DIR                8,1     4096      2 /
md           32 root  rtd       DIR                8,1     4096      2 /
md           32 root  txt   unknown                                    /proc/32/exe
khungtask    35 root  cwd       DIR                8,1     4096      2 /
khungtask    35 root  rtd       DIR                8,1     4096      2 /
khungtask    35 root  txt   unknown                                    /proc/35/exe
kswapd0      36 root  cwd       DIR                8,1     4096      2 /
kswapd0      36 root  rtd       DIR                8,1     4096      2 /
kswapd0      36 root  txt   unknown                                    /proc/36/exe
ksmd         37 root  cwd       DIR                8,1     4096      2 /
ksmd         37 root  rtd       DIR                8,1     4096      2 /
ksmd         37 root  txt   unknown                                    /proc/37/exe
khugepage    38 root  cwd       DIR                8,1     4096      2 /
khugepage    38 root  rtd       DIR                8,1     4096      2 /
khugepage    38 root  txt   unknown                                    /proc/38/exe
fsnotify_    39 root  cwd       DIR                8,1     4096      2 /
fsnotify_    39 root  rtd       DIR                8,1     4096      2 /
fsnotify_    39 root  txt   unknown                                    /proc/39/exe
ecryptfs-    40 root  cwd       DIR                8,1     4096      2 /
ecryptfs-    40 root  rtd       DIR                8,1     4096      2 /
ecryptfs-    40 root  txt   unknown                                    /proc/40/exe
crypto       41 root  cwd       DIR                8,1     4096      2 /
crypto       41 root  rtd       DIR                8,1     4096      2 /
crypto       41 root  txt   unknown                                    /proc/41/exe
kthrotld     49 root  cwd       DIR                8,1     4096      2 /
kthrotld     49 root  rtd       DIR                8,1     4096      2 /
kthrotld     49 root  txt   unknown                                    /proc/49/exe
scsi_eh_0    50 root  cwd       DIR                8,1     4096      2 /
scsi_eh_0    50 root  rtd       DIR                8,1     4096      2 /
scsi_eh_0    50 root  txt   unknown                                    /proc/50/exe
scsi_eh_1    51 root  cwd       DIR                8,1     4096      2 /
scsi_eh_1    51 root  rtd       DIR                8,1     4096      2 /
scsi_eh_1    51 root  txt   unknown                                    /proc/51/exe
scsi_eh_2    52 root  cwd       DIR                8,1     4096      2 /
scsi_eh_2    52 root  rtd       DIR                8,1     4096      2 /
scsi_eh_2    52 root  txt   unknown                                    /proc/52/exe
scsi_eh_3    53 root  cwd       DIR                8,1     4096      2 /
scsi_eh_3    53 root  rtd       DIR                8,1     4096      2 /
scsi_eh_3    53 root  txt   unknown                                    /proc/53/exe
scsi_eh_4    54 root  cwd       DIR                8,1     4096      2 /
scsi_eh_4    54 root  rtd       DIR                8,1     4096      2 /
scsi_eh_4    54 root  txt   unknown                                    /proc/54/exe
kworker/u    55 root  cwd       DIR                8,1     4096      2 /
kworker/u    55 root  rtd       DIR                8,1     4096      2 /
kworker/u    55 root  txt   unknown                                    /proc/55/exe
devfreq_w    80 root  cwd       DIR                8,1     4096      2 /
devfreq_w    80 root  rtd       DIR                8,1     4096      2 /
devfreq_w    80 root  txt   unknown                                    /proc/80/exe
ttm_swap    213 root  cwd       DIR                8,1     4096      2 /
ttm_swap    213 root  rtd       DIR                8,1     4096      2 /
ttm_swap    213 root  txt   unknown                                    /proc/213/exe
kjournald   283 root  cwd       DIR                8,1     4096      2 /
kjournald   283 root  rtd       DIR                8,1     4096      2 /
kjournald   283 root  txt   unknown                                    /proc/283/exe
irq/43-me   743 root  cwd       DIR                8,1     4096      2 /
irq/43-me   743 root  rtd       DIR                8,1     4096      2 /
irq/43-me   743 root  txt   unknown                                    /proc/743/exe
kpsmoused   744 root  cwd       DIR                8,1     4096      2 /
kpsmoused   744 root  rtd       DIR                8,1     4096      2 /
kpsmoused   744 root  txt   unknown                                    /proc/744/exe
kmemstick   755 root  cwd       DIR                8,1     4096      2 /
kmemstick   755 root  rtd       DIR                8,1     4096      2 /
kmemstick   755 root  txt   unknown                                    /proc/755/exe
cfg80211    758 root  cwd       DIR                8,1     4096      2 /
cfg80211    758 root  rtd       DIR                8,1     4096      2 /
cfg80211    758 root  txt   unknown                                    /proc/758/exe
iwlwifi     784 root  cwd       DIR                8,1     4096      2 /
iwlwifi     784 root  rtd       DIR                8,1     4096      2 /
iwlwifi     784 root  txt   unknown                                    /proc/784/exe
hd-audio0   862 root  cwd       DIR                8,1     4096      2 /
hd-audio0   862 root  rtd       DIR                8,1     4096      2 /
hd-audio0   862 root  txt   unknown                                    /proc/862/exe
hd-audio1   901 root  cwd       DIR                8,1     4096      2 /
hd-audio1   901 root  rtd       DIR                8,1     4096      2 /
hd-audio1   901 root  txt   unknown                                    /proc/901/exe
krfcommd   1192 root  cwd       DIR                8,1     4096      2 /
krfcommd   1192 root  rtd       DIR                8,1     4096      2 /
krfcommd   1192 root  txt   unknown                                    /proc/1192/exe
flush-8:0  2574 root  cwd       DIR                8,1     4096      2 /
flush-8:0  2574 root  rtd       DIR                8,1     4096      2 /
flush-8:0  2574 root  txt   unknown                                    /proc/2574/exe
kworker/1  5351 root  cwd       DIR                8,1     4096      2 /
kworker/1  5351 root  rtd       DIR                8,1     4096      2 /
kworker/1  5351 root  txt   unknown                                    /proc/5351/exe
kworker/1 12725 root  cwd       DIR                8,1     4096      2 /
kworker/1 12725 root  rtd       DIR                8,1     4096      2 /
kworker/1 12725 root  txt   unknown                                    /proc/12725/exe
kworker/2 12733 root  cwd       DIR                8,1     4096      2 /
kworker/2 12733 root  rtd       DIR                8,1     4096      2 /
kworker/2 12733 root  txt   unknown                                    /proc/12733/exe
kworker/0 13245 root  cwd       DIR                8,1     4096      2 /
kworker/0 13245 root  rtd       DIR                8,1     4096      2 /
kworker/0 13245 root  txt   unknown                                    /proc/13245/exe
kworker/3 13772 root  cwd       DIR                8,1     4096      2 /
kworker/3 13772 root  rtd       DIR                8,1     4096      2 /
kworker/3 13772 root  txt   unknown                                    /proc/13772/exe
kworker/u 13978 root  cwd       DIR                8,1     4096      2 /
kworker/u 13978 root  rtd       DIR                8,1     4096      2 /
kworker/u 13978 root  txt   unknown                                    /proc/13978/exe
kworker/1 20936 root  cwd       DIR                8,1     4096      2 /
kworker/1 20936 root  rtd       DIR                8,1     4096      2 /
kworker/1 20936 root  txt   unknown                                    /proc/20936/exe
kworker/0 20937 root  cwd       DIR                8,1     4096      2 /
kworker/0 20937 root  rtd       DIR                8,1     4096      2 /
kworker/0 20937 root  txt   unknown                                    /proc/20937/exe
kworker/2 20938 root  cwd       DIR                8,1     4096      2 /
kworker/2 20938 root  rtd       DIR                8,1     4096      2 /
kworker/2 20938 root  txt   unknown                                    /proc/20938/exe
kworker/3 22978 root  cwd       DIR                8,1     4096      2 /
kworker/3 22978 root  rtd       DIR                8,1     4096      2 /
kworker/3 22978 root  txt   unknown                                    /proc/22978/exe
kworker/2 24079 root  cwd       DIR                8,1     4096      2 /
kworker/2 24079 root  rtd       DIR                8,1     4096      2 /
kworker/2 24079 root  txt   unknown                                    /proc/24079/exe
rc        24112 root  cwd       DIR                8,1     4096      2 /
rc        24112 root  rtd       DIR                8,1     4096      2 /
rc        24112 root  txt       REG                8,1   109768 114044 /bin/dash
rc        24112 root  mem       REG                8,1  1811128  17749 /lib/x86_64-linux-gnu/libc-2.15.so
rc        24112 root  mem       REG                8,1   149280  17763 /lib/x86_64-linux-gnu/ld-2.15.so
rc        24112 root    0u      CHR                5,1      0t0   1038 /dev/console
rc        24112 root    1u      CHR                5,1      0t0   1038 /dev/console
rc        24112 root    2u      CHR                5,1      0t0   1038 /dev/console
rc        24112 root   10r      REG                8,1     8635 148196 /etc/init.d/rc
plymouthd 24194 root  cwd       DIR                8,1     4096      2 /
plymouthd 24194 root  rtd       DIR                8,1     4096      2 /
plymouthd 24194 root  txt       REG                8,1    64752 285095 /sbin/plymouthd
plymouthd 24194 root  mem       REG                8,1    14600  16587 /lib/plymouth/details.so
plymouthd 24194 root  mem       CHR              226,0            1366 /dev/dri/card0
plymouthd 24194 root  mem       REG                8,1    10872 399255 /usr/lib/x86_64-linux-gnu/pango/1.6.0/modules/pango-basic-fc.so
plymouthd 24194 root  mem       REG                8,1    52120  17759 /lib/x86_64-linux-gnu/libnss_files-2.15.so
plymouthd 24194 root  mem       REG                8,1    47680  17755 /lib/x86_64-linux-gnu/libnss_nis-2.15.so
plymouthd 24194 root  mem       REG                8,1    97248  17768 /lib/x86_64-linux-gnu/libnsl-2.15.so
plymouthd 24194 root  mem       REG                8,1    35680  17760 /lib/x86_64-linux-gnu/libnss_compat-2.15.so
plymouthd 24194 root  mem       REG                8,1    22504 228117 /usr/lib/x86_64-linux-gnu/libXdmcp.so.6.0.0
plymouthd 24194 root  mem       REG                8,1    10328 228106 /usr/lib/x86_64-linux-gnu/libXau.so.6.0.0
plymouthd 24194 root  mem       REG                8,1   170024  17291 /lib/x86_64-linux-gnu/libexpat.so.1.5.2
plymouthd 24194 root  mem       REG                8,1   247896  17346 /lib/x86_64-linux-gnu/libpcre.so.3.12.1
plymouthd 24194 root  mem       REG                8,1    30896 228291 /usr/lib/x86_64-linux-gnu/libffi.so.6.0.0
plymouthd 24194 root  mem       REG                8,1  1260960 228104 /usr/lib/x86_64-linux-gnu/libX11.so.6.3.0
plymouthd 24194 root  mem       REG                8,1    39336 228139 /usr/lib/x86_64-linux-gnu/libXrender.so.1.3.0
plymouthd 24194 root  mem       REG                8,1   121232 342187 /usr/lib/x86_64-linux-gnu/libxcb.so.1.1.0
plymouthd 24194 root  mem       REG                8,1    38960 228065 /usr/lib/x86_64-linux-gnu/libxcb-render.so.0.0.0
plymouthd 24194 root  mem       REG                8,1    10272 228093 /usr/lib/x86_64-linux-gnu/libxcb-shm.so.0.0.0
plymouthd 24194 root  mem       REG                8,1   551176 228548 /usr/lib/x86_64-linux-gnu/libpixman-1.so.0.24.4
plymouthd 24194 root  mem       REG                8,1    14528 228338 /usr/lib/x86_64-linux-gnu/libgmodule-2.0.so.0.3200.3
plymouthd 24194 root  mem       REG                8,1   220896 228293 /usr/lib/x86_64-linux-gnu/libfontconfig.so.1.4.4
plymouthd 24194 root  mem       REG                8,1   637160 342809 /usr/lib/x86_64-linux-gnu/libfreetype.so.6.8.0
plymouthd 24194 root  mem       REG                8,1   171984 228532 /usr/lib/x86_64-linux-gnu/libpangoft2-1.0.so.0.3000.0
plymouthd 24194 root  mem       REG                8,1  1000472  17298 /lib/x86_64-linux-gnu/libglib-2.0.so.0.3200.3
plymouthd 24194 root  mem       REG                8,1   322648 228352 /usr/lib/x86_64-linux-gnu/libgobject-2.0.so.0.3200.3
plymouthd 24194 root  mem       REG                8,1   766024 228203 /usr/lib/x86_64-linux-gnu/libcairo.so.2.11000.2
plymouthd 24194 root  mem       REG                8,1   298368 228528 /usr/lib/x86_64-linux-gnu/libpango-1.0.so.0.3000.0
plymouthd 24194 root  mem       REG                8,1    48312 228530 /usr/lib/x86_64-linux-gnu/libpangocairo-1.0.so.0.3000.0
plymouthd 24194 root  mem       REG                8,1    10400  16586 /lib/plymouth/label.so
plymouthd 24194 root  mem       REG                8,1   162776  17350 /lib/x86_64-linux-gnu/libpng12.so.0.46.0
plymouthd 24194 root  mem       REG                8,1    35352  16593 /lib/libply-splash-graphics.so.2.0.0
plymouthd 24194 root  mem       REG                8,1    77176  16588 /lib/plymouth/script.so
plymouthd 24194 root  mem       REG                8,1    92720  17384 /lib/x86_64-linux-gnu/libz.so.1.2.3.4
plymouthd 24194 root  mem       REG                8,1    35096 228542 /usr/lib/x86_64-linux-gnu/libpciaccess.so.0.11.0
plymouthd 24194 root  mem       REG                8,1    22592 342180 /usr/lib/x86_64-linux-gnu/libdrm_nouveau.so.1.0.0
plymouthd 24194 root  mem       REG                8,1    43240 342056 /usr/lib/x86_64-linux-gnu/libdrm.so.2.4.0
plymouthd 24194 root  mem       REG                8,1    39232 342319 /usr/lib/x86_64-linux-gnu/libdrm_radeon.so.1.0.1
plymouthd 24194 root  mem       REG                8,1   130936 342178 /usr/lib/x86_64-linux-gnu/libdrm_intel.so.1.0.0
plymouthd 24194 root  mem       REG                8,1    40024  49725 /lib/plymouth/renderers/drm.so
plymouthd 24194 root  mem       REG                8,1   135366  17751 /lib/x86_64-linux-gnu/libpthread-2.15.so
plymouthd 24194 root  mem       REG                8,1  1030512  17757 /lib/x86_64-linux-gnu/libm-2.15.so
plymouthd 24194 root  mem       REG                8,1    14768  16311 /lib/x86_64-linux-gnu/libdl-2.15.so
plymouthd 24194 root  mem       REG                8,1    31752  17753 /lib/x86_64-linux-gnu/librt-2.15.so
plymouthd 24194 root  mem       REG                8,1  1811128  17749 /lib/x86_64-linux-gnu/libc-2.15.so
plymouthd 24194 root  mem       REG                8,1    68464  16592 /lib/libply-splash-core.so.2.0.0
plymouthd 24194 root  mem       REG                8,1    89136  16590 /lib/libply.so.2.0.0
plymouthd 24194 root  mem       REG                8,1   149280  17763 /lib/x86_64-linux-gnu/ld-2.15.so
plymouthd 24194 root  mem       REG                8,1    26258 394744 /usr/lib/x86_64-linux-gnu/gconv/gconv-modules.cache
plymouthd 24194 root  mem       REG                8,1   720856 440242 /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
plymouthd 24194 root  mem       REG                8,1     1472 516995 /var/cache/fontconfig/c05880de57d1f5e948fdfacc138775d9-le64.cache-3
plymouthd 24194 root  mem       REG                8,1    34128 516990 /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-le64.cache-3
plymouthd 24194 root  mem       REG                8,1     7224 516991 /var/cache/fontconfig/99e8ed0e538f840c565b6ed5dad60d56-le64.cache-3
plymouthd 24194 root  mem       REG                8,1    14392 516977 /var/cache/fontconfig/2cd17615ca594fa2959ae173292e504c-le64.cache-3
plymouthd 24194 root  mem       REG                8,1     2984 517002 /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-le64.cache-3
plymouthd 24194 root  mem       REG                8,1     2984 516975 /var/cache/fontconfig/0d8c3b2ac0904cb8a57a757ad11a4a08-le64.cache-3
plymouthd 24194 root  mem       REG                8,1    22520 516992 /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-le64.cache-3
plymouthd 24194 root  mem       REG                8,1    36360 516720 /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-le64.cache-3
plymouthd 24194 root  mem       REG                8,1    63840 516974 /var/cache/fontconfig/04aabc0a78ac019cf9454389977116d2-le64.cache-3
plymouthd 24194 root  mem       REG                8,1    12168 516980 /var/cache/fontconfig/385c0604a188198f04d133e54aba7fe7-le64.cache-3
plymouthd 24194 root  mem       REG                8,1     2128 516981 /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-le64.cache-3
plymouthd 24194 root  mem       REG                8,1    11560 516989 /var/cache/fontconfig/8801497958630a81b71ace7c5f9b32a8-le64.cache-3
plymouthd 24194 root  mem       REG                8,1   186864 518486 /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-le64.cache-3
plymouthd 24194 root  mem       REG                8,1    19376 516978 /var/cache/fontconfig/3047814df9a2f067bd2d96a2b9c36e5a-le64.cache-3
plymouthd 24194 root  mem       REG                8,1     1624 516983 /var/cache/fontconfig/56cf4f4769d0f4abc89a4895d7bd3ae1-le64.cache-3
plymouthd 24194 root  mem       REG                8,1     2736 516994 /var/cache/fontconfig/b9d506c9ac06c20b433354fa67a72993-le64.cache-3
plymouthd 24194 root  mem       REG                8,1    17808 516993 /var/cache/fontconfig/b47c4e1ecd0709278f4910c18777a504-le64.cache-3
plymouthd 24194 root  mem       REG                8,1    63856 516998 /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-le64.cache-3
plymouthd 24194 root  mem       REG                8,1    77104 516986 /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-le64.cache-3
plymouthd 24194 root  mem       REG                8,1    12920 518487 /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-le64.cache-3
plymouthd 24194 root    0u      CHR                4,7      0t0   1050 /dev/tty7
plymouthd 24194 root    1u      CHR                4,7      0t0   1050 /dev/tty7
plymouthd 24194 root    2u      CHR                4,7      0t0   1050 /dev/tty7
plymouthd 24194 root    3u     0000                0,9        0   8834 anon_inode
plymouthd 24194 root    4r     FIFO                0,8      0t0 635072 pipe
plymouthd 24194 root    5w     FIFO                0,8      0t0 635072 pipe
plymouthd 24194 root    6u     unix 0xffff88016792fa80      0t0 634601 socket
plymouthd 24194 root    8u      CHR              226,0      0t0   1366 /dev/dri/card0
plymouthd 24194 root    9u      CHR                4,7      0t0   1050 /dev/tty7
S60umount 24399 root  cwd       DIR                8,1     4096      2 /
S60umount 24399 root  rtd       DIR                8,1     4096      2 /
S60umount 24399 root  txt       REG                8,1   109768 114044 /bin/dash
S60umount 24399 root  mem       REG                8,1  1811128  17749 /lib/x86_64-linux-gnu/libc-2.15.so
S60umount 24399 root  mem       REG                8,1   149280  17763 /lib/x86_64-linux-gnu/ld-2.15.so
S60umount 24399 root    0u      CHR                5,1      0t0   1038 /dev/console
S60umount 24399 root    1w      REG                8,1     2388 516269 /var/log/mountdebug
S60umount 24399 root    2u      CHR                5,1      0t0   1038 /dev/console
S60umount 24399 root   10r      REG                8,1     3081 149282 /etc/init.d/umountroot
S60umount 24399 root   11u      CHR                5,1      0t0   1038 /dev/console
lsof      24415 root  cwd       DIR                8,1     4096      2 /
lsof      24415 root  rtd       DIR                8,1     4096      2 /
lsof      24415 root  txt       REG                8,1   131312 326399 /usr/bin/lsof
lsof      24415 root  mem       REG                8,1  1811128  17749 /lib/x86_64-linux-gnu/libc-2.15.so
lsof      24415 root  mem       REG                8,1   149280  17763 /lib/x86_64-linux-gnu/ld-2.15.so
lsof      24415 root    0u      CHR                5,1      0t0   1038 /dev/console
lsof      24415 root    1w      REG                8,1     2388 516269 /var/log/mountdebug
lsof      24415 root    2u      CHR                5,1      0t0   1038 /dev/console
lsof      24415 root    3r      DIR                0,3        0      1 /proc
lsof      24415 root    4r      DIR                0,3        0 637635 /proc/24415/fd
lsof      24415 root    5w     FIFO                0,8      0t0 637640 pipe
lsof      24415 root    6r     FIFO                0,8      0t0 637641 pipe
lsof      24416 root  cwd       DIR                8,1     4096      2 /
lsof      24416 root  rtd       DIR                8,1     4096      2 /
lsof      24416 root  txt       REG                8,1   131312 326399 /usr/bin/lsof
lsof      24416 root  mem       REG                8,1  1811128  17749 /lib/x86_64-linux-gnu/libc-2.15.so
lsof      24416 root  mem       REG                8,1   149280  17763 /lib/x86_64-linux-gnu/ld-2.15.so
lsof      24416 root    4r     FIFO                0,8      0t0 637640 pipe
lsof      24416 root    7w     FIFO                0,8      0t0 637641 pipe
kworker/0 29722 root  cwd       DIR                8,1     4096      2 /
kworker/0 29722 root  rtd       DIR                8,1     4096      2 /
kworker/0 29722 root  txt   unknown                                    /proc/29722/exe
kworker/2 30097 root  cwd       DIR                8,1     4096      2 /
kworker/2 30097 root  rtd       DIR                8,1     4096      2 /
kworker/2 30097 root  txt   unknown                                    /proc/30097/exe
kworker/u 30816 root  cwd       DIR                8,1     4096      2 /
kworker/u 30816 root  rtd       DIR                8,1     4096      2 /
kworker/u 30816 root  txt   unknown                                    /proc/30816/exe

```

---

### Post by rnerwein on 2013-02-05
> **vajorie said:**
> a quick update -- I found that if I log off and only then shutdown the computer (through lightdm's login screen), the system unmounts filesystems without problems and I don't get any orphaned inodes in the subsequent boot at my /home partition... 

any ideas as to what may be causing this issue?
hi
the output of: lsof /home and lsof /home/your_account would be helpful. the output when the system don't shutdown clean (orphanded inodes).
cheers

---

### Post by vajorie on 2013-02-06
> **rnerwein said:**
> hi
the output of: lsof /home and lsof /home/your_account would be helpful. the output when the system don't shutdown clean (orphanded inodes).
cheers

Thanks, I put them in but for some reason I'm not getting orphaned inodes now.. I'll post back when/if I do..

---

