---
title: "pdftohtml"
date: 2017-08-27
forum: General Help
---

### Post by cmcanulty on 2017-08-27
Recently pdftohtml is using 25% of cpu, yet it isn't showing as even in synaptic. I think it is part of poppler-utils but I can't remove that or I lose a ton of needed stuff. When I end process on it, it immediately regenerates. Thank you

[ATTACH=CONFIG]276517[/ATTACH]

[ATTACH=CONFIG]276518[/ATTACH]

---

### Post by SeijiSensei on 2017-08-27
Is it working on converting a PDF?  What do you see if you run "top" from the command prompt?

It could be that there are two processes, a parent and a child.  Killing only the child will often result in it being respawned by the parent.  Run "ps aux | grep pdftohtml | grep -v grep" to see how many processes are tied to that program.

---

### Post by vasa1 on 2017-08-28
Maybe you're trying to convert a pdf file that pdftohtml just can't handle?

Have you tried any of the options listed by *pdftohtml --help*?

---

### Post by cmcanulty on 2017-08-28
I was not running anything except Firefox, today it is not running so I will wait and reply when it happens again. I wonder if it is related to a Firefox addon I have called "Print Friendly & PDF". But i have had that addon for years and never this issue. Thank you, I will run those commands when it happens again

---

### Post by cmcanulty on 2017-08-28
Now it is running and I am not doing any pdf operations in firefox or anywhere else. Also top shows it using 100% of cpu

