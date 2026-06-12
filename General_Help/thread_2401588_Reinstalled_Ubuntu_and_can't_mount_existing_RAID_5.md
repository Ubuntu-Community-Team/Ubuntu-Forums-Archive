---
title: "Reinstalled Ubuntu and can't mount existing RAID 5"
date: 2018-09-20
forum: General Help
---

### Post by stopshort on 2018-09-20
New to the forum, at least in membership, but have looked at various postings trying to solve my dilemma.  Also, I am not new to Linux, but I am not fluent in all the syntax.  I recently hit a snag when directed to reboot my computer after an update in which my computer continuously rebooted.  I did recover, but it wasn't the same so I decided to upgrade to 18.04.  I have been attempting to remount my RAID 5 (6 drives) with no success.  The results of lsblk suggest that all drives have been identified.  When I attempt mdadm --assemble it used to state "6 drives assembled", but now the same command is just blank.  This would seem to me that it is already assembled and just needs to be mounted.  Any help would be greatly appreciated.

My two issues are:
1) The RAID used to be mounted as md126p2 at /media/matt/FLIX and that mdadm mount function no longer works on this upgraded system.  I looked at the mdadm create function, but that seems to be for new builds and this is not.  Any ideas?

2) When I run cat /proc/mdstat I don't have any RAIDs (md) listed (results below).  This in conjunction with the lsblk data has got be baffled as to how the computer sees these drives in relation to one another.  Would it be easier to just reinstall the OS and potentially use the GUI to properly setup the partitions?

cat /proc/mdstat
Personalities : [raid6] [raid5] [raid4] 
unused devices: <none>


lsblk
NAME                    MAJ:MIN RM   SIZE RO TYPE   MOUNTPOINT
loop0                     7:0    0  86.9M  1 loop   /snap/core/4917
loop1                     7:1    0  34.7M  1 loop   /snap/gtk-common-themes/319
loop2                     7:2    0 140.9M  1 loop   /snap/gnome-3-26-1604/70
loop3                     7:3    0   2.3M  1 loop   /snap/gnome-calculator/180
loop4                     7:4    0    13M  1 loop   /snap/gnome-characters/103
loop5                     7:5    0  14.5M  1 loop   /snap/gnome-logs/37
loop6                     7:6    0   3.7M  1 loop   /snap/gnome-system-monitor/51
sda                       8:0    0   4.6T  0 disk   
&#9500;&#9472;sda1                    8:1    0   128M  0 part   
&#9492;&#9472;sda2                    8:2    0   4.6T  0 part   /media/matt/Seagate Expansion Drive
sdb                       8:16   0   3.7T  0 disk   
&#9492;&#9472;isw_dajdjecea_FLIX    253:0    0   8.2T  0 dmraid 
  &#9492;&#9472;isw_dajdjecea_FLIX1 253:1    0   128M  0 part   
sdc                       8:32   0   3.7T  0 disk   
&#9492;&#9472;isw_dajdjecea_FLIX    253:0    0   8.2T  0 dmraid 
  &#9492;&#9472;isw_dajdjecea_FLIX1 253:1    0   128M  0 part   
sdd                       8:48   0   3.7T  0 disk   
&#9492;&#9472;isw_dajdjecea_FLIX    253:0    0   8.2T  0 dmraid 
  &#9492;&#9472;isw_dajdjecea_FLIX1 253:1    0   128M  0 part   
sde                       8:64   0   3.7T  0 disk   
&#9492;&#9472;isw_dajdjecea_FLIX    253:0    0   8.2T  0 dmraid 
  &#9492;&#9472;isw_dajdjecea_FLIX1 253:1    0   128M  0 part   
sdf                       8:80   0   3.7T  0 disk   
&#9492;&#9472;isw_dajdjecea_FLIX    253:0    0   8.2T  0 dmraid 
  &#9492;&#9472;isw_dajdjecea_FLIX1 253:1    0   128M  0 part   
sdg                       8:96   0   3.7T  0 disk   
&#9492;&#9472;isw_dajdjecea_FLIX    253:0    0   8.2T  0 dmraid 
  &#9492;&#9472;isw_dajdjecea_FLIX1 253:1    0   128M  0 part   
sdh                       8:112  0 223.6G  0 disk   
&#9500;&#9472;sdh1                    8:113  0   512M  0 part   /boot/efi
&#9500;&#9472;sdh2                    8:114  0   244M  0 part   
&#9492;&#9472;sdh3                    8:115  0 222.9G  0 part   
  &#9500;&#9472;ubuntu--vg-root     253:2    0 207.1G  0 lvm    
  &#9492;&#9472;ubuntu--vg-swap_1   253:3    0  15.7G  0 lvm    
sdi                       8:128  0 223.6G  0 disk   
&#9500;&#9472;sdi1                    8:129  0   512M  0 part   
&#9492;&#9472;sdi2                    8:130  0 223.1G  0 part   /
sdj                       8:144  1  58.5G  0 disk   
&#9492;&#9472;sdj1                    8:145  1  58.5G  0 part   /media/matt/B
sr0                      11:0    1  45.7G  0 rom    /media/matt/SICARIO
sr1                      11:1    1  1024M  0 rom

---

