---
title: "light-locker doesn't run on xubuntu 16.10"
date: 2017-02-20
forum: General Help
---

### Post by mastupristi on 2017-02-20
Hi,
I have a problem with light-locker. It is not running but if I try to run it:
```
max@Anakin:~$ light-locker --debug
[gs_debug_init] gs-debug.c:106 (22:24:17):	 Debugging enabled
[main] light-locker.c:142 (22:24:17):	 initializing light-locker 1.7.0
[main] light-locker.c:144 (22:24:17):	 lock after screensaver 0
[main] light-locker.c:145 (22:24:17):	 late locking 0
[main] light-locker.c:146 (22:24:17):	 lock on suspend 1
[main] light-locker.c:147 (22:24:17):	 lock on lid 0
[main] light-locker.c:148 (22:24:17):	 idle hint 0
[init_session_id] gs-listener-dbus.c:2180 (22:24:17):	 Got session-id: /org/freedesktop/login1/session/c2
[init_session_id] gs-listener-dbus.c:2185 (22:24:17):	 Got sd-session-id: c2
[init_seat_path] gs-listener-dbus.c:2262 (22:24:17):	 Got seat: /org/freedesktop/DisplayManager/Seat0
[gs_listener_delay_suspend] gs-listener-dbus.c:449 (22:24:17):	 Delay suspend

** (light-locker:11728): WARNING **: screensaver already running in this session

```

