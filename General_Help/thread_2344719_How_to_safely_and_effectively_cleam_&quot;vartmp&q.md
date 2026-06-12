---
title: "How to safely and effectively cleam &quot;/var/tmp&quot; folder"
date: 2016-11-27
forum: General Help
---

### Post by p2bc on 2016-11-27
Ok back story and setup config:

I have my /usr, /var, /tmp, and so on on separate partitions, old school, and for every iteration of install these partitions have gone unchanged in their sizes. Just the occasion format with any new LTS fresh install release. I did a install in June with 16.04 with no hiccups what so ever.

Recently, two to three weeks, I have been warnings that my /var is full. Now in the past I would use my machine to test for php websites, I even had 3 full versions of Drupal 8 when it was in beta installed in my /var/www folder, along with about another hundred php files, and I never got a warning that my /var folder was full. Point beine, that was when I was actively putting stuff in my /var director. So you could understand my confusion for my recent warnings.

So I did a "du" command to see the trouble spot and got:

```

sudo du -sxhc /var/*
6.3M    /var/backups
128M    /var/cache
640K    /var/crash
849M    /var/lib
4.0K    /var/local
0    /var/lock
20M    /var/log
16K    /var/lost+found
4.0K    /var/mail
4.0K    /var/metrics
4.0K    /var/opt
0    /var/run
40K    /var/snap
128K    /var/spool
2.5G    /var/tmp
36K    /var/www
3.5G    total

```

The tmp folder is taking over two thirds the partition, so I did a few searches, and found nothing current, 2012, let alone relevant.

So I ask, what would be a safe and effective way to clear the /var/tmp folder.
Also what could be the cause, just for future problem solving. 
I did play with snappy a month ago, nothing serious, just install the equivalent of "Hello World", anyways was wondering if that could be the culprit causing the bloat?

Thanks in advance

---

