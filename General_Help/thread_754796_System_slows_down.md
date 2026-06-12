---
title: "System slows down"
date: 2008-04-14
forum: General Help
---

### Post by balagunner on 2008-04-14
The system slows down right from the beginning. The Sys monitor shows that both my CPU's have 90% usage.

Please help me.
Is there something to control the start up processes as in Windows e.g. Sys Mechanic or msconfig

Xorg takes around 500 Mb of Virtual memory!! What is Xorg??

---

### Post by ryanhaigh on 2008-04-14
Xorg is the graphical environment but should not be using that much ram, what process is using all that cpu. You can use the system monitor or the command top in a terminal to find out. If you have desktop effects enabled try disabling them for the moment.

---

### Post by balagunner on 2008-04-17
They have been disabled but still the system hangs while playing songs quite often.

---

### Post by Hallvor on 2008-04-17
You need to find out what is using all your CPU - not ram. Please post the output of 

```
top
```

---

### Post by balagunner on 2008-04-18
33 root      10  -5     0    0    0 S   74  0.0   6:59.39 kacpid
   34 root      10  -5     0    0    0 D   13  0.0   1:17.51 kacpi_notify
 5798 balaji    15   0  167m  49m  20m S    1  2.5   0:15.40 firefox-bin
 5063 root      15   0  350m  20m 7812 S    1  1.0   0:11.94 Xorg
 5059 haldaemo  16   0  3260 1188 1036 S    0  0.1   0:00.14 hald-addon-stor
    1 root      16   0  2952 1852  532 S    0  0.1   0:01.18 init
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper
   31 root      10  -5     0    0    0 S    0  0.0   0:00.04 kblockd/0
   32 root      19  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1
  136 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod
  164 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
  165 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush
  166 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0
  217 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0
  218 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1
 1987 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd
 1988 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd
 2059 root      10  -5     0    0    0 S    0  0.0   0:00.02 ata/0
 2060 root      10  -5     0    0    0 S    0  0.0   0:00.04 ata/1
 2072 root      19  -5     0    0    0 S    0  0.0   0:00.00 ata_aux
 2211 root      10  -5     0    0    0 S    0  0.0   0:00.09 scsi_eh_0
 2212 root      14  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1
 2238 root      13  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2
 2239 root      10  -5     0    0    0 S    0  0.0   0:00.01 scsi_eh_3
 2497 root      12  -5     0    0    0 S    0  0.0   0:00.01 kjournald
 2702 root      12  -4  3072 1420  408 S    0  0.1   0:00.24 udevd
 3705 root      17  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused
 4201 root      18   0  4024 1288  588 S    0  0.1   0:00.43 mount.ntfs-3g
 4204 root      15   0  3788 1056  584 S    0  0.1   0:00.14 mount.ntfs-3g
 4352 root      15   0  2900  892  676 S    0  0.0   0:00.00 pppd
 4503 root      18   0  1692  512  448 S    0  0.0   0:00.00 getty
 4504 root      18   0  1696  520  448 S    0  0.0   0:00.00 getty
 4507 root      18   0  1692  516  448 S    0  0.0   0:00.00 getty
 4508 root      18   0  1692  512  448 S    0  0.0   0:00.00 getty

---

