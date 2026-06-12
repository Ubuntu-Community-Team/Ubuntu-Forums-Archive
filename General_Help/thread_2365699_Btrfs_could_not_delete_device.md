---
title: "Btrfs could not delete device"
date: 2017-07-09
forum: General Help
---

### Post by hugoxyu on 2017-07-09
Hi and thank you in advance and please forgive my english :)

I'm facing a problem with btrfs. In essence I cannot delete a device within a two-drive pool.

Some background info:
The system is a pet-project server with some btrfs filesystems and some lxd containers runing different services.

 The btrfs with problems info is:
```
btrfs fi show /mnt/pool_nocrit/Label: 'POOL_NOCRIT'  uuid: 4cfd2681-985c-4488-b8ac-b5d23fe5d249
        Total devices 2 FS bytes used 825.59GiB
        devid    4 size 2.73TiB used 2.19TiB path /dev/sda
        devid    5 size 1.36TiB used 41.03GiB path /dev/sdb

```

I've taken out critical info, so there's no problem with losing data within this pool. But for the sake of experiencing, i'm triying to rescue this. Of course I can wipe out the entire drives and starting from fresh, but this is not the point.

Some time ago i've been experiencing automatic read-only remounts on this pool. Looking at the syslog, I found a lot of lines like this:

```

syslog.6:Jul  3 08:26:16 brocoli kernel: [ 1864.319596] BTRFS warning (device sda): checksum error at logical 8420365942784 on dev /dev/sdb, sector 79438944, root 8009, inode 1499244, offset
 0, length 4096, links 7 (path: patio/weekly.0/localhost/usr/share/vim/vim74/lang/pl/LC_MESSAGES/vim.mo)

```

After deleting the files shown in syslog, after sometime, this same errors returned.

There's no aparent problems in both drives. I'm running long and short SMART tests periodically:

smartcl on /dev/sda:
```

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%     21115         -
# 2  Short offline       Completed without error       00%     21083         -
# 3  Short offline       Completed without error       00%     21059         -


ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   200   200   051    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0033   200   200   140    Pre-fail  Always       -       0

```


smartcl on /dev/sdb:
```

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed without error       00%      2373         -
# 2  Short offline       Completed without error       00%      2344         -
# 3  Short offline       Completed without error       00%      2320         -


ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   100   100   051    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0

```

Since the errors always seemed to be on /dev/sdb (syslog dixit) I'm trying first to delete /dev/sdb from the pool:
```

# btrfs device delete /dev/sdb /mnt/pool_nocrit/
ERROR: error removing device '/dev/sdb': Input/output error

```

With this on syslog:
```

Jul  9 20:00:07 brocoli kernel: [434592.209276] BTRFS info (device loop0 ): relocating block group 8423717666816 flags 1
Jul  9 20:00:08 brocoli kernel: [434592.933558] BTRFS warning (device loop0 ): csum failed ino 277 off 12279808 csum 2089608114 expected csum 1923434760
Jul  9 20:00:08 brocoli kernel: [434592.933779] BTRFS warning (device loop0 ): csum failed ino 277 off 12279808 csum 2089608114 expected csum 1923434760

```

First question: Why is showing "loop0" since the pool is now using only /dev/sda and /dev/sdb?
**One of the things I've tried before posting this is:**
[LIST]
[*]Create a loop device to a file with the same size of /dev/sdb (1.5Tb)
[*]Replace /dev/sdb with this new loop device** 'btrfs replace start 5 /dev/loop0 /mnt/pool_nocrit' **
[*]Since it has not changed anything (same input/output errors, same csum errors, same errors on files, etc), i've rolled back this with **'btrfs replace start 5 /dev/sdb /mnt/pool_nocrit' **
[/LIST]

I've tried remount with rescue options:  **same results** (input/output error)

Now some checks:
```

Checking filesystem on /dev/sdb
UUID: 4cfd2681-985c-4488-b8ac-b5d23fe5d249
checking extents
checking free space cache
checking fs roots
checking csums
checking root refs
found 2770248972646 bytes used err is 0
total csum bytes: 2697638396
total tree bytes: 5744492544
total fs tree bytes: 2681274368
total extent tree bytes: 206028800
btree space waste bytes: 719657169
file data blocks allocated: 31345599639552
 referenced 2771684646912

```

```

# btrfs scrub status /dev/sdb
scrub status for 4cfd2681-985c-4488-b8ac-b5d23fe5d249
        scrub started at Wed Jul  5 10:43:17 2017 and finished after 00:07:07
        total bytes scrubbed: 41.78GiB with 11129 errors
        error details: csum=11129
        corrected errors: 0, uncorrectable errors: 11129, unverified errors: 0

```

```

#btrfs check --init-csum-tree /dev/sdb
Creating a new CRC tree
Checking filesystem on /dev/sdb
UUID: 4cfd2681-985c-4488-b8ac-b5d23fe5d249
Reinit crc root
Unable to find block group for 0
extent-tree.c:289: find_search_start: Assertion `1` failed.
btrfs[0x438110]
btrfs(btrfs_reserve_extent+0x70b)[0x43c31e]
btrfs(btrfs_alloc_free_block+0x63)[0x43c5ae]
btrfs[0x432459]
btrfs(btrfs_search_slot+0xc22)[0x43366f]
btrfs(btrfs_csum_file_block+0x268)[0x440a2e]
btrfs[0x409ca8]
btrfs(cmd_check+0xdd6)[0x425315]
btrfs(main+0x139)[0x40ec30]
/lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xf0)[0x7f3d6e6ff830]
btrfs(_start+0x29)[0x40ec69]

```

It seems to be a logical error, not a problem with the drive.

As an exercice I want to not to delete the entire btrfs filesystem and rebuild it. 

Can you guide me on to do more some tests to light up the real problem? 
There's anything I can do to repair the filesystem?

Thanks in advance.

Hugo.

edit: i'm using "ubuntu 16.04.02 LTS"

---