### Post by ajgreeny on 2016-11-28
Show us what is actually in /var/tmp with an extension of that command to **sudo du -sxhc /var/tmp/*** and we may be able to give you some better clues of where to go from here.

---

### Post by p2bc on 2016-11-28
Fair enough

```

sudo du -sxhc /var/tmp/*
104M    /var/tmp/mkinitramfs_3Iz7hx
104M    /var/tmp/mkinitramfs_5JGFOW
104M    /var/tmp/mkinitramfs_8w2Ywh
104M    /var/tmp/mkinitramfs_BBGnC3
104M    /var/tmp/mkinitramfs_CP2xFx
104M    /var/tmp/mkinitramfs_F0T7ad
104M    /var/tmp/mkinitramfs_feTlJC
104M    /var/tmp/mkinitramfs_fnB1Xe
104M    /var/tmp/mkinitramfs_FOO9Lv
0    /var/tmp/mkinitramfs-FW_0gX9xy
0    /var/tmp/mkinitramfs-FW_3EEX3L
0    /var/tmp/mkinitramfs-FW_76mHuY
0    /var/tmp/mkinitramfs-FW_AB2OKP
0    /var/tmp/mkinitramfs-FW_dcXhrD
0    /var/tmp/mkinitramfs-FW_DvbLUm
0    /var/tmp/mkinitramfs-FW_eSnBEi
0    /var/tmp/mkinitramfs-FW_GbiPWU
0    /var/tmp/mkinitramfs-FW_GnblKb
0    /var/tmp/mkinitramfs-FW_GXhOFN
0    /var/tmp/mkinitramfs-FW_Imb2vh
0    /var/tmp/mkinitramfs-FW_Jpx5K1
0    /var/tmp/mkinitramfs-FW_lYtEcX
0    /var/tmp/mkinitramfs-FW_Mudype
0    /var/tmp/mkinitramfs-FW_nEmI7E
0    /var/tmp/mkinitramfs-FW_QjPlu8
0    /var/tmp/mkinitramfs-FW_UMlF15
0    /var/tmp/mkinitramfs-FW_vQ83zx
0    /var/tmp/mkinitramfs-FW_w8msYz
0    /var/tmp/mkinitramfs-FW_WEqXp8
0    /var/tmp/mkinitramfs-FW_WtUSdI
0    /var/tmp/mkinitramfs-FW_xS7tVZ
0    /var/tmp/mkinitramfs-FW_Y29zpE
0    /var/tmp/mkinitramfs-FW_Yqa8FS
104M    /var/tmp/mkinitramfs_iRO7LA
104M    /var/tmp/mkinitramfs_iutZ2N
103M    /var/tmp/mkinitramfs_k7Ml9R
107M    /var/tmp/mkinitramfs_MBWOx3
0    /var/tmp/mkinitramfs-OL_2Lq3nj
0    /var/tmp/mkinitramfs-OL_3uuXA7
0    /var/tmp/mkinitramfs-OL_44nyXw
0    /var/tmp/mkinitramfs-OL_cziV1b
0    /var/tmp/mkinitramfs-OL_FVXWGh
0    /var/tmp/mkinitramfs-OL_fwTI2u
0    /var/tmp/mkinitramfs-OL_G7ZNCC
0    /var/tmp/mkinitramfs-OL_hkZtPH
0    /var/tmp/mkinitramfs-OL_IEdgJW
0    /var/tmp/mkinitramfs-OL_IQaXiC
0    /var/tmp/mkinitramfs-OL_J0Xz15
0    /var/tmp/mkinitramfs-OL_lEEZ7U
0    /var/tmp/mkinitramfs-OL_lk1W73
0    /var/tmp/mkinitramfs-OL_m45SkD
0    /var/tmp/mkinitramfs-OL_PaDctj
0    /var/tmp/mkinitramfs-OL_QtLI9N
0    /var/tmp/mkinitramfs-OL_QUOeuI
0    /var/tmp/mkinitramfs-OL_rul1mQ
0    /var/tmp/mkinitramfs-OL_Wfnrqw
0    /var/tmp/mkinitramfs-OL_xJvlHH
0    /var/tmp/mkinitramfs-OL_Xyquo1
0    /var/tmp/mkinitramfs-OL_Y4ckoX
0    /var/tmp/mkinitramfs-OL_yywXoz
0    /var/tmp/mkinitramfs-OL_zKUt8E
104M    /var/tmp/mkinitramfs_P8j8NY
103M    /var/tmp/mkinitramfs_Pimm0R
104M    /var/tmp/mkinitramfs_R5FPo2
104M    /var/tmp/mkinitramfs_r82csg
104M    /var/tmp/mkinitramfs_RSNPMk
107M    /var/tmp/mkinitramfs_TaUSWE
107M    /var/tmp/mkinitramfs_uDtm9x
107M    /var/tmp/mkinitramfs_x88TWJ
104M    /var/tmp/mkinitramfs_xY3U66
104M    /var/tmp/mkinitramfs_Z3hhcH
104M    /var/tmp/mkinitramfs_z403au
8.0K    /var/tmp/systemd-private-006f49fe59264772b443eeeb0e4ea76a-colord.service-lYeZHL
8.0K    /var/tmp/systemd-private-006f49fe59264772b443eeeb0e4ea76a-rtkit-daemon.service-A3MQgq
8.0K    /var/tmp/systemd-private-006f49fe59264772b443eeeb0e4ea76a-systemd-timesyncd.service-s8gpYR
8.0K    /var/tmp/systemd-private-117f9a4db9634f5bb9bec4f6572cff72-colord.service-dbzEx7
8.0K    /var/tmp/systemd-private-117f9a4db9634f5bb9bec4f6572cff72-rtkit-daemon.service-5KPKam
8.0K    /var/tmp/systemd-private-117f9a4db9634f5bb9bec4f6572cff72-systemd-timesyncd.service-DwzitS
8.0K    /var/tmp/systemd-private-1d49aa85dae746b5bdc201007489bdb2-colord.service-4ECEJg
8.0K    /var/tmp/systemd-private-1d49aa85dae746b5bdc201007489bdb2-rtkit-daemon.service-uLhs8W
8.0K    /var/tmp/systemd-private-1d49aa85dae746b5bdc201007489bdb2-systemd-timesyncd.service-btkSEM
8.0K    /var/tmp/systemd-private-28c6dc78c7d24f258fd601815c0eef1a-systemd-timesyncd.service-TwQTv4
8.0K    /var/tmp/systemd-private-2b80e10284b940afbe486432d333705d-colord.service-dgBbpL
8.0K    /var/tmp/systemd-private-2b80e10284b940afbe486432d333705d-rtkit-daemon.service-XW7yRv
8.0K    /var/tmp/systemd-private-2b80e10284b940afbe486432d333705d-systemd-timesyncd.service-aDIUss
8.0K    /var/tmp/systemd-private-59d49e76ed6a409484311effbefd91cd-colord.service-dYSneR
8.0K    /var/tmp/systemd-private-59d49e76ed6a409484311effbefd91cd-rtkit-daemon.service-XANDeG
8.0K    /var/tmp/systemd-private-59d49e76ed6a409484311effbefd91cd-systemd-timesyncd.service-SCb43q
8.0K    /var/tmp/systemd-private-65dcd86cb2f24efba0052cf6c8f4274d-colord.service-aAFKcj
8.0K    /var/tmp/systemd-private-65dcd86cb2f24efba0052cf6c8f4274d-rtkit-daemon.service-hIIekV
8.0K    /var/tmp/systemd-private-65dcd86cb2f24efba0052cf6c8f4274d-systemd-timesyncd.service-T9XgtU
8.0K    /var/tmp/systemd-private-6ae74cc8222148b5945415f67fb059c6-colord.service-2E0AlH
8.0K    /var/tmp/systemd-private-6ae74cc8222148b5945415f67fb059c6-rtkit-daemon.service-0TnoNL
8.0K    /var/tmp/systemd-private-6ae74cc8222148b5945415f67fb059c6-systemd-timesyncd.service-bM5RJr
8.0K    /var/tmp/systemd-private-b505a486c4e144e898619de2fb0b734e-colord.service-wESBP1
8.0K    /var/tmp/systemd-private-b505a486c4e144e898619de2fb0b734e-rtkit-daemon.service-NS11qL
8.0K    /var/tmp/systemd-private-b505a486c4e144e898619de2fb0b734e-systemd-timesyncd.service-gA0s1I
8.0K    /var/tmp/systemd-private-c06283c76ebe463385400e0be47dfeb3-colord.service-05GMC1
8.0K    /var/tmp/systemd-private-c06283c76ebe463385400e0be47dfeb3-rtkit-daemon.service-od0jRi
8.0K    /var/tmp/systemd-private-c06283c76ebe463385400e0be47dfeb3-systemd-timesyncd.service-nyeVZs
8.0K    /var/tmp/systemd-private-cd697887e34d48c3a842bb1d6b6cae1e-colord.service-3YsQZp
8.0K    /var/tmp/systemd-private-cd697887e34d48c3a842bb1d6b6cae1e-rtkit-daemon.service-Z4uwWx
8.0K    /var/tmp/systemd-private-cd697887e34d48c3a842bb1d6b6cae1e-systemd-timesyncd.service-fuzMrp
8.0K    /var/tmp/systemd-private-f890b18925af40e58123f3d152e94e6e-colord.service-5DEHK3
8.0K    /var/tmp/systemd-private-f890b18925af40e58123f3d152e94e6e-rtkit-daemon.service-rB57Jt
8.0K    /var/tmp/systemd-private-f890b18925af40e58123f3d152e94e6e-systemd-timesyncd.service-l6aV28
2.5G    total

```

---

### Post by p2bc on 2016-11-28
Just for giggles I wanted to see what was in one of the "104M" folders. 104 is not that big, but multiplied by 24 and you pretty much get 2.5 gigs. So just picking one at random.

```

sudo du -sxhc /var/tmp/mkinitramfs_3Iz7hx/*
1.4M    /var/tmp/mkinitramfs_3Iz7hx/bin
24K    /var/tmp/mkinitramfs_3Iz7hx/conf
248K    /var/tmp/mkinitramfs_3Iz7hx/etc
8.0K    /var/tmp/mkinitramfs_3Iz7hx/init
93M    /var/tmp/mkinitramfs_3Iz7hx/lib
4.0K    /var/tmp/mkinitramfs_3Iz7hx/lib64
4.0K    /var/tmp/mkinitramfs_3Iz7hx/run
2.3M    /var/tmp/mkinitramfs_3Iz7hx/sbin
204K    /var/tmp/mkinitramfs_3Iz7hx/scripts
7.2M    /var/tmp/mkinitramfs_3Iz7hx/usr
20K    /var/tmp/mkinitramfs_3Iz7hx/var
104M    total

```

---

### Post by ajgreeny on 2016-11-28
I noticed all those mkinitramfs* shown in the tmp system files but I really have no idea what they are all about as I have none at all in my /var/tmp/ folder.  A search, however, suggests that encryption of filesystem may be part of the story; are you using encryption, or maybe LVM partitioning?

---

### Post by HermanAB on 2016-11-28
Well, if /tmp is a tmpfs (RAM disk), then all you need to do is reboot...

---

### Post by vasa1 on 2016-11-28
> **HermanAB said:**
> Well, if /tmp is a tmpfs (RAM disk), then all you need to do is reboot...
But OP wrote> 
I have my /usr, /var, /tmp, and so on on separate partitions, old school, and for every iteration of install these partitions have gone unchanged in their sizes.so I'm guessing that won't be applicable? And the issue seems to relate to /var/tmp and not to /tmp itself.

*man mkinitramfs* has this:
```
       mkinitramfs  honours  the  TMPDIR environment variable. If set, it uses
       subdirectories in the given directory to create its  temporary  working
       directories.  Else  it uses /var/tmp as default value for that purpose.
       The given  directory  should  be  on  a  filesystem  which  allows  the
       execution  of  files stored there, i.e.  should not be mounted with the
       noexec mount option.

```
And I came across [tmp file is left under /var/tmp if mkinitramfs fails]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=814345")

---

### Post by p2bc on 2016-11-28
To: HermanAB - As vasa1, it is not the same as /tmp so it does not get cleared. Something is clearing, because when I do restart the system the warning displays a range on free space from 0mg, to 10mg it varies and changes every time, just not enough.

To: ajgreeny - Yes, the main partition (/dev/sda1) is encrypted with LVMs as virtual partition for my different mounting points.

```

sudo lvdisplay -m
  --- Logical volume ---
  LV Path                /dev/systm/lv-root
  LV Name                lv-root
  VG Name                systm
  LV UUID                aYworM-hjja-4WXj-c2SV-9jgs-Fr0O-4Kc1gD
  LV Write Access        read/write
  LV Creation host, time comp1, 2016-04-26 13:35:24 -0400
  LV Status              available
  # open                 1
  LV Size                2.79 GiB
  Current LE             715
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:1
   
  --- Segments ---
  Logical extents 0 to 714:
    Type        linear
    Physical volume    /dev/mapper/sdb5_crypt
    Physical extents    0 to 714
   
   
  --- Logical volume ---
  LV Path                /dev/systm/lv-var
  LV Name                lv-var
  VG Name                systm
  LV UUID                uwl6L4-jQn6-LD4O-Fqcc-qCo7-IpDc-WQ7jkW
  LV Write Access        read/write
  LV Creation host, time comp1, 2016-04-26 13:37:09 -0400
  LV Status              available
  # open                 1
  LV Size                3.72 GiB
  Current LE             953
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:2
   
  --- Segments ---
  Logical extents 0 to 952:
    Type        linear
    Physical volume    /dev/mapper/sdb5_crypt
    Physical extents    1191 to 2143
   
   
  --- Logical volume ---
  LV Path                /dev/systm/lv-tmp
  LV Name                lv-tmp
  VG Name                systm
  LV UUID                YwA3gC-aeoJ-k31M-hKXa-KjbK-Yiou-y5ibl1
  LV Write Access        read/write
  LV Creation host, time comp1, 2016-04-26 13:39:53 -0400
  LV Status              available
  # open                 1
  LV Size                1.86 GiB
  Current LE             476
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:3
   
  --- Segments ---
  Logical extents 0 to 475:
    Type        linear
    Physical volume    /dev/mapper/sdb5_crypt
    Physical extents    715 to 1190
   
   
  --- Logical volume ---
  LV Path                /dev/systm/lv-swap
  LV Name                lv-swap
  VG Name                systm
  LV UUID                mSd5xB-0bee-ivUh-Hxwz-NvUj-j6pC-LzqbPH
  LV Write Access        read/write
  LV Creation host, time comp1, 2016-04-26 13:40:41 -0400
  LV Status              available
  # open                 2
  LV Size                1.86 GiB
  Current LE             476
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:4
   
  --- Segments ---
  Logical extents 0 to 475:
    Type        linear
    Physical volume    /dev/mapper/sdb5_crypt
    Physical extents    3097 to 3572
   
   
  --- Logical volume ---
  LV Path                /dev/systm/lv-usr
  LV Name                lv-usr
  VG Name                systm
  LV UUID                9sBZDf-gzng-jptY-nDD0-ThWo-9PUz-nR6JYT
  LV Write Access        read/write
  LV Creation host, time comp1, 2016-04-26 17:49:11 -0400
  LV Status              available
  # open                 1
  LV Size                9.31 GiB
  Current LE             2384
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:5
   
  --- Segments ---
  Logical extents 0 to 2383:
    Type        linear
    Physical volume    /dev/mapper/sdb5_crypt
    Physical extents    3573 to 5956
   
   
  --- Logical volume ---
  LV Path                /dev/systm/lv-home
  LV Name                lv-home
  VG Name                systm
  LV UUID                Qe0apR-5v2x-owtv-peEW-KZmm-uUkP-R2RABj
  LV Write Access        read/write
  LV Creation host, time comp1, 2016-04-26 17:49:49 -0400
  LV Status              available
  # open                 1
  LV Size                352.98 GiB
  Current LE             90362
  Segments               2
  Allocation             inherit
  Read ahead sectors     auto
  - currently set to     256
  Block device           252:6
   
  --- Segments ---
  Logical extents 0 to 89408:
    Type        linear
    Physical volume    /dev/mapper/sdb5_crypt
    Physical extents    5957 to 95365
   
  Logical extents 89409 to 90361:
    Type        linear
    Physical volume    /dev/mapper/sdb5_crypt
    Physical extents    2144 to 3096



```

But like I said, nothing new.

More back story: This is a dual boot system laptop, with Linux on /dev/sda1, and Windows on /dev/sda2. I use the Windows for work and have to bring it around to see clients. So if it ever gets stolen and the thief tries to access my person stuff, even from a LiveCD, like banking, browser history, swap files, it is all encrypted so good luck. As for the Windows side, they would see CAD drawing and Photoshop files for work, big woop.

---

### Post by p2bc on 2016-11-28
> **vasa1 said:**
> 

*man mkinitramfs* has this:
```
       mkinitramfs  honours  the  TMPDIR environment variable. If set, it uses
       subdirectories in the given directory to create its  temporary  working
       directories.  Else  it uses /var/tmp as default value for that purpose.
       The given  directory  should  be  on  a  filesystem  which  allows  the
       execution  of  files stored there, i.e.  should not be mounted with the
       noexec mount option.

```
And I came across [tmp file is left under /var/tmp if mkinitramfs fails]("https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=814345")


Thanks i will check it out.

---

### Post by ajgreeny on 2016-11-28
That's a good find vasa1 !

I wonder if it is worth creating a new line in /etc/rc.local or somewhere else which will remove all those presumably unnecessary mkinitramfs_* files immediately on boot.  That assumes those files really are not needed for any reason, and certainly the bug you linked to suggests that should be the case but that bug means they are left behind and not removed.

Alternatively, perhaps the $TMPDIR variable needs setting to /tmp instead of /var/tmp.  Not sure how to do that, but I'm sure it must be possible and someone will hopefully be able to tell us how.

---

### Post by p2bc on 2016-11-30
Ok update;

After reading the link vasa1 shared, thank you by the way, I went to clear out my /boot folder. Oh yeah I mention I am "old school" my /boot folder is on its own 500mg partition, because it can't be part of the encrypted partition if you were wondering why. Anyways, so after every 3 or 4 kernel releases, it does get full. I simply go clear them out with Synaptic, or manually, anyways it does happen that I get a message that /boot is full and can't not apply new linux-image. For the most part I clean out and go about my business, BUT sometime I do hit ignore, and say I will deal with it later.

So after reading the link from vasa1, I went to clean up with Synaptic, and..... Synaptic crashs. I re-open,... crash. Few curse words later, and getting a warning I should do, "sudo dpkg --configure -a". So I do and ... irony is;

```

sudo dpkg --configure -a
dpkg: error: failed to write status database record about 'python-dnspython' to '/var/lib/dpkg/status': **No space left on device**

```

The /var folder is full... so I can't do what I need to do to fix my /var folder from being full. So I start manually deleting the "mkinitramfs" folders, oldest first. After a dozen or so, I can run the "sudo dpkg --configure -a" command, so I can finish clean /boot partition so I can stop filling my /var/tmp folder.

So after all that, and if you are still reading this crazy long post, everything seems to be better. The /var partition is stay relatively low, only 10mgs since I deleted the dozen "mkinitramfs" folders. The /boot partition is clean for about 2 to 3 linux-images, so all is good.


Now if I may bring this back to my original query, is there recommendation to safely and effectively clean "/var/tmp" folder. The bug aside, and me staying on top of /boot partition not filling up, short of me manually deleting the "mkinitramfs" folders manually. My concern is that I could go too far and delete too much. How do I avoid ALL this in the future? I still have another dozen or so "mkinitramfs" folders lingering around.

Thanks again

---

### Post by kpatz on 2016-11-30
I think you can safely delete all the mkinitramfs folders.  Maybe to be "super safe", delete all but the most recent, especially if it's today's date.  They're temporary and are supposed to be deleted when mkinitramfs finishes, but if your /boot was full, it could have caused mkinitramfs to fail without cleaning up after itself.

None of my systems have any stray mkinitramfs folders in /var/tmp.

You can use```
sudo apt-get autoremove
```to clean out older kernels from /boot and associated files (headers etc.) that land in /var as well.

---

### Post by p2bc on 2016-12-01
Thx [[COLOR=#000000]kpatz[/COLOR]]("https://ubuntuforums.org/member.php?u=223801&") for the advise, but I am sorry to say "sudo apt-get autoremove" had no effect.

---

### Post by DuckHook on 2016-12-01
> **p2bc said:**
> Thx [[COLOR=#000000]kpatz[/COLOR]]("https://ubuntuforums.org/member.php?u=223801&") for the advise, but I am sorry to say "sudo apt-get autoremove" had no effect.Are you on 16.04? If so, do:```
sudo apt autoremove
```&#8230;*not* apt-get. The new apt command defaults to removing all kernels except the last two. However, it will not remove kernels with the manual installation flag set. You will still have to remove any of those yourself. However, once you've beaten your kernel structure back down to the default ones that came with initial installation, all future invocations of *apt autoremove* will keep you running with just the two latest. The best procedure is to habitually run autoremove with every *full-upgrade* (which replaces dist-upgrade):```
sudo apt update && sudo apt full-upgrade && sudo apt autoremove && sudo apt clean
```I also run *apt clean* to free up old packages too.

Don't think it too much trouble to delete only those files created by your rogue process. Hopefully, freeing up room in /boot will get rid of your errant mkinitramfs files in future. If all else fails, fire up a LiveUSB, get into your /var/tmp that way and sudo rm all that you need to delete.

Remember, in OS as in medicine: first, do no harm.

---

### Post by kingneutron on 2016-12-01
> So I ask, what would be a safe and effective way to clear the /var/tmp folder.

--For (interactively) safely deleting files and directories as root, nothing I have found is better or safer than Midnight Commander.

(as root, or add 'sudo' before the commands)
' apt-get update;apt-get install mc '
' mc /var/tmp '

--Once MC fires up, you will see a 2-pane window with 2 directories that you can TAB between.  In /var/tmp, hit the Grey+ key (on the numeric keypad) and you will see a Select window come up (See attmt.)   From there, it should default to "*" which will select all files + dirs under your current dir.  You can also manually select/unselect as needed with the Insert key.   When you're ready, press F8 key to recursively Delete what you selected - it will ask for confirmation.  **Note** if you have not made a selection, F8 will by default delete whatever the "cursor line" is currently on (use up/down arrow keys to move around.)    **Bonus:** MC does not require X and can run directly from a TTY console.

--I once read that accidental RM usage was around 80% root cause of all *NIX system failures.  So, I almost _never_ use RM directly from the command line -- I use MC to be safer.

--However, if you absolutely need to script an RM, I have included a 2nd attachment that demonstrates how to do it relatively safely. Modify the "dest" and the "time find" lines for your needs.

---

### Post by vasa1 on 2016-12-01
> **DuckHook said:**
> ... it will not remove kernels with the manual installation flag set. You will still have to remove any of those yourself. ...

So would running something like ```
apt list --installed | grep -i linux
```help identify those kernels? In my case, nothing encrypted, the kernels seem automatic:```
$ apt list --installed | grep -i linux

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

console-setup-linux/xenial-updates,now 1.108ubuntu15.2 all [installed,automatic]
extlinux/xenial,now 3:6.03+dfsg-11ubuntu1 amd64 [installed,automatic]
libselinux1/xenial,now 2.4-3build2 amd64 [installed]
linux-base/xenial,now 4.0ubuntu1 all [installed,automatic]
linux-firmware/xenial-updates,now 1.157.5 all [installed,automatic]
linux-generic/xenial-updates,xenial-security,now 4.4.0.51.54 amd64 [installed]
linux-headers-4.4.0-47/xenial-updates,xenial-security,now 4.4.0-47.68 all [installed,automatic]
linux-headers-4.4.0-47-generic/xenial-updates,xenial-security,now 4.4.0-47.68 amd64 [installed,automatic]
linux-headers-4.4.0-51/xenial-updates,xenial-security,now 4.4.0-51.72 all [installed,automatic]
linux-headers-4.4.0-51-generic/xenial-updates,xenial-security,now 4.4.0-51.72 amd64 [installed,automatic]
linux-headers-generic/xenial-updates,xenial-security,now 4.4.0.51.54 amd64 [installed,automatic]
linux-image-4.4.0-47-generic/xenial-updates,xenial-security,now 4.4.0-47.68 amd64 [installed,automatic]
linux-image-4.4.0-51-generic/xenial-updates,xenial-security,now 4.4.0-51.72 amd64 [installed,automatic]
linux-image-extra-4.4.0-47-generic/xenial-updates,xenial-security,now 4.4.0-47.68 amd64 [installed,automatic]
linux-image-extra-4.4.0-51-generic/xenial-updates,xenial-security,now 4.4.0-51.72 amd64 [installed,automatic]
linux-image-generic/xenial-updates,xenial-security,now 4.4.0.51.54 amd64 [installed,automatic]
linux-libc-dev/xenial-updates,xenial-security,now 4.4.0-51.72 amd64 [installed,automatic]
linux-sound-base/xenial,now 1.0.25+dfsg-0ubuntu5 all [installed,automatic]
syslinux/xenial,now 3:6.03+dfsg-11ubuntu1 amd64 [installed]
syslinux-common/xenial,now 3:6.03+dfsg-11ubuntu1 all [installed]
syslinux-legacy/xenial,now 2:3.63+dfsg-2ubuntu8 amd64 [installed]
util-linux/xenial-updates,now 2.27.1-6ubuntu3.1 amd64 [installed]
$ 

```

---

### Post by kpatz on 2016-12-01
@vasa1, you have 2 kernels installed (current + previous version), this is normal.  Both are automatic, so next time you install a kernel update, you'll have the new one as the current, the 4.4.0-51 as the previous and the 4.4.0-47.68 would be removed when you do an apt autoremove.

---

### Post by vasa1 on 2016-12-01
> **kpatz said:**
> @vasa1, you have 2 kernels installed (current + previous version), this is normal.  Both are automatic, so next time you install a kernel update, you'll have the new one as the current, the 4.4.0-51 as the previous and the 4.4.0-47.68 would be removed when you do an apt autoremove.
Yes, I don't have any kernel issues. Autoremove works just fine for me. I thought that OP could identify which of his kernels were manually installed.

---

### Post by DuckHook on 2016-12-01
> **vasa1 said:**
> So would running something like ```
apt list --installed | grep -i linux
```help identify those kernels?

> **vasa1 said:**
> …I thought that OP could identify which of his kernels were manually installed.I actually like your way better than mine, which would have been the more obvious&#8213;and clunky:```
apt-mark showmanual | grep linux
```…followed by:```
apt-mark showauto | grep linux
```On my system, this yields the following:```
DuckHook@Prime:~$ apt-mark showmanual | grep linux
console-setup-linux
libselinux1
linux-generic
linux-signed-generic
util-linux

DuckHook@Prime:~$ apt-mark showauto | grep linux
extlinux
libselinux1:i386
linux-base
linux-firmware
linux-headers-4.4.0-45
linux-headers-4.4.0-45-generic
linux-headers-4.4.0-47
linux-headers-4.4.0-47-generic
linux-headers-generic
linux-image-4.4.0-45-generic
linux-image-4.4.0-47-generic
linux-image-extra-4.4.0-45-generic
linux-image-extra-4.4.0-47-generic
linux-image-generic
linux-libc-dev
linux-signed-image-4.4.0-45-generic
linux-signed-image-4.4.0-47-generic
linux-signed-image-generic
linux-sound-base
pptp-linux
syslinux
syslinux-common
syslinux-legacy
```The important thing to look at is that no *versioned* kernels appear in *showmanual*, and only two show in *showauto*. The *linux-generic* and *linux-signed-generic* sans version numbers are as expected and in fact *must* be present in *showmanual* else system will break.

---

### Post by DuckHook on 2016-12-01
> **kingneutron said:**
> &#8230;For (interactively) safely deleting files and directories as root, nothing I have found is better or safer than Midnight Commander&#8230;This is an excellent recommendation. MC is great for new and power users alike. I have it installed too, but have fallen into the habit of advising only processes that can be executed from a native installation whenever possible.> I once read that accidental RM usage was around 80% root cause of all *NIX system failures.  So, I almost _never_ use RM directly from the command line -- I use MC to be safer.@p2bc

To delete the files that you are targetting, you will have to invoke mc with sudo. This still makes it dangerous, but less so than barebones rm.

Let us know how it goes.

---

### Post by p2bc on 2017-01-03
Happy New Year all...

Been busy, but wanted to follow up.

After manually deleting all the mkinitramfs folders, and running "sudo apt autoremove", aannnd staying on top of keeping the /boot partition clear so the bug stays at bay, my /var partition has not been screaming at me so **all is good**, I guess.

I just want to take a moment to thank everyone for their help.

---

### Post by jis on 2017-04-10
I updated instructions [here]("https://help.ubuntu.com/community/RemoveOldKernels").

---