but no screensaver is runng:
```
max@Anakin:~$ ps auxf
USER       PID %CPU %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
root         2  0.0  0.0      0     0 ?        S    21:20   0:00 [kthreadd]
root         3  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [ksoftirqd/0]
root         5  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/0:0H]
root         7  0.0  0.0      0     0 ?        S    21:20   0:02  \_ [rcu_sched]
root         8  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [rcu_bh]
root         9  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [migration/0]
root        10  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [lru-add-drain]
root        11  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [watchdog/0]
root        12  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [cpuhp/0]
root        13  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [cpuhp/1]
root        14  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [watchdog/1]
root        15  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [migration/1]
root        16  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [ksoftirqd/1]
root        18  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/1:0H]
root        19  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [cpuhp/2]
root        20  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [watchdog/2]
root        21  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [migration/2]
root        22  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [ksoftirqd/2]
root        24  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/2:0H]
root        25  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [cpuhp/3]
root        26  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [watchdog/3]
root        27  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [migration/3]
root        28  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [ksoftirqd/3]
root        30  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/3:0H]
root        31  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [cpuhp/4]
root        32  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [watchdog/4]
root        33  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [migration/4]
root        34  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [ksoftirqd/4]
root        35  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kworker/4:0]
root        36  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/4:0H]
root        37  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [cpuhp/5]
root        38  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [watchdog/5]
root        39  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [migration/5]
root        40  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [ksoftirqd/5]
root        42  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/5:0H]
root        43  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [cpuhp/6]
root        44  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [watchdog/6]
root        45  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [migration/6]
root        46  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [ksoftirqd/6]
root        48  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/6:0H]
root        49  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [cpuhp/7]
root        50  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [watchdog/7]
root        51  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [migration/7]
root        52  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [ksoftirqd/7]
root        54  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/7:0H]
root        55  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [cpuhp/8]
root        56  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [watchdog/8]
root        57  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [migration/8]
root        58  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [ksoftirqd/8]
root        60  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/8:0H]
root        61  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [cpuhp/9]
root        62  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [watchdog/9]
root        63  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [migration/9]
root        64  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [ksoftirqd/9]
root        65  0.0  0.0      0     0 ?        R    21:20   0:00  \_ [kworker/9:0]
root        66  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/9:0H]
root        67  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [cpuhp/10]
root        68  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [watchdog/10]
root        69  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [migration/10]
root        70  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [ksoftirqd/10]
root        71  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kworker/10:0]
root        72  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/10:0H]
root        73  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [cpuhp/11]
root        74  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [watchdog/11]
root        75  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [migration/11]
root        76  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [ksoftirqd/11]
root        78  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/11:0H]
root        79  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kdevtmpfs]
root        80  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [netns]
root        81  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [khungtaskd]
root        82  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [oom_reaper]
root        83  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [writeback]
root        84  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kcompactd0]
root        85  0.0  0.0      0     0 ?        SN   21:20   0:00  \_ [ksmd]
root        86  0.0  0.0      0     0 ?        SN   21:20   0:00  \_ [khugepaged]
root        87  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [crypto]
root        88  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kintegrityd]
root        89  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root        90  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kblockd]
root        91  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [ata_sff]
root        92  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [md]
root        93  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [devfreq_wq]
root        94  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [watchdogd]
root        96  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kworker/0:1]
root        97  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kworker/6:1]
root        99  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kswapd0]
root       100  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [vmstat]
root       101  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [ecryptfs-kthrea]
root       140  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kthrotld]
root       141  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [acpi_thermal_pm]
root       142  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       143  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       144  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       145  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       146  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       147  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       148  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       149  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       150  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       151  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       152  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       153  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       154  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       155  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       156  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       157  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       158  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       159  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       160  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       161  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       162  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       163  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       164  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       165  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       166  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [scsi_eh_0]
root       167  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [scsi_tmf_0]
root       168  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [scsi_eh_1]
root       169  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [scsi_tmf_1]
root       171  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [scsi_eh_2]
root       172  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [scsi_tmf_2]
root       173  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [scsi_eh_3]
root       174  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [scsi_tmf_3]
root       181  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [ipv6_addrconf]
root       182  0.0  0.0      0     0 ?        S    21:20   0:01  \_ [kworker/0:2]
root       203  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [deferwq]
root       204  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [charger_manager]
root       206  0.0  0.0      0     0 ?        S    21:20   0:01  \_ [kworker/3:1]
root       208  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kworker/2:1]
root       209  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kworker/8:1]
root       211  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kworker/1:1]
root       214  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       215  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kworker/8:2]
root       216  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kworker/5:1]
root       217  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       218  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       219  0.0  0.0      0     0 ?        S    21:20   0:01  \_ [kworker/7:1]
root       220  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/5:1H]
root       221  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       282  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [firewire]
root       283  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [firewire_ohci]
root       286  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [scsi_eh_4]
root       287  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [scsi_tmf_4]
root       288  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [scsi_eh_5]
root       289  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [scsi_tmf_5]
root       291  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [scsi_eh_6]
root       292  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [scsi_tmf_6]
root       293  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [scsi_eh_7]
root       294  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [scsi_tmf_7]
root       295  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [scsi_eh_8]
root       296  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [scsi_tmf_8]
root       297  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [scsi_eh_9]
root       298  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [scsi_tmf_9]
root       299  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [scsi_eh_10]
root       300  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [scsi_tmf_10]
root       301  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [scsi_eh_11]
root       302  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [scsi_tmf_11]
root       308  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kpsmoused]
root       322  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kworker/3:2]
root       323  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/8:1H]
root       324  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/6:1H]
root       327  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/10:1H]
root       328  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/0:1H]
root       329  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/1:1H]
root       330  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kworker/10:1]
root       331  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [bioset]
root       353  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [jbd2/sdc4-8]
root       354  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [ext4-rsv-conver]
root       389  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kauditd]
root       410  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [rpciod]
root       411  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [xprtiod]
root       451  0.0  0.0      0     0 ?        S    21:20   0:01  \_ [kworker/4:2]
root       456  0.0  0.0      0     0 ?        S    21:20   0:01  \_ [kworker/5:2]
root       497  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/7:1H]
root       508  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [edac-poller]
root       517  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/3:1H]
root       523  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/11:1H]
root       553  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [kworker/11:2]
root       726  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kvm-irqfd-clean]
root       859  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [UVM global queu]
root       860  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [UVM Tools Event]
root       975  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/2:1H]
root      1021  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [kworker/9:1H]
root      1031  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [jbd2/sdc5-8]
root      1032  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [ext4-rsv-conver]
root      1038  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [jbd2/sdc2-8]
root      1039  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [ext4-rsv-conver]
root      1040  0.0  0.0      0     0 ?        S    21:20   0:00  \_ [jbd2/sdc1-8]
root      1041  0.0  0.0      0     0 ?        S<   21:20   0:00  \_ [ext4-rsv-conver]
root      1384  0.0  0.0      0     0 ?        S<   21:21   0:00  \_ [kworker/4:1H]
root      1450  0.0  0.0      0     0 ?        S<   21:21   0:00  \_ [nfsd4_callbacks]
root      1451  0.0  0.0      0     0 ?        S    21:21   0:00  \_ [lockd]
root      1453  0.0  0.0      0     0 ?        S    21:21   0:00  \_ [nfsd]
root      1454  0.0  0.0      0     0 ?        S    21:21   0:00  \_ [nfsd]
root      1455  0.0  0.0      0     0 ?        S    21:21   0:00  \_ [nfsd]
root      1456  0.0  0.0      0     0 ?        S    21:21   0:00  \_ [nfsd]
root      1457  0.0  0.0      0     0 ?        S    21:21   0:00  \_ [nfsd]
root      1458  0.0  0.0      0     0 ?        S    21:21   0:00  \_ [nfsd]
root      1459  0.0  0.0      0     0 ?        S    21:21   0:00  \_ [nfsd]
root      1460  0.0  0.0      0     0 ?        S    21:21   0:00  \_ [nfsd]
root      1493  0.0  0.0      0     0 ?        S    21:21   0:00  \_ [kworker/9:2]
root      2086  0.0  0.0      0     0 ?        S    21:21   0:00  \_ [kworker/6:2]
root      5281  0.0  0.0      0     0 ?        S<   21:22   0:00  \_ [iprt-VBoxWQueue]
root      5285  0.0  0.0      0     0 ?        S    21:22   0:00  \_ [iprt-VBoxTscThr]
root     10287  0.0  0.0      0     0 ?        S    21:27   0:01  \_ [kworker/1:0]
root     10561  0.0  0.0      0     0 ?        S    21:36   0:01  \_ [kworker/2:0]
root     11123  0.0  0.0      0     0 ?        S    22:01   0:00  \_ [kworker/11:1]
root     11551  0.0  0.0      0     0 ?        S    22:16   0:00  \_ [kworker/u32:0]
root     11946  0.0  0.0      0     0 ?        S    22:25   0:00  \_ [kworker/7:2]
root     12033  0.0  0.0      0     0 ?        S    22:28   0:00  \_ [kworker/u32:1]
root     12092  0.0  0.0      0     0 ?        S    22:33   0:00  \_ [kworker/u32:2]
root         1  0.0  0.0 203080  7484 ?        Ss   21:20   0:01 /sbin/init splash
root       395  0.0  0.0  44104  5928 ?        Ss   21:20   0:00 /lib/systemd/systemd-journald
root       433  0.0  0.0  46568  5440 ?        Ss   21:20   0:00 /lib/systemd/systemd-udevd
root      1086  0.0  0.0  47852  3280 ?        Ss   21:20   0:00 /sbin/rpcbind -f -w
root      1092  0.0  0.0  23524   208 ?        Ss   21:20   0:00 /usr/sbin/rpc.idmapd
root      1174  0.0  0.0 283168  6924 ?        Ssl  21:20   0:00 /usr/lib/accountsservice/accounts-daemon
message+  1178  0.0  0.0  45512  5468 ?        Ss   21:20   0:01 /usr/bin/dbus-daemon --system --address=systemd: --nofork --nopidfile --systemd-activation
root      1190  0.0  0.0  44412  4788 ?        Ss   21:20   0:00 /lib/systemd/systemd-logind
root      1192  0.0  0.1 207956 21540 ?        Ssl  21:20   0:00 /usr/lib/snapd/snapd
syslog    1193  0.0  0.0 256408  3184 ?        Ssl  21:20   0:00 /usr/sbin/rsyslogd -n
avahi     1196  0.0  0.0  45140  3548 ?        Ss   21:20   0:00 avahi-daemon: running [Anakin.local]
avahi     1256  0.0  0.0  45012   348 ?        S    21:21   0:00  \_ avahi-daemon: chroot helper
root      1202  0.0  0.0   4388  1280 ?        Ss   21:20   0:02 /usr/sbin/acpid
daemon    1204  0.0  0.0  28136  2212 ?        Ss   21:20   0:00 /usr/sbin/atd -f
whoopsie  1205  0.0  0.1 379604 12852 ?        Ssl  21:20   0:00 /usr/bin/whoopsie -f
root      1213  0.0  0.0  31112  2904 ?        Ss   21:20   0:00 /usr/sbin/cron -f
root      1214  0.0  0.0 346928 10096 ?        Ssl  21:20   0:00 /usr/sbin/ModemManager
root      1215  0.0  0.1 468584 19140 ?        Ssl  21:20   0:00 /usr/sbin/NetworkManager --no-daemon
nobody    1537  0.0  0.0  53156  4064 ?        S    21:21   0:00  \_ /usr/sbin/dnsmasq --no-resolv --keep-in-foreground --no-hosts --bind-interfaces --pid-
root      1216  0.0  0.0  98416 10324 ?        Ss   21:20   0:00 /usr/sbin/cupsd -l
root      1257  0.0  0.0 282360 12244 ?        Ssl  21:21   0:00 /usr/sbin/cups-browsed
root      1286  0.0  0.0 289816  9712 ?        Ssl  21:21   0:00 /usr/lib/policykit-1/polkitd --no-debug
root      1395  0.0  0.0  67824  5424 ?        Ss   21:21   0:00 /usr/sbin/sshd -D
systemd+  1396  0.0  0.0  47672  4956 ?        Ss   21:21   0:00 /lib/systemd/systemd-resolved
root      1402  0.0  0.0  37984   864 ?        Ss   21:21   0:00 /usr/sbin/rpc.mountd --manage-gids
root      1506  0.0  0.0 361672  6464 ?        SLsl 21:21   0:00 /usr/sbin/lightdm
root      1522  5.8  2.0 492132 249796 tty7    Ss+  21:21   4:27  \_ /usr/lib/xorg/Xorg -core :0 -seat seat0 -auth /var/run/lightdm/root/:0 -nolisten tcp v
root      2282  0.0  0.0 252852  7028 ?        Sl   21:21   0:00  \_ lightdm --session-child 13 20
max       5455  0.0  0.0  46740  4576 ?        Ss   21:23   0:00      \_ /sbin/upstart --user
max       5497  0.0  0.0  82428  5472 ?        S    21:23   0:01          \_ /usr/bin/xbrlapi -q
max       5547  0.0  0.0  33160   280 ?        S    21:23   0:00          \_ upstart-udev-bridge --daemon --user
max       5552  0.0  0.0   7292   728 ?        Ss   21:23   0:00          \_ sleep infinity
max       5564  0.0  0.0 160360  9780 ?        Ssl  21:23   0:00          \_ /usr/lib/x86_64-linux-gnu/hud/window-stack-bridge
max       5606  0.0  0.0  33056   320 ?        S    21:23   0:00          \_ upstart-dbus-bridge --daemon --session --user --bus-name session
max       5608  0.0  0.0  33056   324 ?        S    21:23   0:00          \_ upstart-dbus-bridge --daemon --system --user --bus-name system
max       5612  0.0  0.0  41548   412 ?        S    21:23   0:00          \_ upstart-file-bridge --daemon --user
max       5616  0.0  0.0 166912   672 ?        Ss   21:23   0:00          \_ gpg-agent --homedir /home/max/.gnupg --use-standard-socket --daemon
max       5653  0.0  0.0   4496  1556 ?        Ss   21:23   0:00          \_ /bin/sh /etc/xdg/xfce4/xinitrc -- /etc/X11/xinit/xserverrc
max       5663  0.0  0.1 416240 18760 ?        Sl   21:23   0:01          |   \_ xfce4-session
max       5677  0.2  0.2 418208 25756 ?        Sl   21:23   0:09          |       \_ xfwm4 --replace --display :0.0 --sm-client-id 28d85458e-cb85-4708-841c
max       5682  0.0  0.3 866916 38432 ?        Sl   21:23   0:04          |       \_ xfce4-panel --display :0.0 --sm-client-id 262c3303f-99f7-4652-bf5d-4fa
max       7533  0.2  0.1 397272 16264 ?        Sl   21:23   0:10          |       |   \_ /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 /usr/lib/x86_64-
max       7540  0.0  0.1 401788 16680 ?        Sl   21:23   0:00          |       |   \_ /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 /usr/lib/x86_64-
max       7541  0.0  0.2 492828 33708 ?        Sl   21:23   0:00          |       |   \_ /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-2.0 /usr/lib/x86_64-
max       7550  0.0  0.2 424836 28520 ?        Sl   21:23   0:00          |       |   \_ /usr/lib/x86_64-linux-gnu/xfce4/panel/wrapper-1.0 /usr/lib/x86_64-
max      10254  0.0  0.2 545288 35956 ?        Sl   21:27   0:01          |       |   \_ xfce4-settings-manager
max      11672  0.0  0.0  12532  2872 ?        S    22:22   0:00          |       |   |   \_ bash /usr/bin/light-locker-settings
max      11673  0.0  0.4 580928 52732 ?        Sl   22:22   0:00          |       |   |       \_ /usr/bin/python /usr/share/light-locker-settings/light-loc
max      10420  0.0  0.0   4496   776 ?        S    21:33   0:00          |       |   \_ /bin/sh /usr/bin/synaptic-pkexec
root     10421  0.0  1.1 685580 146392 ?       Sl   21:33   0:02          |       |   |   \_ /usr/sbin/synaptic
max      11026  0.5  0.7 1484616 95148 ?       Sl   22:01   0:11          |       |   \_ /usr/lib/virtualbox/VirtualBox
max       9625  0.0  0.4 747040 50232 ?        Sl   21:24   0:01          |       \_ xfdesktop --display :0.0 --sm-client-id 2a6916fa8-d1de-415c-81ed-2466f
max       9655  0.0  0.1 653768 17848 ?        Sl   21:24   0:00          |       \_ zeitgeist-datahub
max       9656  0.0  0.2 246416 31400 ?        Sl   21:24   0:00          |       \_ /usr/bin/python3 /usr/share/system-config-printer/applet.py
max       9657  0.0  0.2 514356 25432 ?        Sl   21:24   0:00          |       \_ update-notifier
max       9662  0.0  0.2 539300 33496 ?        Sl   21:24   0:00          |       \_ nm-applet
max       9688  0.0  0.4 642192 54288 ?        Sl   21:24   0:00          |       \_ /usr/bin/python3 /usr/bin/blueman-applet
max       9692  0.0  0.2 473512 33668 ?        Sl   21:24   0:00          |       \_ /usr/lib/policykit-1-gnome/polkit-gnome-authentication-agent-1
max       9700  0.0  0.0 445272  7540 ?        Sl   21:24   0:00          |       \_ /usr/lib/x86_64-linux-gnu/deja-dup/deja-dup-monitor
max       5701  0.0  0.1 461392 19148 ?        Ssl  21:23   0:00          \_ xfsettingsd --display :0.0 --sm-client-id 2b3f450f4-810e-445a-82c5-d2dea167ec8
max       8257  0.0  0.0  46496  4364 ?        S    21:23   0:00          \_ upstart --user --startup-event indicator-services-start
max       8267  0.0  0.0 363044  8476 ?        Ssl  21:23   0:00          |   \_ /usr/lib/x86_64-linux-gnu/indicator-messages/indicator-messages-service
max       8268  0.0  0.0 351180  5924 ?        Ssl  21:23   0:00          |   \_ /usr/lib/x86_64-linux-gnu/indicator-bluetooth/indicator-bluetooth-service
max       8273  0.0  0.0 571768  6636 ?        Ssl  21:23   0:00          |   \_ /usr/lib/x86_64-linux-gnu/indicator-power/indicator-power-service
max       8276  0.0  0.2 1114892 34580 ?       Ssl  21:23   0:00          |   \_ /usr/lib/x86_64-linux-gnu/indicator-datetime/indicator-datetime-service
max       8277  0.0  0.2 704828 31412 ?        Ssl  21:23   0:00          |   \_ /usr/lib/x86_64-linux-gnu/indicator-keyboard/indicator-keyboard-service --
max       8280  0.0  0.0 819292 11632 ?        Ssl  21:23   0:00          |   \_ /usr/lib/x86_64-linux-gnu/indicator-sound/indicator-sound-service
max       8281  0.0  0.0 896964  7224 ?        Ssl  21:23   0:00          |   \_ /usr/lib/x86_64-linux-gnu/indicator-session/indicator-session-service
max       8307  0.0  0.1 407468 13060 ?        Ssl  21:23   0:00          |   \_ /usr/lib/x86_64-linux-gnu/indicator-application/indicator-application-serv
max       8346  0.0  0.1 772024 13012 ?        S<l  21:23   0:00          |   \_ /usr/bin/pulseaudio --start --log-target=syslog
max       9647  0.0  0.1 417564 19328 ?        Ssl  21:24   0:00          \_ xfce4-power-manager --restart --sm-client-id 20c72cc6f-9b18-4696-8255-821e9df0
max       9684  0.0  0.1 538560 15496 ?        Ssl  21:24   0:00          \_ xfce4-volumed
max       9706  0.0  0.1 403296 15184 ?        Ssl  21:24   0:00          \_ xfce4-power-manager
max       9824  0.1  1.5 5243776 191444 ?      Ssl  21:24   0:08          \_ /home/max/.dropbox-dist/dropbox-lnx.x86_64-19.4.13/dropbox
max      10141  9.9  7.8 2200488 961432 ?      Rl   21:26   7:01          \_ /usr/lib/firefox/firefox
root     10437  0.0  0.0  43952  2460 ?        S    21:33   0:00          \_ dbus-launch --autolaunch=8370cff141113a12bb5f53fb52c598b8 --binary-syntax --cl
root     10438  0.0  0.0  43000  2548 ?        Ss   21:33   0:00          \_ /usr/bin/dbus-daemon --fork --print-pid 5 --print-address 7 --session
max      10476  0.0  0.2 500360 33016 ?        Sl   21:34   0:02          \_ /usr/bin/xfce4-terminal
max      10481  0.0  0.0  14860  1812 ?        S    21:34   0:00          |   \_ gnome-pty-helper
max      10482  0.0  0.0  23428  6024 pts/1    Ss   21:34   0:00          |   \_ bash
max      12116  0.0  0.0  38136  3836 pts/1    R+   22:37   0:00          |   |   \_ ps auxf
max      11306  0.0  0.0  23392  5976 pts/12   Ss   22:06   0:00          |   \_ bash
max      11403  0.0  0.3 547304 37348 pts/12   Sl+  22:11   0:01          |   |   \_ scite gs-listener-dbus.c
max      11500  0.0  0.0  23372  5972 pts/13   Ss+  22:14   0:00          |   \_ bash
max      11045  0.3  0.1 166836 12636 ?        S    22:01   0:06          \_ /usr/lib/virtualbox/VBoxXPCOMIPCD
max      11050  0.8  0.2 827500 25920 ?        Sl   22:01   0:18          \_ /usr/lib/virtualbox/VBoxSVC --auto-shutdown
max      11100 13.0  8.5 4820812 1055880 ?     Sl   22:01   4:34              \_ /usr/lib/virtualbox/VirtualBox --comment kinetis --startvm f179c6e0-ad42-4
max      11142  0.0  0.1 160880 12944 ?        S    22:01   0:00              \_ /usr/lib/virtualbox/VBoxNetDHCP --ip-address 192.168.56.100 --lower-ip 192
root      1508  0.0  0.0  19640  2304 ?        Ss   21:21   0:00 /usr/sbin/irqbalance --pid=/var/run/irqbalance.pid
colord    1511  0.0  0.1 311840 14568 ?        Ssl  21:21   0:00 /usr/lib/colord/colord
debian-+  1526  0.0  0.2  80744 36536 ?        Ss   21:21   0:01 /usr/bin/tor --defaults-torrc /usr/share/tor/tor-service-defaults-torrc -f /etc/tor/torrc 
nvidia-+  2031  0.0  0.0  17088  1664 ?        Ss   21:21   0:00 /usr/bin/nvidia-persistenced --user nvidia-persistenced --no-persistence-mode --verbose
dhcpd     2068  0.0  0.1  46836 14048 ?        Ss   21:21   0:00 dhcpd -user dhcpd -group dhcpd -f -4 -pf /run/dhcp-server/dhcpd.pid -cf /etc/dhcp/dhcpd.co
root      2085  0.0  0.0  16072  1808 tty1     Ss+  21:21   0:00 /sbin/agetty --noclear tty1 linux
root      2090  0.1  0.1 314620 14444 ?        Sl   21:21   0:07 /opt/teamviewer/tv_bin/teamviewerd -d
ntp       2210  0.0  0.0 107076  5112 ?        Ssl  21:21   0:00 /usr/sbin/ntpd -p /var/run/ntpd.pid -g -u 117:126
rtkit     2226  0.0  0.0 183764  2912 ?        SNsl 21:21   0:00 /usr/lib/rtkit/rtkit-daemon
max       5443  0.0  0.0  63016  6684 ?        Ss   21:23   0:00 /lib/systemd/systemd --user
max       5445  0.0  0.0 176300  2544 ?        S    21:23   0:00  \_ (sd-pam)
max       5471  0.0  0.0  44216  5056 ?        Ss   21:23   0:01  \_ /usr/bin/dbus-daemon --session --address=systemd: --nofork --nopidfile --systemd-activ
max       5618  0.0  0.2 433048 27928 ?        Ssl  21:23   0:01  \_ /usr/lib/x86_64-linux-gnu/bamf/bamfdaemon
max       5619  0.0  0.0 346948  6192 ?        Ssl  21:23   0:00  \_ /usr/lib/at-spi2-core/at-spi-bus-launcher
max       5624  0.0  0.0  43276  4212 ?        S    21:23   0:00  |   \_ /usr/bin/dbus-daemon --config-file=/usr/share/defaults/at-spi2/accessibility.conf 
max       5627  0.0  0.0 213968  5376 ?        Sl   21:23   0:00  \_ /usr/lib/at-spi2-core/at-spi2-registryd --use-gnome-session
max       5632  0.0  0.0 283680  6560 ?        Ssl  21:23   0:00  \_ /usr/lib/gvfs/gvfsd
max       5637  0.0  0.0 415744  5536 ?        Sl   21:23   0:00  \_ /usr/lib/gvfs/gvfsd-fuse /run/user/1000/gvfs -f -o big_writes
max       5672  0.0  0.0  54632  5000 ?        S    21:23   0:00  \_ /usr/lib/x86_64-linux-gnu/xfce4/xfconf/xfconfd
max       8325  0.0  0.1 417492 24228 ?        Sl   21:23   0:00  \_ /usr/bin/gnome-screensaver --no-daemon
max       8503  0.0  0.2 1247996 24880 ?       Ssl  21:23   0:00  \_ /usr/lib/evolution/evolution-source-registry
max       8784  0.0  0.2 773292 35688 ?        Sl   21:23   0:00  \_ /usr/lib/x86_64-linux-gnu/gnome-online-accounts/goa-daemon
max       9460  0.0  0.2 850744 33648 ?        Ssl  21:24   0:00  \_ /usr/lib/evolution/evolution-calendar-factory
max       9879  0.0  0.1 797564 23708 ?        Sl   21:24   0:00  |   \_ /usr/lib/evolution/evolution-calendar-factory-subprocess --factory contacts --bus-
max       9890  0.0  0.1 844052 20668 ?        Sl   21:24   0:00  |   \_ /usr/lib/evolution/evolution-calendar-factory-subprocess --factory local --bus-nam
max       9674  0.0  0.0 187688  5064 ?        Sl   21:24   0:00  \_ /usr/lib/dconf/dconf-service
max       9681  0.0  0.0   4496   768 ?        S    21:24   0:00  \_ /bin/sh -c /usr/lib/x86_64-linux-gnu/zeitgeist/zeitgeist-maybe-vacuum; /usr/bin/zeitge
max       9702  0.0  0.0 417688  6956 ?        Sl   21:24   0:00  |   \_ /usr/bin/zeitgeist-daemon
max       9732  0.0  0.0 292932  8652 ?        Ssl  21:24   0:00  \_ /usr/lib/gvfs/gvfs-udisks2-volume-monitor
max       9739  0.0  0.0 317808 10192 ?        Sl   21:24   0:00  \_ /usr/lib/x86_64-linux-gnu/zeitgeist-fts
max       9779  0.0  0.0 292196  8800 ?        Sl   21:24   0:00  \_ /usr/lib/x86_64-linux-gnu/gnome-online-accounts/goa-identity-service
max       9806  0.0  0.0 278820  5620 ?        Ssl  21:24   0:00  \_ /usr/lib/gvfs/gvfs-gphoto2-volume-monitor
max       9815  0.0  0.0 266620  5108 ?        Ssl  21:24   0:00  \_ /usr/lib/gvfs/gvfs-mtp-volume-monitor
max       9819  0.0  0.0 266620  5424 ?        Ssl  21:24   0:00  \_ /usr/lib/gvfs/gvfs-goa-volume-monitor
max       9836  0.0  0.1 432572 13388 ?        Ssl  21:24   0:00  \_ /usr/lib/telepathy/mission-control-5
max       9838  0.0  0.0 412920  9412 ?        Ssl  21:24   0:00  \_ /usr/lib/gvfs/gvfs-afc-volume-monitor
max       9853  0.0  0.0 360012  7540 ?        Sl   21:24   0:00  \_ /usr/lib/gvfs/gvfsd-trash --spawner :1.13 /org/gtk/gvfs/exec_spaw/0
max       9859  0.0  0.0 193412  6052 ?        Ssl  21:24   0:00  \_ /usr/lib/gvfs/gvfsd-metadata
max       9897  0.0  0.1 714716 22556 ?        Ssl  21:24   0:00  \_ /usr/lib/evolution/evolution-addressbook-factory
max       9913  0.0  0.1 787744 21532 ?        Sl   21:24   0:00  |   \_ /usr/lib/evolution/evolution-addressbook-factory-subprocess --factory local --bus-
max      10203  0.0  0.0  68628  5584 ?        S    21:26   0:00  \_ /usr/lib/x86_64-linux-gnu/gconf/gconfd-2
max       5452  0.0  0.0 214676  7772 ?        Sl   21:23   0:00 /usr/bin/gnome-keyring-daemon --daemonize --login
root      6503  0.0  0.0 354456 10308 ?        Ssl  21:23   0:00 /usr/lib/upower/upowerd
root      9762  0.0  0.0 375364  9664 ?        Ssl  21:24   0:01 /usr/lib/udisks2/udisksd --no-debug
uuidd     9969  0.0  0.0  28392  1472 ?        Ss   21:24   0:00 /usr/sbin/uuidd --socket-activation
lightdm  11760  0.0  0.0  62884  6596 ?        Ss   22:24   0:00 /lib/systemd/systemd --user
lightdm  11761  0.0  0.0 241836  2556 ?        S    22:24   0:00  \_ (sd-pam)
lightdm  11865  0.0  0.0 425096 10708 ?        S<l  22:24   0:00 /usr/bin/pulseaudio --start --log-target=syslog

```

so where am I wrong?

best regards
Max

---

