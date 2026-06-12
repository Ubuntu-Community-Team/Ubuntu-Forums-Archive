---
title: "Deleted files but disk space didnt free up (.trash empty)"
date: 2007-05-28
forum: General Help
---

### Post by tom72 on 2007-05-28
Ubuntu Feisty with 2.6.20-16-generic kernel installed on /dev/sdb1 which is a 250GB drive
I ran partimage to back up my windows partition on /dev/sda1, which created files of about 170GB in total. Quite a lot so I deleted those files afterwards, even made sure that the ~/.trash is empty but the space isn't freed up.
When I ran the disk usage analyzer it reports that the used space on /dev/sdb1 is about 199GB. When I scan the filesystem in this analyzer it tells me however that I only use about 14GB. So technically I should more than 200GB left! Now where's the space gone??

rebooted ubuntu in recovery mode and mounted the filesystem as readonly and ran fsck. The file system is fine, but fsck also reports that most of the blocks on my drive are used.

tune2fs output:
```

tom@tom-desktop:~$ sudo tune2fs -l /dev/sdb1
tune2fs 1.40-WIP (14-Nov-2006)
Filesystem volume name:   <none>
Last mounted on:          <not available>
Filesystem UUID:          54d3e226-3ff0-4181-90ad-4bb5b548f67e
Filesystem magic number:  0xEF53
Filesystem revision #:    1 (dynamic)
Filesystem features:      has_journal resize_inode dir_index filetype needs_recovery sparse_super large_file
Filesystem flags:         signed directory hash 
Default mount options:    (none)
Filesystem state:         clean
Errors behavior:          Continue
Filesystem OS type:       Linux
Inode count:              29769728
Block count:              59528849
Reserved block count:     2976442
Free blocks:              6404456
Free inodes:              29577903
First block:              0
Block size:               4096
Fragment size:            4096
Reserved GDT blocks:      1009
Blocks per group:         32768
Fragments per group:      32768
Inodes per group:         16384
Inode blocks per group:   512
Filesystem created:       Tue Apr 24 14:47:58 2007
Last mount time:          Mon May 28 17:37:49 2007
Last write time:          Mon May 28 17:37:49 2007
Mount count:              1
Maximum mount count:      34
Last checked:             Mon May 28 17:27:45 2007
Check interval:           15552000 (6 months)
Next check after:         Sat Nov 24 16:27:45 2007
Reserved blocks uid:      0 (user root)
Reserved blocks gid:      0 (group root)
First inode:              11
Inode size:               128
Journal inode:            8
Default directory hash:   tea
Directory Hash Seed:      6776c327-8e7c-4a69-864d-a60b7937ef80
Journal backup:           inode blocks

```

```

tom@tom-desktop:~$ du -hs /
15G     /
tom@tom-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sdb1             224G  200G   14G  94% /
varrun               1014M  228K 1013M   1% /var/run
varlock              1014M     0 1014M   0% /var/lock
procbususb           1014M  120K 1014M   1% /proc/bus/usb
udev                 1014M  120K 1014M   1% /dev
devshm               1014M     0 1014M   0% /dev/shm
lrm                  1014M   33M  981M   4% /lib/modules/2.6.20-16-generic/volatile

```

Any help would be greatly appreciated!
-Tom

---

### Post by tom72 on 2007-05-28
Problem solved: I deleted those files as root, so they appeared in /root/.trash

I guess I won the stupidest noob of the year award :popcorn:

---

### Post by orb9220 on 2007-05-28
Nope I Beach Ya!

Alt-F2 and entered msconfig.

Thought I was in windows?

> "Brain and Brain, What is Brain!"

---

### Post by tom72 on 2007-05-29
Wow, now that certainly won you that award :grin:

---

