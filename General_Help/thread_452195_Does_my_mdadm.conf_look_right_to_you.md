---
title: "Does my mdadm.conf look right to you?"
date: 2007-05-23
forum: General Help
---

### Post by rocktorrentz on 2007-05-23
Here is my mdadm.conf which is supposed to be for a 3 drive raid 5 array. However it says that there is one spare which I don't think there should be but i'll leave that for you to decide.
```

DEVICE partitions
ARRAY /dev/md0 level=raid5 num-devices=3 spares=1 UUID=45d042ca:ff79345d:7bb08481:f2cd1ae2

```

Thanks in advance
rocktorrentz

---

### Post by lintoolman on 2007-05-23
What is the output of the command:

```

mdadm --detail /dev/md0
```

Since mdadm doesn't need a configuration file, you can always generate another one if you desire.

Check out this url and see if it helps.

[http://nst.sourceforge.net/nst/docs/user/ch14.html](http://nst.sourceforge.net/nst/docs/user/ch14.html)

---