```
top - 08:36:16 up  1:24,  2 users,  load average: 1.67, 2.10, 2.19
Tasks: 238 total,   2 running, 236 sleeping,   0 stopped,   0 zombie
%Cpu(s): 25.8 us,  2.4 sy,  0.2 ni, 67.3 id,  4.0 wa,  0.0 hi,  0.4 si,  0.0 st
KiB Mem :  7967936 total,  1842316 free,  1301184 used,  4824436 buff/cache
KiB Swap:  4235260 total,  4235260 free,        0 used.  6201104 avail Mem 

  PID USER      PR  NI    VIRT    RES    SHR S  %CPU %MEM     TIME+ COMMAND
24489 cmcanul+  20   0  114644  75952   6196 R 100.0  1.0   7:04.24 pdftohtml
24818 cmcanul+  20   0 2898908 924816 150460 S  25.0 11.6   2:41.92 firefox
    1 root      20   0  120132   6436   4112 S   0.0  0.1   0:02.21 systemd
    2 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kthreadd
    3 root      20   0       0      0      0 S   0.0  0.0   0:00.19 ksoftirqd/0
    5 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/0:+
    7 root      20   0       0      0      0 S   0.0  0.0   0:08.46 rcu_sched
    8 root      20   0       0      0      0 S   0.0  0.0   0:00.00 rcu_bh
    9 root      rt   0       0      0      0 S   0.0  0.0   0:00.11 migration/0
   10 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 watchdog/0
   11 root      rt   0       0      0      0 S   0.0  0.0   0:00.02 watchdog/1
   12 root      rt   0       0      0      0 S   0.0  0.0   0:00.12 migration/1
   13 root      20   0       0      0      0 S   0.0  0.0   0:00.42 ksoftirqd/1
   15 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/1:+
   16 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 watchdog/2
   17 root      rt   0       0      0      0 S   0.0  0.0   0:00.10 migration/2
   18 root      20   0       0      0      0 S   0.0  0.0   0:00.39 ksoftirqd/2
   20 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/2:+
   21 root      rt   0       0      0      0 S   0.0  0.0   0:00.01 watchdog/3
   22 root      rt   0       0      0      0 S   0.0  0.0   0:00.10 migration/3
   23 root      20   0       0      0      0 S   0.0  0.0   0:00.32 ksoftirqd/3
   25 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kworker/3:+
   26 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kdevtmpfs
   27 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 netns
   28 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 perf
   29 root      20   0       0      0      0 S   0.0  0.0   0:00.00 khungtaskd
   30 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 writeback
   31 root      25   5       0      0      0 S   0.0  0.0   0:00.00 ksmd
   32 root      39  19       0      0      0 S   0.0  0.0   0:01.60 khugepaged
   33 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 crypto
   34 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kintegrityd
   35 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   36 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kblockd
   37 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ata_sff
   38 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 md
   39 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 devfreq_wq
   43 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kswapd0
   44 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 vmstat
   45 root      20   0       0      0      0 S   0.0  0.0   0:00.00 fsnotify_m+
   46 root      20   0       0      0      0 S   0.0  0.0   0:00.00 ecryptfs-k+
   62 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kthrotld
   63 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 acpi_therm+
   66 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   67 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   68 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   69 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   70 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   71 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   72 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   73 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
   74 root      20   0       0      0      0 S   0.0  0.0   0:00.94 kworker/u1+
   78 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ipv6_addrc+
   79 root      20   0       0      0      0 S   0.0  0.0   0:04.10 kworker/0:2
   93 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 deferwq
   94 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 charger_ma+
  132 root      20   0       0      0      0 S   0.0  0.0   0:00.04 ips-adjust
  133 root      20   0       0      0      0 S   0.0  0.0   0:00.74 ips-monitor
  134 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kpsmoused
  135 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_0
  136 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 scsi_tmf_0
  137 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_1
  138 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 scsi_tmf_1
  139 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_2
  140 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 scsi_tmf_2
  141 root      20   0       0      0      0 S   0.0  0.0   0:00.00 scsi_eh_3
  142 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 scsi_tmf_3
  153 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
  154 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
  241 root       0 -20       0      0      0 S   0.0  0.0   0:00.71 kworker/3:+
  242 root       0 -20       0      0      0 S   0.0  0.0   0:00.06 kworker/2:+
  244 root      20   0       0      0      0 S   0.0  0.0   0:00.28 jbd2/sda1-8
  245 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-rsv-c+
  276 root       0 -20       0      0      0 S   0.0  0.0   0:00.06 kworker/1:+
  280 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kauditd
  282 root      20   0   35400   4652   4220 S   0.0  0.1   0:00.46 systemd-jo+
  340 root      20   0   46264   5600   3076 S   0.0  0.1   0:00.93 systemd-ud+
  392 root       0 -20       0      0      0 S   0.0  0.0   0:00.08 kworker/0:+
  418 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop0
  422 root       0 -20       0      0      0 S   0.0  0.0   0:00.03 loop1
  427 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop2
  431 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop3
  434 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop4
  444 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 loop5
  491 root     -51   0       0      0      0 S   0.0  0.0   0:00.00 irq/27-mei+
  543 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 cfg80211
  544 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 kvm-irqfd-+
  663 root      20   0       0      0      0 S   0.0  0.0   0:00.00 wl_event_h+
  757 root      20   0       0      0      0 S   0.0  0.0   0:00.40 jbd2/sda2-8
  758 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 ext4-rsv-c+
  958 syslog    20   0  256396   3408   2704 S   0.0  0.0   0:00.14 rsyslogd
  961 avahi     20   0   45048   3772   3252 S   0.0  0.0   0:00.22 avahi-daem+
  971 root      20   0   29008   3008   2724 S   0.0  0.0   0:00.00 cron
  983 message+  20   0   44276   5212   3568 S   0.0  0.1   0:01.82 dbus-daemon
 1000 avahi     20   0   44788    344     12 S   0.0  0.0   0:00.00 avahi-daem+
 1038 root      20   0  449696  17060  13824 S   0.0  0.2   0:01.93 NetworkMan+
 1048 root      20   0  337348  10864   7116 S   0.0  0.1   0:00.03 ModemManag+
 1051 daemon    20   0   26044   2196   1996 S   0.0  0.0   0:00.00 atd
 1055 root      20   0  429568   5136    928 S   0.0  0.1   0:00.00 osspd
 1072 root      20   0   29880   1596   1380 S   0.0  0.0   0:00.00 cgmanager
 1075 root      20   0  276124   6788   5764 S   0.0  0.1   0:00.46 accounts-d+
 1084 root      20   0    4400   1312   1220 S   0.0  0.0   0:00.17 acpid
 1091 root      20   0   28640   3212   2800 S   0.0  0.0   0:00.05 systemd-lo+
 1111 root      15  -5  371000  25768  14112 S   0.0  0.3   0:01.01 snapd
 1183 root       0 -20   23168  10692   3552 S   0.0  0.1   0:00.91 atop
 1221 root      20   0   19472    248      0 S   0.0  0.0   0:00.17 irqbalance
 1227 colord    20   0  304988  15052   8568 S   0.0  0.2   0:00.97 colord
 1302 root      20   0  350376   6392   5460 S   0.0  0.1   0:00.07 lightdm
 1304 root      20   0  278804  10256   5848 S   0.0  0.1   0:00.39 polkitd
 1317 root      20   0   10000   4824   4320 S   0.0  0.1   0:00.10 sshd
 1359 root      20   0   54336  13584   2628 S   0.0  0.2   0:03.78 x2gocleans+
 1360 root      20   0   44024   6460   5804 S   0.0  0.1   0:00.24 wpa_suppli+
 1374 root      20   0   16124   3676   2816 S   0.0  0.0   0:00.00 dhclient
 1415 cmcanul+  20   0   45240   5124   4276 S   0.0  0.1   0:00.04 systemd
 1416 cmcanul+  20   0   90152   2108     16 S   0.0  0.0   0:00.00 (sd-pam)
 1436 nobody    20   0   52868   4224   3840 S   0.0  0.1   0:00.58 dnsmasq
 1895 root      20   0   95124   6048   5100 S   0.0  0.1   0:00.01 ocserv-main
 1931 whoopsie  20   0  364744  11776  10224 S   0.0  0.1   0:00.04 whoopsie
 2004 root      20   0   15940   1824   1684 S   0.0  0.0   0:00.00 agetty
 2042 xrdp      20   0   22832    460      0 S   0.0  0.0   0:00.00 xrdp
 2044 root      20   0  193148   5972   5220 S   0.0  0.1   0:00.98 hamachid
 2045 root      20   0   35360    428      0 S   0.0  0.0   0:00.00 xrdp-sesman
 2048 root      20   0   95144   3368   2420 S   0.0  0.0   0:00.00 ocserv-sec+
 2128 root      20   0  168892  13860   8864 S   0.0  0.2   0:04.12 teamviewerd
 2141 root      20   0  394428  33276  25612 S   0.0  0.4   0:00.23 apache2
 2266 root      20   0  240004   5964   4124 S   0.0  0.1   0:00.07 nmbd
 2267 root      20   0  287268   9044   6908 S   0.0  0.1   0:00.06 winbindd
 2283 root      20   0  287264   8864   6728 S   0.0  0.1   0:00.01 winbindd
 2286 root      20   0  337924  15852  13292 S   0.0  0.2   0:00.01 smbd
 2287 root      20   0   97528   5900   4972 S   0.0  0.1   0:00.00 x11vnc
 2292 root      20   0  329808   4424   1972 S   0.0  0.1   0:00.00 smbd
 2295 root      20   0  287268   6448   4300 S   0.0  0.1   0:00.00 winbindd
 2296 root      20   0  287268   4028   1896 S   0.0  0.1   0:00.00 winbindd
 2297 root      20   0  337924   8596   6020 S   0.0  0.1   0:00.04 smbd
 2512 cmcanul+  20   0    4604    204      0 S   0.0  0.0   0:00.00 ssh-agent
 3506 cmcanul+  20   0   28316  10888   1644 S   0.0  0.1   0:00.08 wineserver
 5861 root      20   0  347152   9700   8556 S   0.0  0.1   0:00.21 upowerd
 6190 root      20   0  432424  10584   6364 S   0.0  0.1   0:00.94 udisksd
 6254 cmcanul+  20   0   45964   4204   3580 S   0.0  0.1   0:00.05 upstart
 6291 cmcanul+   9 -11  416732  11356   8028 S   0.0  0.1   0:17.92 pulseaudio
 6292 rtkit     21   1  183544   3108   2824 S   0.0  0.0   0:00.05 rtkit-daem+
 7059 root      20   0       0      0      0 S   0.0  0.0   0:01.27 kworker/3:1
10950 www-data  20   0  394452   9700   2028 S   0.0  0.1   0:00.00 apache2
10951 www-data  20   0  394452   9700   2028 S   0.0  0.1   0:00.00 apache2
10952 www-data  20   0  394452   9700   2028 S   0.0  0.1   0:00.00 apache2
10953 www-data  20   0  394452   9700   2028 S   0.0  0.1   0:00.00 apache2
10954 www-data  20   0  394452   9700   2028 S   0.0  0.1   0:00.00 apache2
10979 root      20   0  170828  11484   6548 S   0.0  0.1   0:00.13 cupsd
10981 root      20   0  274960   9564   8316 S   0.0  0.1   0:00.03 cups-brows+
14687 root      20   0       0      0      0 S   0.0  0.0   0:01.67 kworker/3:2
14717 root      20   0   81360   3748   3148 S   0.0  0.0   0:00.00 cron
14718 cmcanul+  20   0    4508    856    780 S   0.0  0.0   0:00.00 sh
14719 cmcanul+  20   0  536188  37132  28828 S   0.0  0.5   0:04.41 bookworm
19245 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 xfsalloc
19248 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 xfs_mru_ca+
19255 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsIO
19256 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsCommit
19257 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsCommit
19258 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsCommit
19259 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsCommit
19260 root      20   0       0      0      0 S   0.0  0.0   0:00.00 jfsSync
19298 root       0 -20       0      0      0 S   0.0  0.0   0:00.00 bioset
19489 root      20   0       0      0      0 S   0.0  0.0   0:00.08 kworker/u1+
20448 root      20   0       0      0      0 S   0.0  0.0   0:00.35 kworker/1:2
20450 root      20   0  315904  73828  60748 S   0.0  0.9   0:34.14 Xorg
20590 root      20   0  256336   7216   6156 S   0.0  0.1   0:00.01 lightdm
20593 root      20   0  123516  14192   6952 S   0.0  0.2   0:00.45 x11vnc
20745 cmcanul+  20   0  220240  23976   6588 S   0.0  0.3   0:02.26 gnome-keyr+
20750 cmcanul+  20   0   46224   4448   3596 S   0.0  0.1   0:00.13 upstart
20766 root      20   0   16128   3772   2864 S   0.0  0.0   0:00.00 dhclient
20836 cmcanul+  20   0   32864    280     12 S   0.0  0.0   0:00.00 upstart-ud+
20841 cmcanul+  20   0   43600   4020   2804 S   0.0  0.1   0:00.37 dbus-daemon
20873 cmcanul+  20   0   32852    304     12 S   0.0  0.0   0:00.02 upstart-db+
20875 cmcanul+  20   0   32800    304     12 S   0.0  0.0   0:00.03 upstart-db+
20888 cmcanul+  20   0   41292    388     12 S   0.0  0.0   0:00.00 upstart-fi+
20898 cmcanul+  20   0  166540    720    456 S   0.0  0.0   0:00.00 gpg-agent
21000 root      20   0       0      0      0 S   0.0  0.0   0:00.79 kworker/2:0
21053 cmcanul+  20   0    4508   1712   1608 S   0.0  0.0   0:00.00 sh
21065 cmcanul+  20   0  327012  19568  17208 S   0.0  0.2   0:00.15 xfce4-sess+
21069 cmcanul+  20   0   47744   5008   4424 S   0.0  0.1   0:00.05 xfconfd
21073 cmcanul+  20   0    4604    208      0 S   0.0  0.0   0:00.00 ssh-agent
21077 cmcanul+  20   0  175028  21140  17916 S   0.0  0.3   0:01.19 xfwm4
21081 cmcanul+  20   0  410936  46864  22776 S   0.0  0.6   0:02.95 xfce4-panel
21082 cmcanul+  20   0  368396  17240  14748 S   0.0  0.2   0:00.53 xfsettingsd
21086 cmcanul+  20   0  405140  24536  19136 S   0.0  0.3   0:00.19 Thunar
21088 cmcanul+  20   0  460124  44364  23092 S   0.0  0.6   0:20.74 xfdesktop
21094 cmcanul+  20   0   22372   1156    992 S   0.0  0.0   0:00.01 syndaemon
21095 cmcanul+  20   0  200184  15232   8332 S   0.0  0.2   0:00.07 gnome-twea+
21096 cmcanul+  20   0  323392  17904  14988 S   0.0  0.2   0:00.19 xfce4-powe+
21099 cmcanul+  20   0  530972  33580  27460 S   0.0  0.4   0:00.48 nm-applet
21106 cmcanul+  20   0  500716  23848  19940 S   0.0  0.3   0:00.49 alarm-cloc+
21107 cmcanul+  20   0  328308  16948  15228 S   0.0  0.2   0:00.04 polkit-gno+
21119 cmcanul+  20   0   22372   1148    984 S   0.0  0.0   0:00.02 syndaemon
21122 cmcanul+  20   0  274560   6328   5620 S   0.0  0.1   0:00.03 gvfsd
21127 cmcanul+  20   0  406860   7404   4840 S   0.0  0.1   0:00.01 gvfsd-fuse
21140 cmcanul+  20   0   61448   5680   4944 S   0.0  0.1   0:00.01 gconfd-2
21146 cmcanul+  20   0  338008   6052   5476 S   0.0  0.1   0:00.00 at-spi-bus+
21147 cmcanul+  20   0  334024  23228  19720 S   0.0  0.3   0:00.19 panel-1-wh+
21152 cmcanul+  20   0  323680  21336  18068 S   0.0  0.3   0:00.19 panel-8-pl+
21154 cmcanul+  20   0   42768   3480   3148 S   0.0  0.0   0:00.07 dbus-daemon
21163 cmcanul+  20   0  206868   4968   4492 S   0.0  0.1   0:00.22 at-spi2-re+
21173 cmcanul+  20   0  285348   9592   6468 S   0.0  0.1   0:00.04 gvfs-udisk+
21176 cmcanul+  20   0  520928  32320  24712 S   0.0  0.4   0:00.32 panel-13-i+
21178 cmcanul+  20   0  316836  17648  14908 S   0.0  0.2   0:00.12 panel-33-p+
21180 cmcanul+  20   0  403652  11116   8052 S   0.0  0.1   0:00.02 gvfs-afc-v+
21189 cmcanul+  20   0  271860   5944   5196 S   0.0  0.1   0:00.01 gvfs-gphot+
21194 cmcanul+  20   0  171668  18416  16280 S   0.0  0.2   0:00.10 panel-9-ac+
21197 cmcanul+  20   0  259532   4640   4232 S   0.0  0.1   0:00.01 gvfs-mtp-v+
21202 cmcanul+  20   0  257692   5484   4956 S   0.0  0.1   0:00.02 gvfs-goa-v+
21203 cmcanul+  20   0  311960  17068  14412 S   0.0  0.2   0:00.09 panel-19-t+
21209 cmcanul+  20   0  758636  31748  24892 S   0.0  0.4   0:00.08 goa-daemon
21216 cmcanul+  20   0  317120  21392  18036 S   0.0  0.3   0:00.16 panel-28-x+
21220 cmcanul+  20   0  356844   6588   5912 S   0.0  0.1   0:00.02 goa-identi+
21229 cmcanul+  20   0   45964   4288   3704 S   0.0  0.1   0:00.00 upstart
21231 cmcanul+  20   0  355700   8432   6708 S   0.0  0.1   0:00.05 indicator-+
21232 cmcanul+  20   0  738456  12128   9044 S   0.0  0.2   0:00.12 indicator-+
21238 cmcanul+  20   0  403152  12944  11464 S   0.0  0.2   0:00.03 indicator-+
21253 cmcanul+  20   0  350612   6208   5580 S   0.0  0.1   0:00.01 gvfsd-trash
21478 cmcanul+  20   0  179404   5772   4428 S   0.0  0.1   0:00.26 dconf-serv+
21885 root      20   0       0      0      0 S   0.0  0.0   0:00.68 kworker/0:1
23205 root      20   0       0      0      0 S   0.0  0.0   0:00.03 kworker/1:3
24370 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/2:1
25310 root      20   0       0      0      0 S   0.0  0.0   0:00.18 kworker/1:0
25319 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/3:0
25320 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/3:3
25321 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/3:4
25322 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/3:5
25323 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/3:6
25324 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/3:7
25325 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/3:8
25326 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/3:9
25327 root      20   0       0      0      0 S   0.0  0.0   0:00.20 kworker/3:+
26073 cmcanul+  20   0  619056  60848  36640 S   0.0  0.8   0:01.14 gedit
26351 root      20   0       0      0      0 S   0.0  0.0   0:00.00 kworker/u1+
26455 cmcanul+  20   0  137228   9404   8468 S   0.0  0.1   0:00.00 exo-helper+
26456 cmcanul+  20   0  386692  22908  19124 S   0.0  0.3   0:00.15 xfce4-term+
26460 cmcanul+  20   0   14872   1704   1556 S   0.0  0.0   0:00.00 gnome-pty-+
26461 cmcanul+  20   0   22708   5304   3352 S   0.0  0.1   0:00.04 bash
26480 cmcanul+  20   0   41800   3708   3164 R   0.0  0.0   0:00.00 top

```

```
cmcanulty@ubuntu1:~$ ps aux | grep pdftohtml | grep -v grep
cmcanul+ 24489 99.9  0.9 114700 76008 ?        R    08:29  10:29 pdftohtml -noframes -zoom 2.0 -wbt 20.0 -nomerge /home/cmcanulty/Documents/eBooks/alaskadayswithjo00youn.pdf /home/cmcanulty/.config/bookworm/books/alaskadayswithjo00youn.pdf/alaskadayswithjo00youn.pdf.html
cmcanulty@ubuntu1:~$ 

```

---

