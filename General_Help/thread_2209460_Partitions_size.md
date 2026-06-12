---
title: "Partitions size"
date: 2014-03-05
forum: General Help
---

### Post by PokerLegion on 2014-03-05
I made partitions using Ubiquity (50GB root, 400GB home and 1GB swap) parted -l command show me this:
```
Number  Start   End     Size    Type     File system     Flags
 1      1049kB  50,0GB  50,0GB  primary  ext4            boot
 2      50,0GB  450GB   400GB   primary  ext4
 3      450GB   451GB   1024MB  primary  linux-swap(v1)

```
Disks application also show me this, so all is ok i think BUT system monitor show 49,1GB for root, 393,6GB for home and 976,6MiB (what is this MiB?) for swap... Should i care about this or all is ok? I am perfectionist so you know, it bothers me :rolleyes:

---

### Post by monkeybrain20122 on 2014-03-05
I think it has something to do with units. In computer speak a kilo is 1024, but conventionally it is 1000 etc.
BTW 50G / is wait too much IMO ~15G would be more than enough for most normal use. Maybe 20G if you install a lot of games which typically take up more space or if you install some huge proprietary software (e.g Matlab) but I would install those in /home instead and just symlink them to the file system.

---

### Post by PokerLegion on 2014-03-05
Thanks for reply. So partitions are ok? This 50GB is really 50GB or less? Damn units... Ubuntu works very well with no problems at all but i just want to know ;)
EDIT
I see now... I created (well Ubiquity in fact) 50GB partition 50 x 1000 and i should 50 x 1024 :-k Solved.

---

