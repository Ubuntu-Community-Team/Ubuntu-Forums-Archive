---
title: "Check whole hard disk for bad blocks"
date: 2008-02-13
forum: General Help
---

### Post by xdcdx on 2008-02-13
Hello,

I have a disk with some ext3 partitions and a swap one. I want to check the whole disk for bad blocks.

I know the ext3 ones should be checked with 'fsck.ext3 -c'. What about the swap partition? Should I use the 'badblocks' command? With which options? Shouldn't there exist a friendlier command for that?

Cheers.

---

### Post by jan quark on 2008-02-14
check this site out

[http://ubuntumagnet.com/2008/01/checking-disks-errors-using-badblocks-command](http://ubuntumagnet.com/2008/01/checking-disks-errors-using-badblocks-command)

and I would suggest this command taken from this site
```

sudo badblocks -s  -c 10240 /dev/sdx
```

---

