---
title: "ZFS 1TB of space lost?"
date: 2015-02-25
forum: General Help
---

### Post by Athideus on 2015-02-25
[COLOR=#000000][FONT=Tahoma]I wasn't too sure where to post this, but hopefully someone here can help me out. Over the weekend I switched from XFS/mhddfs with snapraid dual parity to ZFS RAIDz2 and, using the same exact drives with the same basic setup, I lost almost a TB of available space. When I was using XFS I had 9.1TB of available space but now when I switched to ZFS I have only 8.28TB. Checking all the calculators for RAIDz2, they all say that I should have 9.1TB of free space. Coincidentally, I destroyed the pool and set it up as a RAIDz1 and a RAIDz3 and the available storage matched what the calculator said. Is this simply a current bug with ZFS and I'm out of luck or is there something fixable that could be causing this? Below is all the information 

7x2TB drives in RAIDz2  [/FONT][/COLOR]Ubuntu 14.04.2 LTS (GNU/Linux 3.13.0-45-generic x86_64)[COLOR=#000000][FONT=Tahoma]
[/FONT][/COLOR]```

---------------------------------zpool list-----------------------------------
NAME   SIZE  ALLOC   FREE    CAP  DEDUP  HEALTH  ALTROOT
loot  12.6T  10.0T    2.59T    79%    1.00x     ONLINE     -


---------------------------------zpool status------------------------------
pool: loot
 state: ONLINE
scan: none requested
config:


        NAME        STATE     READ WRITE CKSUM
        loot        ONLINE       0     0     0
       raidz2-0  ONLINE       0     0     0
            sda     ONLINE       0     0     0
            sdb     ONLINE       0     0     0
            sdc     ONLINE       0     0     0
            sdd     ONLINE       0     0     0
            sde     ONLINE       0     0     0
            sdf      ONLINE       0     0     0
            sdh     ONLINE       0     0     0


errors: No known data errors


---------------- zpool get version loot--------------------
NAME  PROPERTY  VALUE    SOURCE
loot  version   -        default
------------------ zfs get version loot---------------
NAME  PROPERTY  VALUE    SOURCE
loot  version   5        -




----------------------------zfs list------------------------------------
NAME                                  USED  AVAIL  REFER  MOUNTPOINT
loot                                  6.68T  1.59T   288K  /loot
loot/loot                             6.68T  1.59T   496K  /loot/loot
loot/loot/Anime                       2.54T  1.59T  2.54T  /loot/loot/Anime
loot/loot/BDMV                        95.0G  1.59T  95.0G  /loot/loot/BDMV
loot/loot/DND                         409M  1.59T   409M  /loot/loot/DND
loot/loot/Documents                   376K  1.59T   376K  /loot/loot/Documents
loot/loot/FLAC Music                  8.98G  1.59T  8.98G  /loot/loot/FLAC Music
loot/loot/Games                       234G  1.59T   234G  /loot/loot/Games
loot/loot/Manga                       7.58G  1.59T  7.58G  /loot/loot/Manga
loot/loot/Movies                      1.42T  1.59T  1.42T  /loot/loot/Movies
loot/loot/Music                       84.6G  1.59T  84.6G  /loot/loot/Music
loot/loot/Operating Systems           3.10G  1.59T  3.10G  /loot/loot/Operating Systems
loot/loot/Pictures                    3.09G  1.59T  3.09G  /loot/loot/Pictures
loot/loot/Programs                    2.84G  1.59T  2.84G  /loot/loot/Programs
loot/loot/Random                      2.82G  1.59T  2.82G  /loot/loot/Random
loot/loot/TV Shows                   2.29T  1.59T  2.29T  /loot/loot/TV Shows


------------------------------zfs get used/available------------------------
loot/loot  used                  6.68T                  -
loot/loot  available             1.59T                  -

```

---

### Post by tgalati4 on 2015-02-25
ZFS is a 128-bit file system with CRC protection of files.  Add parity and RAID striping and that adds up to a lot of overhead.  What pool version of ZFS are you running?  There are several versions with different features:  [http://docs.oracle.com/cd/E23824_01/html/821-1448/gjxle.html](http://docs.oracle.com/cd/E23824_01/html/821-1448/gjxle.html).

According to my search, Linux uses pool version 14 or 28.  So it's possible that the calculators used the feature set of 14, but the feature set of 28 requires more overhead.

---

### Post by Athideus on 2015-02-25
The version it says is -

NAME  PROPERTY  VALUE    SOURCE
loot  version   -        default

I'd be more willing to accept that I'd lose a max 100GB of usable space for overhead and such, but definitely not almost 1TB. Not to mention, when I built the pools using the other RAIDz level, they matched what the calculator told me

---

### Post by tgalati4 on 2015-02-25
I run ZFS on a freenas server, so I really can't help further.  I'm just pointing out the fact that there are many flavors of ZFS and many configurations, so it's not surprizing that the free-space calculator is incorrect.  Because the pool status shows OK, I presume that it really is OK and that is the normal overhead.

---

