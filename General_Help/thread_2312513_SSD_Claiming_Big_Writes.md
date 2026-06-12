---
title: "SSD Claiming Big Writes"
date: 2016-02-04
forum: General Help
---

### Post by Marcaitus on 2016-02-04
I'm running Xubuntu 15.10 with a 256GB SSD as my OS drive. Every once in  awhile my disk monitor will report that it has written hundreds of  gigabytes to the SSD even though there's no way I could have done that  and it's nearly the entire size of the SSD. When I check disk space  nothing is out of the ordinary and everything is accounted for.

Does this have to do with TRIM or something? I've never used an SSD before.

```

grep sdb /proc/diskstats
   8      16 sdb 834918 1010 31407898 299816 424575 652073 464781080 1263572 0 563508 1563200
   8      17 sdb1 834557 1010 31394730 299780 387441 652073 464780272 1262492 0 562472 1562180

df -m /dev/sdb1
Filesystem     1M-blocks  Used Available Use% Mounted on
/dev/sdb1         225215  7791    205961   4% /

```

464781080 sectors * 512 bytes per sector = 221.62 GB of writes.

There's no way that's possible as the only thing I use it for is the OS, no media files are stored on it whatsoever. This is the second time I've caught this happening so it's not a one time occurrence.

---