### Post by balagunner on 2008-04-18
> **balagunner said:**
> 33 root      10  -5     0    0    0 S   74  0.0   6:59.39 kacpid
   34 root      10  -5     0    0    0 D   13  0.0   1:17.51 kacpi_notify
 5798 balaji    15   0  167m  49m  20m S    1  2.5   0:15.40 firefox-bin
 5063 root      15   0  350m  20m 7812 S    1  1.0   0:11.94 Xorg
 5059 haldaemo  16   0  3260 1188 1036 S    0  0.1   0:00.14 hald-addon-stor
    1 root      16   0  2952 1852  532 S    0  0.1   0:01.18 init
    2 root      10  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0
    4 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      34  19     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/0
   10 root      10  -5     0    0    0 S    0  0.0   0:00.00 events/1
   11 root      10  -5     0    0    0 S    0  0.0   0:00.00 khelper
   31 root      10  -5     0    0    0 S    0  0.0   0:00.04 kblockd/0
   32 root      19  -5     0    0    0 S    0  0.0   0:00.00 kblockd/1
  136 root      10  -5     0    0    0 S    0  0.0   0:00.00 kseriod
  164 root      20   0     0    0    0 S    0  0.0   0:00.00 pdflush
  165 root      15   0     0    0    0 S    0  0.0   0:00.00 pdflush
  166 root      15  -5     0    0    0 S    0  0.0   0:00.00 kswapd0
  217 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/0
  218 root      15  -5     0    0    0 S    0  0.0   0:00.00 aio/1
 1987 root      10  -5     0    0    0 S    0  0.0   0:00.00 ksuspend_usbd
 1988 root      10  -5     0    0    0 S    0  0.0   0:00.00 khubd
 2059 root      10  -5     0    0    0 S    0  0.0   0:00.02 ata/0
 2060 root      10  -5     0    0    0 S    0  0.0   0:00.04 ata/1
 2072 root      19  -5     0    0    0 S    0  0.0   0:00.00 ata_aux
 2211 root      10  -5     0    0    0 S    0  0.0   0:00.09 scsi_eh_0
 2212 root      14  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_1
 2238 root      13  -5     0    0    0 S    0  0.0   0:00.00 scsi_eh_2
 2239 root      10  -5     0    0    0 S    0  0.0   0:00.01 scsi_eh_3
 2497 root      12  -5     0    0    0 S    0  0.0   0:00.01 kjournald
 2702 root      12  -4  3072 1420  408 S    0  0.1   0:00.24 udevd
 3705 root      17  -5     0    0    0 S    0  0.0   0:00.00 kpsmoused
 4201 root      18   0  4024 1288  588 S    0  0.1   0:00.43 mount.ntfs-3g
 4204 root      15   0  3788 1056  584 S    0  0.1   0:00.14 mount.ntfs-3g
 4352 root      15   0  2900  892  676 S    0  0.0   0:00.00 pppd
 4503 root      18   0  1692  512  448 S    0  0.0   0:00.00 getty
 4504 root      18   0  1696  520  448 S    0  0.0   0:00.00 getty
 4507 root      18   0  1692  516  448 S    0  0.0   0:00.00 getty
 4508 root      18   0  1692  512  448 S    0  0.0   0:00.00 getty


There was more but I could copy only these many. 
Recently I had installed kde-core, deluge and other software.
Is it because of that?

Thanks

---

### Post by Hallvor on 2008-04-18
I can`t see any process using much CPU. If both processors are using some 80% CPU, you have to look for processes using it. I couldn`t see anything from what you posted, but a large number of processes will also eat a lot of CPU.

Mixing Gnome with KDE is not a good thing. It is like alcohol and women. They are better enjoyed separately. But mixing them can be a real disaster. Better to go with pure Gnome or pure KDE. It will give you a lighter system. Besides, Gnome applications run better in Gnome and KDE applications run better in KDE.

---

### Post by ryanhaigh on 2008-04-18
It looks to me like kacpid is using all of your cpu, according to google searches this is likely due to bugs in your systems bios. You could try updating the bios if there is a newer version availalble for your pc. Google searches provide a range of 'solutions' that worked for different people...maybe one of them will help you.

---

### Post by balagunner on 2008-04-18
How to update bios?
Never done it before.
 
and how to completely remove "kde" from my system

---

### Post by ryanhaigh on 2008-04-19
You will need to check the website of your system manufacturer for bios updates and do it via windows or a floppy. They should have instructions, as for removing kde I would think that removing kde's base libraries would force everything else to be removed, although I am sure there are better answers available via a search on google/ubuntu documentation site/forums.

---

### Post by BLTicklemonster on 2008-04-27
ata/0 is eating me alive on hardy updated beta (just updated)
```

 1449 root      15  -5     0    0    0 R 79.7  0.0  11:25.20 ata/0              
 6825 root      20   0 67476  39m 7188 S  6.3  4.6   1:30.95 Xorg               
 7372 bill      20   0  201m  77m  22m R  3.3  8.9   1:07.26 firefox            
 7583 bill      20   0 84060  19m  10m S  2.0  2.2   0:01.10 gnome-terminal     
 7042 bill      20   0 45552  27m 9556 R  1.3  3.2   0:35.86 python             
 5666 root      20   0  3416 1152 1008 S  0.7  0.1   0:00.06 hald-addon-inpu    
    1 root      20   0  2844 1688  544 S  0.0  0.2   0:01.16 init 
```   

I have a P4 3.3 gig computer, 1 gig Ram and an FX5200 video card, and Hardy feels like it's installed on a Pentium 75 meg with 4 megs ram and an S3 virge isa card.

I have done some tweaking with xorg.conf, which had all kinds of odd stuff, like it showed my onboard video, not my pci card (onboard is disabled in bios) and other plain odd stuff (used settings from my gutsy install) and overall, the system is more responsive (bogs down less, locks up less) but it's still 
THE
WORST
BETA-ISH LTS
UBUNTU
I've used.

---

