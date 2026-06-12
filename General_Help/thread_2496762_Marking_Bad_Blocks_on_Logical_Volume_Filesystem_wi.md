---
title: "Marking Bad Blocks on Logical Volume Filesystem with Multiple Physical Volumes"
date: 2024-04-11
forum: General Help
---

### Post by pogo7 on 2024-04-11
Hey everyone,




I've encountered a situation where I needed to mark bad blocks on a ext4 - Logical Volume (LV) filesystem that spans multiple Physical Volumes (PVs) within a Volume Group (VG). I wanted to share my approach and confirm if it's the correct way to handle this scenario.




I have a setup where my LV spans across two HDDs (sda and sdc) within a VG.
One of the HDDs (sda) has bad blocks that need to be marked to prevent data corruption.


Approach:


Identify Bad Blocks:


I used the badblocks command to scan the HDD (sda) and generated a list of bad blocks.
Command:


```
sudo badblocks -sv /dev/sda -o badblocks_sda.txt
``` (would -w be beneficial?)




Mark Bad Blocks on LV filesystem:




After obtaining the list of bad blocks, I use fsck -l to mark them on the LV filesystem.


Command:


```
sudo fsck -l badblocks_sda.txt /dev/nfs_dir_vg/nfs_dir_lv
```


Questions:




Does this approach correctly mark bad blocks on the LV filesystem spanning multiple PV?
Are there any potential pitfalls or better approaches to handle this scenario?
I would appreciate any insights or feedback on this approach. Thank you!

---

### Post by TheFu on 2024-04-13
Bad blocks are recognized by the HDD hardware and get reallocated blocks from spares included in the device. That's my understanding. We don't need to do anything special to make it happen.

Now, the warning I have is about spanning a single file system across multiple HDDs.  Typically, this is done for convenience, but it effectively doubles the chances of data lose.  Most if you stripe the data across both devices, since striping will split 50% of the writes between both HDDs, providing better performance, when everything works. When everything isn't working perfectly, data corruption and very poor performance happen.  

I spanned a file system across 3 HDD long ago, using concatenation.  Then 1 of those disks failed and all the data on all three disks became unavailable.  I know more now and tools are better these days, so perhaps I could have gotten 2/3rds of the data back.  At the time, it was a loss of about 80% of all the data I had.

These days, most of the time when people want to span a file system across multiple disks, it is for convenience and because they have media files.  They think that media center software can only have 1 location for TV and 1 location for Movies and 1 location for Music.  This isn't the actual situation for any of the top 10 popular media center software.  All of them support providing multiple locations for each type of media, which means adding directories that are on different physical disks. For example, I've used XBMC, Kodi, Plex, and Jellyfin media servers.  I have Movies in 3 different disks:
```
/d/D1/M
/d/D2/M
/d/D3/M
```

Bet you can guess where I put TV shows.
```
/d/D1/T
/d/D2/T
/d/D3/T
```

Crazy, right?  Proof I'm not making this up. Here are the NFS mounts for those disks:
```
$ dft
Filesystem                                       Type  Size  Used Avail Use% Mounted on
istar:/d/D1                                      nfs4  3.5T  3.5T   29G 100% /d/D1
istar:/d/D2                                      nfs4  3.6T  3.6T   20G 100% /d/D2
istar:/d/D3                                      nfs4  3.6T  3.6T   23G 100% /d/D3
```

Of course, you may not be spanning file systems across multiple disks for media at all.  There are other methods to keep normal file systems on single disks, but mux those into a virtual view if that is needed.  I've never done it, but there used to be UnionFS and others (Unionfs vs Aufs vs Overlayfs vs mhddfs vs MergerFS) designed specifically for this need.  Wouldn't hurt to do a little research on the pros/cons of each.

BTW, I love, love, love LVM and use it on nearly all my systems.  But since my data loss, I never span file systems across multiple disks, unless it is using LVM in RAID1 mode.  Also, I have excellent backups, which I couldn't afford to have back when all that data was lost.  In another window, I'm currently migrating data of a dying 8TB HDD onto a new 8TB HDD.  Looks like it won't finish until sometime tomorrow because my only working dock is USB2. ;(
```
     ipos:  102147 MB, non-trimmed:        0 B,  current rate:  44433 kB/s
     opos:  102147 MB, non-scraped:        0 B,  average rate:  40136 kB/s
non-tried:    7899 GB,  bad-sector:        0 B,    error rate:       0 B/s
  rescued:  102147 MB,   bad areas:        0,        run time:     42m 25s
pct rescued:    1.27%, read errors:        0,  remaining time:     19h 31m
                              time since last successful read:          0s

```
I'm particular about HDD selection.

---

### Post by pogo7 on 2024-04-16
Thank you for your response,


I've decided to mount the drives separately due to significant issues with one of them. The HDD in question has persistent problems with bad sectors, occasionally numbering over 1,000 according to SMART diagnostics. Despite attempts to fix them, they often reappear in subsequent scans. Consequently, I've reverted to using ext4 as the filesystem and am employing badblocks to manage it. Fortunately, this approach seems to be functioning adequately. While I initially considered LVM for its convenience, it appears that the drive's condition is beyond what any FS other than ext4 & badblocks can handle.


I trust that the data migration process proceeded smoothly,


Best regards.

---

### Post by TheFu on 2024-04-16
When you look at the SMART data, if there's more than about 10 reallocated blocks, it is time to get a new HDD and stop using for anything important.  Relegate the HDD to sneaker*net use for unimportant files only until it dies completely.

1000 bad blocks would have me placing the HDD into my drill 5 holes and Thermite pile for total destruction.

---

