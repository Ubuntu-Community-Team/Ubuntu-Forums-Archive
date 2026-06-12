---
title: "Ubuntu going extremely slow! Please help ASAP!"
date: 2008-05-29
forum: General Help
---

### Post by lash9420 on 2008-05-29
The whole OS is going extremely slow. The only think I can think of would be uninstalling and reinstalling xserver-xgl. When I log in it also displays a black screen and an "X" for my mouse. Then loads normailly. FF goes extremely slow as does everything. Please help ASAP!

Thanks!

---

### Post by ibuclaw on 2008-05-29
Can you post the output of the command
```
ps -ely
```
And the command
```
swapon -s
```
Thanks...

[EDIT]
A few more questions...
What is your current window configuration? (ie: metacity/emerald? compiz-fusion enabled?)
Also, what hardware specs do you have?

Regards
Iain

---

### Post by lash9420 on 2008-05-29
I hope this is what you mean:

S   UID   PID  PPID  C PRI  NI   RSS    SZ WCHAN  TTY          TIME CMD
S     0     1     0  0  80   0   888  1005 -      ?        00:00:01 init
S     0     2     0  0  75  -5     0     0 kthrea ?        00:00:00 kthreadd
S     0     3     2  0 -40   -     0     0 migrat ?        00:00:00 migration/0
S     0     4     2  0  75  -5     0     0 ksofti ?        00:00:00 ksoftirqd/0
S     0     5     2  0 -40   -     0     0 watchd ?        00:00:00 watchdog/0
S     0     6     2  0 -40   -     0     0 migrat ?        00:00:00 migration/1
S     0     7     2  0  75  -5     0     0 ksofti ?        00:00:00 ksoftirqd/1
S     0     8     2  0 -40   -     0     0 watchd ?        00:00:00 watchdog/1
S     0     9     2  0  75  -5     0     0 worker ?        00:00:00 events/0
S     0    10     2  0  75  -5     0     0 worker ?        00:00:00 events/1
S     0    11     2  0  75  -5     0     0 worker ?        00:00:00 khelper
S     0    44     2  0  75  -5     0     0 worker ?        00:00:00 kblockd/0
S     0    45     2  0  75  -5     0     0 worker ?        00:00:00 kblockd/1
S     0    48     2  0  75  -5     0     0 worker ?        00:00:00 kacpid
S     0    49     2  0  75  -5     0     0 worker ?        00:00:00 kacpi_notify
S     0   117     2  0  75  -5     0     0 serio_ ?        00:00:00 kseriod
S     0   162     2  0  80   0     0     0 pdflus ?        00:00:00 pdflush
S     0   163     2  0  80   0     0     0 pdflus ?        00:00:00 pdflush
S     0   164     2  0  75  -5     0     0 kswapd ?        00:00:00 kswapd0
S     0   207     2  0  75  -5     0     0 worker ?        00:00:00 aio/0
S     0   208     2  0  75  -5     0     0 worker ?        00:00:00 aio/1
S     0  1460     2  0  75  -5     0     0 worker ?        00:00:00 ksuspend_usb
S     0  1463     2  0  75  -5     0     0 hub_th ?        00:00:00 khubd
S     0  1488     2  0  75  -5     0     0 worker ?        00:00:00 ata/0
S     0  1489     2  0  75  -5     0     0 worker ?        00:00:00 ata/1
S     0  1492     2  0  75  -5     0     0 worker ?        00:00:00 ata_aux
S     0  1996     2  0  75  -5     0     0 scsi_e ?        00:00:00 scsi_eh_0
S     0  1997     2  0  75  -5     0     0 scsi_e ?        00:00:00 scsi_eh_1
S     0  2242     2  0  75  -5     0     0 scsi_e ?        00:00:00 scsi_eh_2
S     0  2243     2  0  75  -5     0     0 scsi_e ?        00:00:00 scsi_eh_3
S     0  2459     1  5  80   0  1248  3773 fuse_d ?        00:00:11 mount.ntfs
S     0  2495     2  0  60 -20     0     0 loop_t ?        00:00:00 loop0
S     0  2498     2  0  75  -5     0     0 kjourn ?        00:00:00 kjournald
S     0  2595     2  0  75  -5     0     0 scsi_e ?        00:00:00 scsi_eh_4
S     0  2596     2  0  75  -5     0     0 -      ?        00:00:00 usb-storage
S     0  2598     2  0  75  -5     0     0 scsi_e ?        00:00:00 scsi_eh_5
S     0  2599     2  0  75  -5     0     0 -      ?        00:00:00 usb-storage
S     0  2601     2  0  75  -5     0     0 scsi_e ?        00:00:00 scsi_eh_6
S     0  2602     2  0  75  -5     0     0 usb_st ?        00:00:00 usb-storage
S     0  2714     1  0  76  -4  1296  4296 -      ?        00:00:00 udevd
S     0  3162     2  0  75  -5     0     0 worker ?        00:00:00 kpsmoused
S     0  4585     1  0  80   0   596   966 -      tty4     00:00:00 getty
S     0  4586     1  0  80   0   596   966 -      tty5     00:00:00 getty
S     0  4591     1  0  80   0   592   966 -      tty2     00:00:00 getty
S     0  4594     1  0  80   0   596   966 -      tty3     00:00:00 getty
S     0  4598     1  0  80   0   592   966 -      tty6     00:00:00 getty
S     0  4772     1  0  80   0  1752  3269 -      ?        00:00:00 acpid
S     0  4827     2  0  75  -5     0     0 worker ?        00:00:00 kondemand/0
S     0  4828     2  0  75  -5     0     0 worker ?        00:00:00 kondemand/1
S   102  4888     1  0  80   0   720  3074 -      ?        00:00:00 syslogd
S     0  4939     1  0  80   0   592  2033 syslog ?        00:00:00 dd
S   103  4941     1  0  80   0  2888  1536 pipe_w ?        00:00:00 klogd
S   108  4963     1  0  80   0  1504  5440 -      ?        00:00:00 dbus-daemon
S     0  4979     1  0  80   0  2256 13133 235134 ?        00:00:00 NetworkManag
S     0  4993     1  0  80   0  1408  7096 -      ?        00:00:00 NetworkManag
S     0  5006     1  0  80   0  1212  8798 -      ?        00:00:00 system-tools
S   109  5026     1  0  80   0  1496  7395 -      ?        00:00:00 avahi-daemon
S   109  5027  5026  0  80   0   508  7395 -      ?        00:00:00 avahi-daemon
S   112  5134     1  0  80   0  1060  6432 pause  ?        00:00:00 freshclam
S     0  5161     1  0  80   0  2492 18077 -      ?        00:00:00 cupsd
S     0  5235     1  0  80   0   960  1568 -      ?        00:00:00 dhcdbd
S   111  5254     1  0  80   0  4884 10062 -      ?        00:00:00 hald
S     0  5257     1  0  80   0  2532 10273 452821 ?        00:00:00 console-kit-
S     0  5258  5254  0  80   0  1356  5512 187708 ?        00:00:00 hald-runner
S   111  5337  5258  0  80   0   996  4168 -      ?        00:00:00 hald-addon-a
S     0  5344  5258  0  80   0  1284  6039 207712 ?        00:00:00 hald-addon-i
D     0  5360  5258  0  80   0  1276  6039 blk_ex ?        00:00:00 hald-addon-s
S     0  5362  5258  0  80   0  1268  6039 437111 ?        00:00:00 hald-addon-s
S     0  5365  5258  0  80   0  1280  6039 437111 ?        00:00:00 hald-addon-s
S     0  5367  5258  0  80   0  1276  6039 437111 ?        00:00:00 hald-addon-s
S     0  5369  5258  0  80   0  1280  6039 437111 ?        00:00:00 hald-addon-s
S     0  5371  5258  0  80   0  1276  6039 437111 ?        00:00:00 hald-addon-s
S     0  5374  5258  0  80   0  1272  6039 382263 ?        00:00:00 hald-addon-s
S     0  5377  5258  0  80   0  1280  6039 429493 ?        00:00:00 hald-addon-s
S     0  5424     1  0  80   0  1292  4440 175576 ?        00:00:00 hcid
S     0  5433     2  0  75  -5     0     0 worker ?        00:00:00 btaddconn
S     0  5434     2  0  75  -5     0     0 worker ?        00:00:00 btdelconn
S     0  5450  5424  0  80   0  1184  4395 191012 ?        00:00:00 bluetoothd-s
S     0  5451     2  0  70 -10     0     0 rfcomm ?        00:00:00 krfcommd
S     0  5469  5424  0  80   0  1392  4414 283038 ?        00:00:00 bluetoothd-s
S   101  5486  5235  0  80   0  1472  3776 -      ?        00:00:00 dhclient
S     0  5499     1  0  80   0  1908 29044 -      ?        00:00:00 gdm
S     0  5500  5499  0  80   0  3352 32229 -      ?        00:00:00 gdm
S     0  5506  5500  0  80   0  7420 19743 -      tty7     00:00:00 Xorg
S     1  5560     1  0  80   0   432  4107 -      ?        00:00:00 atd
S     0  5589     1  0  80   0   976  4654 -      ?        00:00:00 cron
S     0  5717     1  0  80   0   596   966 -      tty1     00:00:00 getty
S  1000  5782     1  0  80   0  5824 10935 -      ?        00:00:00 gconfd-2
S  1000  5784     1  0  80   0  2340 15511 -      ?        00:00:00 gnome-keyrin
S  1000  5786  5500  0  80   0  8932 48385 382338 ?        00:00:00 x-session-ma
S  1000  5878  5786  0  80   0   560   986 wait   ?        00:00:00 Xgl-lockfile
S  1000  5883  5878 22  80   0 71556 37295 -      ?        00:00:32 Xgl
S  1000  5894  5786  0  80   0  7924 53746 730144 ?        00:00:00 seahorse-age
S  1000  5905     1  0  80   0  1148  5330 -      ?        00:00:00 dbus-daemon
S  1000  5906  5786  0  80   0 26576 68694 923552 ?        00:00:00 gnome-settin
S  1000  5911  5906  0  80   0  6272 37051 429493 ?        00:00:00 pulseaudio
S  1000  5914  5911  0  80   0  2692 14459 359089 ?        00:00:00 gconf-helper
S  1000  5928     1  0  80   0  3036 33512 -      ?        00:00:00 gnome-screen
S  1000  5933  5786  0  80   0   620   986 wait   ?        00:00:00 compiz
S  1000  5935  5786  1  80   0 25908 94814 -      ?        00:00:01 gnome-panel
S  1000  5936  5786  0  80   0 28344 103638 844437 ?       00:00:00 nautilus
S  1000  5945     1  0  80   0  3740 37466 187144 ?        00:00:00 bonobo-activ
S  1000  5950  5933  1  80   0 22768 54352 188188 ?        00:00:02 compiz.real
S  1000  5955  5786  0  80   0 16564 52118 171798 ?        00:00:00 update-notif
S  1000  5960     1  0  80   0  2276 11193 639950 ?        00:00:00 gvfsd
S  1000  5962  5786  0  80   0 12264 88608 129511 ?        00:00:00 evolution-al
S  1000  5964  5786  0  80   0  6392 30450 -      ?        00:00:00 tracker-appl
S  1000  5970  5786  0  80   0 14852 49933 429493 ?        00:00:00 nm-applet
S  1000  5971     1  0  80   0  5288 46842 446387 ?        00:00:00 gnome-volume
S  1000  5972  5786  0  80   0 16408 48474 923385 ?        00:00:00 python
S  1000  5974     1  0  99  19 11004 35597 426456 ?        00:00:00 trackerd
S  1000  5976     1  0  80   0  8824 53306 426071 ?        00:00:00 gnome-power-
S  1000  5985     1  0  80   0  2224 15579 futex_ ?        00:00:00 gvfs-fuse-da
S  1000  5993     1  0  80   0 11760 71034 923385 ?        00:00:00 evolution-ex
S  1000  5996     1  0  80   0  2360 11193 459561 ?        00:00:00 gvfsd-burn
S  1000  6003     1  0  80   0  8064 75763 448713 ?        00:00:00 evolution-da
S  1000  6007     1  0  80   0 13036 51557 -      ?        00:00:00 trashapplet
S  1000  6009     1  0  80   0  2912 15887 -      ?        00:00:00 gvfsd-trash
S  1000  6023     1  0  80   0  2424 13891 343295 ?        00:00:00 gvfsd-cdda
S  1000  6024  5950  0  80   0   556   986 wait   ?        00:00:00 sh
S  1000  6025  6024  0  80   0   592   986 wait   ?        00:00:00 compiz-decor
S  1000  6027  6025  0  80   0 10868 35389 321071 ?        00:00:00 gtk-window-d
S  1000  6070     1  0  80   0 15852 52656 -      ?        00:00:00 fast-user-sw
S  1000  6073     1  0  80   0 18084 60495 730144 ?        00:00:00 mixer_applet
S  1000  6091     1 10  80   0 103312 133863 282396 ?      00:00:11 firefox
S  1000  6119  6091  0  80   0  8932 16656 923385 ?        00:00:00 npviewer.bin
R  1000  6155     1  3  80   0 24124 64650 -      ?        00:00:00 gnome-termin
S  1000  6157  6155  0  80   0   968  5893 -      ?        00:00:00 gnome-pty-he
S  1000  6158  6155  1  80   0  3496  5147 wait   pts/0    00:00:00 bash
R  1000  6175  6158  0  80   0   872  1661 -      pts/0    00:00:00 ps


