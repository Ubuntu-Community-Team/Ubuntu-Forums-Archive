---
title: "OOM error help request"
date: 2020-12-07
forum: General Help
---

### Post by shag00 on 2020-12-07
I had an oom event last night which appears to be caused by mono. At the  time I had a number of apps open but idle. The oom occurred just before  2:00 am and the last job I started was at the preceding 9:00 pm which  would take somewhere around 50 minutes, so at 2:00 the PC should not  have been doing anything. I have 16GB of RAM and have not ever seen it  all used previously. Basically, I am asking if some one could review the following kernel log and tell me more information so I might take  further action to address it, for example is it mono issue of a ubuntu  issue etc.

```

Dec  7 23:00:36 scottubuntu kernel: [95909.590730] usb 3-2: SerialNumber: LGF800S2ce086f6
Dec  7 23:59:19 scottubuntu kernel: [99432.801583] audit: type=1400 audit(1607356759.667:29): apparmor="DENIED" operation="open" profile="/usr/sbin/cupsd" name="/proc/5987/attr/apparmor/current" pid=5987 comm="cupsd" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
Dec  8 00:00:27 scottubuntu kernel: [99500.878627] audit: type=1400 audit(1607356827.743:30): apparmor="DENIED" operation="capable" profile="/usr/sbin/cups-browsed" pid=61384 comm="cups-browsed" capability=23  capname="sys_nice"
Dec  8 01:56:31 scottubuntu kernel: [106464.880260] mono invoked oom-killer: gfp_mask=0x100cca(GFP_HIGHUSER_MOVABLE), order=0, oom_score_adj=0
Dec  8 01:56:31 scottubuntu kernel: [106464.880263] CPU: 14 PID: 25017 Comm: mono Tainted: P           OE     5.8.0-32-generic #34-Ubuntu
Dec  8 01:56:31 scottubuntu kernel: [106464.880263] Hardware name: Micro-Star International Co., Ltd. MS-7C35/MEG X570 ACE (MS-7C35), BIOS 1.C3 09/29/2020
Dec  8 01:56:31 scottubuntu kernel: [106464.880264] Call Trace:
Dec  8 01:56:31 scottubuntu kernel: [106464.880272]  show_stack+0x52/0x58
Dec  8 01:56:31 scottubuntu kernel: [106464.880274]  dump_stack+0x70/0x8d
Dec  8 01:56:31 scottubuntu kernel: [106464.880277]  dump_header+0x4f/0x1eb
Dec  8 01:56:31 scottubuntu kernel: [106464.880278]  oom_kill_process.cold+0xb/0x10
Dec  8 01:56:31 scottubuntu kernel: [106464.880280]  out_of_memory.part.0+0xbd/0x240
Dec  8 01:56:31 scottubuntu kernel: [106464.880281]  out_of_memory+0x41/0x80
Dec  8 01:56:31 scottubuntu kernel: [106464.880283]  __alloc_pages_slowpath.constprop.0+0xa11/0xae0
Dec  8 01:56:31 scottubuntu kernel: [106464.880285]  __alloc_pages_nodemask+0x2d5/0x300
Dec  8 01:56:31 scottubuntu kernel: [106464.880287]  alloc_pages_current+0x87/0x110
Dec  8 01:56:31 scottubuntu kernel: [106464.880289]  pagecache_get_page+0x158/0x380
Dec  8 01:56:31 scottubuntu kernel: [106464.880290]  ? __do_page_cache_readahead+0x35/0x40
Dec  8 01:56:31 scottubuntu kernel: [106464.880291]  filemap_fault+0x587/0x790
Dec  8 01:56:31 scottubuntu kernel: [106464.880293]  ext4_filemap_fault+0x32/0x46
Dec  8 01:56:31 scottubuntu kernel: [106464.880295]  __do_fault+0x3c/0xe0
Dec  8 01:56:31 scottubuntu kernel: [106464.880297]  do_fault+0xa0/0x200
Dec  8 01:56:31 scottubuntu kernel: [106464.880298]  handle_pte_fault+0x1e7/0x260
Dec  8 01:56:31 scottubuntu kernel: [106464.880299]  __handle_mm_fault+0x599/0x7c0
Dec  8 01:56:31 scottubuntu kernel: [106464.880300]  handle_mm_fault+0xc6/0x1f0
Dec  8 01:56:31 scottubuntu kernel: [106464.880303]  do_user_addr_fault+0x1e2/0x450
Dec  8 01:56:31 scottubuntu kernel: [106464.880305]  exc_page_fault+0x86/0x1a0
Dec  8 01:56:31 scottubuntu kernel: [106464.880307]  ? asm_exc_page_fault+0x8/0x30
Dec  8 01:56:31 scottubuntu kernel: [106464.880308]  asm_exc_page_fault+0x1e/0x30
Dec  8 01:56:31 scottubuntu kernel: [106464.880309] RIP: 0033:0x7fcd2c5d63f0
Dec  8 01:56:31 scottubuntu kernel: [106464.880313] Code: Unable to access opcode bytes at RIP 0x7fcd2c5d63c6.
Dec  8 01:56:31 scottubuntu kernel: [106464.880313] RSP: 002b:00007ffd4df27e28 EFLAGS: 00010206
Dec  8 01:56:31 scottubuntu kernel: [106464.880314] RAX: 0000564e51712b60 RBX: 0000000000000000 RCX: 0000564e513b6edd
Dec  8 01:56:31 scottubuntu kernel: [106464.880315] RDX: 0000000000000000 RSI: 0000564e5149ca4c RDI: 0000564e51738d70
Dec  8 01:56:31 scottubuntu kernel: [106464.880316] RBP: 0000564e51738d70 R08: 0000564e516055a0 R09: 0000000000000000
Dec  8 01:56:31 scottubuntu kernel: [106464.880316] R10: 00000000032b29a4 R11: 00007fcd2c5da370 R12: 00007fcd26110830
Dec  8 01:56:31 scottubuntu kernel: [106464.880317] R13: 00007fcd2603c7b0 R14: 0000564e51635d30 R15: 0000564e51738d70
Dec  8 01:56:31 scottubuntu kernel: [106464.880319] Mem-Info:
Dec  8 01:56:31 scottubuntu kernel: [106464.880322] active_anon:843374 inactive_anon:322563 isolated_anon:0
Dec  8 01:56:31 scottubuntu kernel: [106464.880322]  active_file:232 inactive_file:42 isolated_file:0
Dec  8 01:56:31 scottubuntu kernel: [106464.880322]  unevictable:8 dirty:5 writeback:0
Dec  8 01:56:31 scottubuntu kernel: [106464.880322]  slab_reclaimable:42814 slab_unreclaimable:245807
Dec  8 01:56:31 scottubuntu kernel: [106464.880322]  mapped:2555903 shmem:27009 pagetables:16114 bounce:0
Dec  8 01:56:31 scottubuntu kernel: [106464.880322]  free:32994 free_pcp:2073 free_cma:0
Dec  8 01:56:31 scottubuntu kernel: [106464.880325] Node 0 active_anon:3373496kB inactive_anon:1290252kB active_file:928kB inactive_file:168kB unevictable:32kB isolated(anon):0kB isolated(file):0kB mapped:10223612kB dirty:20kB writeback:0kB shmem:108036kB shmem_thp: 0kB shmem_pmdmapped: 0kB anon_thp: 0kB writeback_tmp:0kB all_unreclaimable? no
Dec  8 01:56:31 scottubuntu kernel: [106464.880325] Node 0 DMA free:13820kB min:64kB low:80kB high:96kB reserved_highatomic:0KB active_anon:0kB inactive_anon:0kB active_file:0kB inactive_file:0kB unevictable:0kB writepending:0kB present:15996kB managed:15900kB mlocked:0kB kernel_stack:0kB pagetables:0kB bounce:0kB free_pcp:0kB local_pcp:0kB free_cma:0kB
Dec  8 01:56:31 scottubuntu kernel: [106464.880328] lowmem_reserve[]: 0 3086 15806 15806 15806
Dec  8 01:56:31 scottubuntu kernel: [106464.880329] Node 0 DMA32 free:63948kB min:13184kB low:16480kB high:19776kB reserved_highatomic:2048KB active_anon:547056kB inactive_anon:156328kB active_file:176kB inactive_file:0kB unevictable:0kB writepending:4kB present:3324644kB managed:3324004kB mlocked:0kB kernel_stack:432kB pagetables:4728kB bounce:0kB free_pcp:2124kB local_pcp:352kB free_cma:0kB
Dec  8 01:56:31 scottubuntu kernel: [106464.880332] lowmem_reserve[]: 0 0 12719 12719 12719
Dec  8 01:56:31 scottubuntu kernel: [106464.880333] Node 0 Normal free:54712kB min:54332kB low:67912kB high:81492kB reserved_highatomic:2048KB active_anon:2826440kB inactive_anon:1133924kB active_file:944kB inactive_file:896kB unevictable:32kB writepending:0kB present:13356544kB managed:13033736kB mlocked:32kB kernel_stack:16544kB pagetables:59728kB bounce:0kB free_pcp:6080kB local_pcp:896kB free_cma:0kB
Dec  8 01:56:31 scottubuntu kernel: [106464.880335] lowmem_reserve[]: 0 0 0 0 0
Dec  8 01:56:31 scottubuntu kernel: [106464.880337] Node 0 DMA: 1*4kB (U) 1*8kB (U) 1*16kB (U) 1*32kB (U) 1*64kB (U) 1*128kB (U) 1*256kB (U) 0*512kB 1*1024kB (U) 2*2048kB (UM) 2*4096kB (M) = 13820kB
Dec  8 01:56:31 scottubuntu kernel: [106464.880342] Node 0 DMA32: 1528*4kB (UMEH) 1639*8kB (UMEH) 2253*16kB (UMEH) 236*32kB (UMEH) 12*64kB (EH) 5*128kB (UH) 2*256kB (H) 0*512kB 0*1024kB 0*2048kB 0*4096kB = 64744kB
Dec  8 01:56:31 scottubuntu kernel: [106464.880346] Node 0 Normal: 41*4kB (UEH) 13*8kB (UE) 2595*16kB (UEH) 357*32kB (UE) 6*64kB (H) 2*128kB (H) 0*256kB 0*512kB 0*1024kB 0*2048kB 0*4096kB = 53852kB
Dec  8 01:56:31 scottubuntu kernel: [106464.880353] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=1048576kB
Dec  8 01:56:31 scottubuntu kernel: [106464.880354] Node 0 hugepages_total=0 hugepages_free=0 hugepages_surp=0 hugepages_size=2048kB
Dec  8 01:56:31 scottubuntu kernel: [106464.880354] 62494 total pagecache pages
Dec  8 01:56:31 scottubuntu kernel: [106464.880356] 34904 pages in swap cache
Dec  8 01:56:31 scottubuntu kernel: [106464.880356] Swap cache stats: add 3854321, delete 3819454, find 975683/1672572
Dec  8 01:56:31 scottubuntu kernel: [106464.880357] Free swap  = 0kB
Dec  8 01:56:31 scottubuntu kernel: [106464.880357] Total swap = 2097148kB
Dec  8 01:56:31 scottubuntu kernel: [106464.880357] 4174296 pages RAM
Dec  8 01:56:31 scottubuntu kernel: [106464.880358] 0 pages HighMem/MovableOnly
Dec  8 01:56:31 scottubuntu kernel: [106464.880358] 80886 pages reserved
Dec  8 01:56:31 scottubuntu kernel: [106464.880358] 0 pages hwpoisoned
Dec  8 01:56:31 scottubuntu kernel: [106464.880359] Tasks state (memory values in pages):
Dec  8 01:56:31 scottubuntu kernel: [106464.880359] [  pid  ]   uid  tgid total_vm      rss pgtables_bytes swapents oom_score_adj name
Dec  8 01:56:31 scottubuntu kernel: [106464.880364] [    448]     0   448    17359      247   126976      158          -250 systemd-journal
Dec  8 01:56:31 scottubuntu kernel: [106464.880366] [    482]     0   482     6166      131    69632      710         -1000 systemd-udevd
Dec  8 01:56:31 scottubuntu kernel: [106464.880368] [    902]     0   902     3948      863    65536      745             0 mount.ntfs
Dec  8 01:56:31 scottubuntu kernel: [106464.880369] [    973]     0   973     2294      105    49152       20             0 mount.ntfs
Dec  8 01:56:31 scottubuntu kernel: [106464.880370] [    996]     0   996     2293      100    53248       27             0 mount.ntfs
Dec  8 01:56:31 scottubuntu kernel: [106464.880371] [   1012]     0  1012     3025      736    57344       88             0 mount.ntfs
Dec  8 01:56:31 scottubuntu kernel: [106464.880373] [   1040]   102  1040     6474      207    90112     1014             0 systemd-resolve
Dec  8 01:56:31 scottubuntu kernel: [106464.880374] [   1041]   100  1041    22852      140    86016      100             0 systemd-timesyn
Dec  8 01:56:31 scottubuntu kernel: [106464.880375] [   1043]     0  1043     2072       51    57344      731             0 haveged
Dec  8 01:56:31 scottubuntu kernel: [106464.880376] [   1051]     0  1051    60098      484    98304       85             0 accounts-daemon
Dec  8 01:56:31 scottubuntu kernel: [106464.880378] [   1052]     0  1052      632       18    49152        0             0 acpid
Dec  8 01:56:31 scottubuntu kernel: [106464.880379] [   1057]   115  1057     2375       98    61440       35             0 avahi-daemon
Dec  8 01:56:31 scottubuntu kernel: [106464.880380] [   1058]     0  1058     2346      101    49152       30             0 bluetoothd
Dec  8 01:56:31 scottubuntu kernel: [106464.880381] [   1063]     0  1063     2350       60    65536        8             0 cron
Dec  8 01:56:31 scottubuntu kernel: [106464.880383] [   1065]   103  1065     2697      530    57344       90          -900 dbus-daemon
Dec  8 01:56:31 scottubuntu kernel: [106464.880384] [   1067]     0  1067    65805      346   151552      365             0 NetworkManager
Dec  8 01:56:31 scottubuntu kernel: [106464.880385] [   1077]     0  1077    20720       53    61440       24             0 irqbalance
Dec  8 01:56:31 scottubuntu kernel: [106464.880386] [   1080]     0  1080     4763       24    57344        0             0 ecbd
Dec  8 01:56:31 scottubuntu kernel: [106464.880388] [   1088]     0  1088     8140        0   106496     1948             0 networkd-dispat
Dec  8 01:56:31 scottubuntu kernel: [106464.880389] [   1095]     0  1095    59040      459    90112      353             0 polkitd
Dec  8 01:56:31 scottubuntu kernel: [106464.880390] [   1100]   104  1100    55281       70    81920      258             0 rsyslogd
Dec  8 01:56:31 scottubuntu kernel: [106464.880391] [   1103]     0  1103     3017      198    57344      234             0 smartd
Dec  8 01:56:31 scottubuntu kernel: [106464.880392] [   1108]   124  1108     1293       37    57344        0             0 nvidia-persiste
Dec  8 01:56:31 scottubuntu kernel: [106464.880394] [   1110]     0  1110     4555      162    73728      119             0 systemd-logind
Dec  8 01:56:31 scottubuntu kernel: [106464.880395] [   1113]     0  1113   117286      995   143360      255             0 udisksd
Dec  8 01:56:31 scottubuntu kernel: [106464.880397] [   1114]     0  1114     3644      101    65536       47             0 wpa_supplicant
Dec  8 01:56:31 scottubuntu kernel: [106464.880398] [   1117]     0  1117      944       43    49152        1             0 atd
Dec  8 01:56:31 scottubuntu kernel: [106464.880399] [   1128]   115  1128     2306       35    61440       50             0 avahi-daemon
Dec  8 01:56:31 scottubuntu kernel: [106464.880400] [   1171]     0  1171    11766      145   131072      494             0 winbindd
Dec  8 01:56:31 scottubuntu kernel: [106464.880401] [   1183]     0  1183    78784      220   114688      233             0 ModemManager
Dec  8 01:56:31 scottubuntu kernel: [106464.880402] [   1184]   118  1184    62167      396   122880     1281             0 colord
Dec  8 01:56:31 scottubuntu kernel: [106464.880404] [   1198]     0  1198     3268      114    69632      100         -1000 sshd
Dec  8 01:56:31 scottubuntu kernel: [106464.880405] [   1237]     0  1237    11766      157   131072      491             0 winbindd
Dec  8 01:56:31 scottubuntu kernel: [106464.880406] [   1272]     0  1272    27627        0   110592     1933             0 unattended-upgr
Dec  8 01:56:31 scottubuntu kernel: [106464.880407] [   1274]     0  1274    34689       35   122880      315             0 sddm
Dec  8 01:56:31 scottubuntu kernel: [106464.880409] [   1348]  1000  1348     5342      308    77824      553             0 systemd
Dec  8 01:56:31 scottubuntu kernel: [106464.880410] [   1349]  1000  1349    42618      171   106496      787             0 (sd-pam)
Dec  8 01:56:31 scottubuntu kernel: [106464.880411] [   1358]  1000  1358   299157       62   307200      989             0 appimagelaunche
Dec  8 01:56:31 scottubuntu kernel: [106464.880412] [   1359]  1000  1359   101385      132   225280      957             0 appimagelaunche
Dec  8 01:56:31 scottubuntu kernel: [106464.880413] [   1360]  1000  1360    27177       30   102400      797             0 pipewire
Dec  8 01:56:31 scottubuntu kernel: [106464.880414] [   1363]  1000  1363   146582      387   196608     1928             0 tracker-miner-f
Dec  8 01:56:31 scottubuntu kernel: [106464.880416] [   1368]   111  1368    38449       55    65536        6             0 rtkit-daemon
Dec  8 01:56:31 scottubuntu kernel: [106464.880417] [   1369]  1000  1369     2300      321    57344       91             0 dbus-daemon
Dec  8 01:56:31 scottubuntu kernel: [106464.880418] [   1383]  1000  1383    59937       95    94208      146             0 gvfsd
Dec  8 01:56:31 scottubuntu kernel: [106464.880419] [   1384]  1000  1384     6769       45    81920      655             0 pipewire-media-
Dec  8 01:56:31 scottubuntu kernel: [106464.880420] [   1410]  1000  1410   199598      358   163840      210             0 gvfs-udisks2-vo
Dec  8 01:56:31 scottubuntu kernel: [106464.880421] [   1448]  1000  1448    58968        0    86016      213             0 gvfs-goa-volume
Dec  8 01:56:31 scottubuntu kernel: [106464.880422] [   1452]  1000  1452    78579        0   102400      282             0 gvfs-afc-volume
Dec  8 01:56:31 scottubuntu kernel: [106464.880423] [   1461]  1000  1461    59552       18    90112      235             0 gvfs-gphoto2-vo
Dec  8 01:56:31 scottubuntu kernel: [106464.880424] [   1481]  1000  1481    59077      118    94208      101             0 gvfs-mtp-volume
Dec  8 01:56:31 scottubuntu kernel: [106464.880425] [   1490]     0  1490    62500      284   106496      109             0 upowerd
Dec  8 01:56:31 scottubuntu kernel: [106464.880426] [   1779]  1000  1779 67198332    39093  2785280      718             0 baloo_file
Dec  8 01:56:31 scottubuntu kernel: [106464.880427] [   1805]  1000  1805    39021        0    69632      170             0 dconf-service
Dec  8 01:56:31 scottubuntu kernel: [106464.880428] [   1854]  1000  1854    76316       47    86016      134             0 at-spi-bus-laun
Dec  8 01:56:31 scottubuntu kernel: [106464.880429] [   1859]  1000  1859     2024       17    57344      120             0 dbus-daemon
Dec  8 01:56:31 scottubuntu kernel: [106464.880430] [   1986]  1000  1986    59230        0    90112      153             0 agent
Dec  8 01:56:31 scottubuntu kernel: [106464.880432] [   2333]   117  2333    62949      204   126976      252             0 whoopsie
Dec  8 01:56:31 scottubuntu kernel: [106464.880433] [   2340]   114  2340     3034       19    69632       92             0 kerneloops
Dec  8 01:56:31 scottubuntu kernel: [106464.880434] [   2342]   114  2342     3034      110    65536        0             0 kerneloops
Dec  8 01:56:31 scottubuntu kernel: [106464.880435] [   2394]  1000  2394    11348        0    81920      199             0 obexd
Dec  8 01:56:31 scottubuntu kernel: [106464.880437] [  17506]     0 17506    86421    33869   581632     8683             0 Xorg
Dec  8 01:56:31 scottubuntu kernel: [106464.880438] [  17511]  1000 17511   404899    50366  1216512    16613             0 plasmashell
Dec  8 01:56:31 scottubuntu kernel: [106464.880439] [  17760]     0 17760    14165        5   106496      374             0 sddm-helper
Dec  8 01:56:31 scottubuntu kernel: [106464.880441] [  17763]  1000 17763    60058      176    90112      117             0 gnome-keyring-d
Dec  8 01:56:31 scottubuntu kernel: [106464.880442] [  17769]  1000 17769    69296        0   241664     1131             0 kwalletd5
Dec  8 01:56:31 scottubuntu kernel: [106464.880443] [  17770]  1000 17770    33103        0   110592      257             0 startplasma-x11
Dec  8 01:56:31 scottubuntu kernel: [106464.880444] [  17897]  1000 17897     1509        8    45056      104             0 ssh-agent
Dec  8 01:56:31 scottubuntu kernel: [106464.880446] [  17984]  1000 17984      599        6    40960       16             0 start_kdeinit
Dec  8 01:56:31 scottubuntu kernel: [106464.880447] [  17985]  1000 17985    26030       53   180224      776             0 kdeinit5
Dec  8 01:56:31 scottubuntu kernel: [106464.880448] [  17987]  1000 17987    68784      168   229376      883             0 klauncher
Dec  8 01:56:31 scottubuntu kernel: [106464.880449] [  18002]  1000 18002   453972      539   700416    11913             0 kded5
Dec  8 01:56:31 scottubuntu kernel: [106464.880450] [  18006]  1000 18006  3360699  2588787 21831680    30779             0 kwin_x11
Dec  8 01:56:31 scottubuntu kernel: [106464.880451] [  18033]  1000 18033    69087      168   245760     1205             0 kglobalaccel5
Dec  8 01:56:31 scottubuntu kernel: [106464.880452] [  18035]  1000 18035   136862      707   253952      768             0 kactivitymanage
Dec  8 01:56:31 scottubuntu kernel: [106464.880454] [  18045]  1000 18045    72034     2371   270336      900             0 ksmserver
Dec  8 01:56:31 scottubuntu kernel: [106464.880455] [  18056]  1000 18056    58863       92   188416      451             0 xembedsniproxy
Dec  8 01:56:31 scottubuntu kernel: [106464.880456] [  18063]  1000 18063   106900       33   270336     1114             0 polkit-kde-auth
Dec  8 01:56:31 scottubuntu kernel: [106464.880457] [  18067]  1000 18067    70272       37   253952     1076             0 kaccess
Dec  8 01:56:31 scottubuntu kernel: [106464.880458] [  18082]  1000 18082    58547       10   176128      507             0 gmenudbusmenupr
Dec  8 01:56:31 scottubuntu kernel: [106464.880459] [  18084]  1000 18084    89229      421   258048     1029             0 kdeconnectd
Dec  8 01:56:31 scottubuntu kernel: [106464.880461] [  18091]  1000 18091   168728      106   339968     1409             0 DiscoverNotifie
Dec  8 01:56:31 scottubuntu kernel: [106464.880462] [  18093]  1000 18093   549263     1101   348160      662             0 pulseaudio
Dec  8 01:56:31 scottubuntu kernel: [106464.880463] [  18094]  1000 18094   155802     1665   385024     7129             0 psensor
Dec  8 01:56:31 scottubuntu kernel: [106464.880464] [  18118]  1000 18118  1153806   291979  4591616    15272             0 firefox
Dec  8 01:56:31 scottubuntu kernel: [106464.880465] [  18131]  1000 18131 67324189     3387   602112     5649             0 dolphin
Dec  8 01:56:31 scottubuntu kernel: [106464.880467] [  18149]  1000 18149    40936       14    81920      182             0 at-spi2-registr
Dec  8 01:56:31 scottubuntu kernel: [106464.880467] [  18168]  1000 18168 67325290     4800   774144     5086             0 dolphin
Dec  8 01:56:31 scottubuntu kernel: [106464.880469] [  18202]  1000 18202    60873        0    98304      293             0 gsettings-helpe
Dec  8 01:56:31 scottubuntu kernel: [106464.880470] [  18210]  1000 18210     1917        0    53248      100             0 xsettingsd
Dec  8 01:56:31 scottubuntu kernel: [106464.880471] [  18232]  1000 18232   151828     2010   593920     5809             0 ksysguard
Dec  8 01:56:31 scottubuntu kernel: [106464.880472] [  18249]  1000 18249   711450    24287  1544192     4777             0 Web Content
Dec  8 01:56:31 scottubuntu kernel: [106464.880473] [  18266]  1000 18266    69043       97   249856     1013             0 kiod5
Dec  8 01:56:31 scottubuntu kernel: [106464.880475] [  18269]  1000 18269    56615       34   159744      478             0 kscreen_backend
Dec  8 01:56:31 scottubuntu kernel: [106464.880476] [  18344]  1000 18344   810668   142917  3055616    13637             0 WebExtensions
Dec  8 01:56:31 scottubuntu kernel: [106464.880477] [  18354]  1000 18354     1116       83    49152       45             0 ksysguardd
Dec  8 01:56:31 scottubuntu kernel: [106464.880478] [  18429]  1000 18429    59230        0    90112      153             0 agent
Dec  8 01:56:31 scottubuntu kernel: [106464.880479] [  18437]  1000 18437   703301     7606  1290240    10409             0 skypeforlinux
Dec  8 01:56:31 scottubuntu kernel: [106464.880480] [  18441]  1000 18441   101065      208   249856      773             0 org_kde_powerde
Dec  8 01:56:31 scottubuntu kernel: [106464.880481] [  18484]  1000 18484    48735        0   303104     1678             0 skypeforlinux
Dec  8 01:56:31 scottubuntu kernel: [106464.880483] [  18492]  1000 18492    48735        0   184320     1679             0 skypeforlinux
Dec  8 01:56:31 scottubuntu kernel: [106464.880484] [  18510]  1000 18510   640702    16642  1056768     3727             0 Privileged Cont
Dec  8 01:56:31 scottubuntu kernel: [106464.880485] [  18604]  1000 18604   208168     4757   679936    18749             0 skypeforlinux
Dec  8 01:56:31 scottubuntu kernel: [106464.880486] [  18605]  1000 18605   197081     3688   421888     1886             0 skypeforlinux
Dec  8 01:56:31 scottubuntu kernel: [106464.880487] [  18621]  1000 18621  1234390    28480  4784128     7663             0 skypeforlinux
Dec  8 01:56:31 scottubuntu kernel: [106464.880488] [  18622]  1000 18622    76440      672   274432     3176             0 skypeforlinux
Dec  8 01:56:31 scottubuntu kernel: [106464.880490] [  18630]  1000 18630    46321      258   282624     1601             0 RDD Process
Dec  8 01:56:31 scottubuntu kernel: [106464.880491] [  18717]  1000 18717    59980        0   102400      202             0 gnome-keyring-d
Dec  8 01:56:31 scottubuntu kernel: [106464.880492] [  18849]  1000 18849    26066       68   180224      758             0 file.so
Dec  8 01:56:31 scottubuntu kernel: [106464.880493] [  19215]  1000 19215   145483     3604   434176     2360             0 mkvtoolnix-gui
Dec  8 01:56:31 scottubuntu kernel: [106464.880494] [  21913]  1000 21913   142473      902   413696     1660             0 AppRun
Dec  8 01:56:31 scottubuntu kernel: [106464.880495] [  21946]  1000 21946     3082      209    57344       25             0 0001.AppImage
Dec  8 01:56:31 scottubuntu kernel: [106464.880496] [  23211]  1000 23211     2919      256    61440     1928             0 wineserver64
Dec  8 01:56:31 scottubuntu kernel: [106464.880498] [  23217]  1000 23217   659355        2   131072     1296             0 services.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880499] [  23220]  1000 23220   662069       82   147456     2312             0 winedevice.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880500] [  23228]  1000 23228   658606        2   110592     1144             0 plugplay.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880501] [  23233]  1000 23233   663956        5   163840     2126             0 winedevice.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880502] [  23235]  1000 23235   665329      215   159744     2936             0 explorer.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880503] [  23245]  1000 23245   658915        0   122880     1300             0 svchost.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880505] [  23252]  1000 23252   764298    25123   892928    23400             0 WaveLab.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880506] [  23307]  1000 23307    85085      271   376832     2695             0 konsole
Dec  8 01:56:31 scottubuntu kernel: [106464.880507] [  23310]  1000 23310     2370        1    57344       59             0 bash
Dec  8 01:56:31 scottubuntu kernel: [106464.880508] [  23312]  1000 23312   663500        0   135168     2243             0 cmd
Dec  8 01:56:31 scottubuntu kernel: [106464.880509] [  23318]  1000 23318     3083      235    69632     2122             0 wineserver64
Dec  8 01:56:31 scottubuntu kernel: [106464.880510] [  23319]  1000 23319     2881        7    61440     2130             0 wineserver64
Dec  8 01:56:31 scottubuntu kernel: [106464.880511] [  23330]  1000 23330   659371        2   131072     1300             0 services.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880512] [  23331]  1000 23331   659355        2   126976     1297             0 services.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880513] [  23335]  1000 23335   661563        2   139264     2126             0 jqs.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880514] [  23337]  1000 23337   661764       57   139264     1903             0 winedevice.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880515] [  23345]  1000 23345   665345      226   163840     2941             0 explorer.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880517] [  23347]  1000 23347   665401       68   163840     3123             0 explorer.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880518] [  23355]  1000 23355   661764       62   139264     1882             0 winedevice.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880519] [  23362]  1000 23362   658590        2   110592     1145             0 plugplay.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880520] [  23367]  1000 23367   663956        5   159744     2126             0 winedevice.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880521] [  23377]  1000 23377   658606        2   114688     1145             0 plugplay.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880522] [  23385]  1000 23385   663956        5   163840     2121             0 winedevice.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880523] [  23390]  1000 23390   658915        0   122880     1300             0 svchost.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880524] [  23397]  1000 23397   658899        0   122880     1299             0 svchost.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880525] [  23402]  1000 23402   664920      632   225280     2237             0 DtsJobQueue.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880526] [  23404]  1000 23404   764095    10379   483328     7298             0 java
Dec  8 01:56:31 scottubuntu kernel: [106464.880527] [  25016]  1000 25016      649        0    40960       23             0 sh
Dec  8 01:56:31 scottubuntu kernel: [106464.880529] [  25017]  1000 25017   716090   274460  4345856   207577             0 mono
Dec  8 01:56:31 scottubuntu kernel: [106464.880530] [  40699]  1000 40699    40649        0    81920      235             0 gvfsd-metadata
Dec  8 01:56:31 scottubuntu kernel: [106464.880531] [  41089]  1000 41089   631676    11005   843776     7222             0 Web Content
Dec  8 01:56:31 scottubuntu kernel: [106464.880532] [  43443]  1000 43443    85081     1233   376832     1953             0 konsole
Dec  8 01:56:31 scottubuntu kernel: [106464.880533] [  43446]  1000 43446   663590      216   135168     2051             0 cmd
Dec  8 01:56:31 scottubuntu kernel: [106464.880534] [  43450]  1000 43450     2532     1749    61440       50             0 wineserver64
Dec  8 01:56:31 scottubuntu kernel: [106464.880535] [  43456]  1000 43456   659355        2   122880     1291             0 services.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880536] [  43459]  1000 43459   658606        2   106496     1144             0 plugplay.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880537] [  43466]  1000 43466   663956        6   163840     2122             0 winedevice.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880538] [  43472]  1000 43472   665416       94   163840     3095             0 explorer.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880539] [  43475]  1000 43475   661733      117   143360     1822             0 winedevice.exe
Dec  8 01:56:31 scottubuntu kernel: [106464.880540] [  43783]  1000 43783    52072      277   241664     1077             0 smb.so
Dec  8 01:56:31 scottubuntu kernel: [106464.880541] [  57326]  1000 57326      649       19    45056        0             0 sh
Dec  8 01:56:31 scottubuntu kernel: [106464.880542] [  57327]  1000 57327   143892    31596   585728        0             0 mono
Dec  8 01:56:31 scottubuntu kernel: [106464.880543] [  59191]  1000 59191    26120      238   180224      591             0 file.so
Dec  8 01:56:31 scottubuntu kernel: [106464.880545] [  59854]  1000 59854   597295     4055   503808        0             0 Web Content
Dec  8 01:56:31 scottubuntu kernel: [106464.880546] [  60089]  1000 60089   216958    26183   667648        0             0 kscreenlocker_g
Dec  8 01:56:31 scottubuntu kernel: [106464.880547] [  60091]  1000 60091      719       34    40960        0             0 kcheckpass
Dec  8 01:56:31 scottubuntu kernel: [106464.880548] [  61383]     0 61383    36488      716   122880       60             0 cupsd
Dec  8 01:56:31 scottubuntu kernel: [106464.880549] [  61384]     0 61384    45243      387   118784       12             0 cups-browsed
Dec  8 01:56:31 scottubuntu kernel: [106464.880550] [  61397]     7 61397     4057      202    69632        0             0 dbus
Dec  8 01:56:31 scottubuntu kernel: [106464.880551] [  61418]     0 61418    99956     5700   221184      587             0 fwupd
Dec  8 01:56:31 scottubuntu kernel: [106464.880553] oom-kill:constraint=CONSTRAINT_NONE,nodemask=(null),cpuset=/,mems_allowed=0,global_oom,task_memcg=/user.slice/user-1000.slice/session-27.scope,task=kwin_x11,pid=18006,uid=1000
Dec  8 01:56:31 scottubuntu kernel: [106464.880580] Out of memory: Killed process 18006 (kwin_x11) total-vm:13442796kB, anon-rss:375524kB, file-rss:9979584kB, shmem-rss:40kB, UID:1000 pgtables:21320kB oom_score_adj:0
Dec  8 01:56:31 scottubuntu kernel: [106464.912105] oom_reaper: reaped process 18006 (kwin_x11), now anon-rss:0kB, file-rss:9981796kB, shmem-rss:40kB


```

---

### Post by CatKiller on 2020-12-07
As far as I can see (although I don't have experience of reading those things) it wasn't necessarily mono that caused the problem, but rather that mono was the process that couldn't be allocated memory, which is what triggered the OOM killer. It does look to me like baloo (KDE's file indexer) was using a large chunk of memory at the time, and does run when the machine is idle, so that might be something to look at. It's disabled on my machine since it was generally irritating.

---

### Post by shag00 on 2020-12-08
I noticed that Baloo was using a lot of memory as well, thanks.

---