and


Filename				Type		Size	Used	Priority
/host/ubuntu/disks/swap.disk            file		976552	4	-1

I am not sure what you mean by my Window Configuration...I'm knew at this Ubuntu thing...

It's a decent computer, I don't know my specs off the top of my head but I know I have a Pentium 4 and 1 GB of ram. (I'm pretty sure...) It was working fine earlier today.

---

### Post by ibuclaw on 2008-05-29
Well, that snapshot of your running processes doesn't show anything that appears to be hogging your system (good news), and you're swap drive is on and working (if it wasn't then you're system would be even slower!) but I notice that you do indeed have compiz running.

Here's a [small wiki]("http://wiki.compiz-fusion.org/") about compiz-fusion and what gives to Linux.

But simply put, compiz is a rather heavy beast on small hardware.
The more desktop compositing effects you turn on, although it is more aesthetically pleasing, the slower the desktop gets as your PC is constantly rendering the image on screen.
You also mentioned a slow logging in, and that may well be because of compiz loading all the enabled modules.

Although, it probably isn't your PC to blame either, more like a low-key graphics card.

Try opening up your Desktop Effects (Or Compiz Settings Manager) in **System>Preferences** and just disable some plugins that you'll never need.

Alternatively, go into **Appearance** and under the "**Visual Effects**" tab, set it to either "Normal" or "Extra".

Regards
Iain

---

### Post by lash9420 on 2008-05-30
I mean it was working fine earlier yesterday...Can this just change that quickly? Should I just reinstall it? I'm using Wubi and I don't have anything important...It's all on my flash drives.

---

### Post by jrybon on 2008-05-30
My system was running slow and that coincided with the Update Notification.  I ran the update, and rebooted.  Everything seems fine now.

Its almost like the update is given processor priority, or the updates are hogging disk space or something.

I'm currently trying to figure out how to submit this as an enhancement request.

---

### Post by lash9420 on 2008-05-30
While it was going slow, it alerted me that I had updates so I hoped that was the problem....Installed and restarted and it still do not work. Please! I really need this fixed!

---

