---
title: "How bad is deleting /opt/?"
date: 2008-01-12
forum: General Help
---

### Post by Pichu0102 on 2008-01-12
I, a long while back, downloaded Google Desktop for Linux, around when it first came out. Then I removed it, and it took /opt with it.

I'm just wondering how long I have left before my installation breaks down. :(

---

### Post by Steveway on 2008-01-12
I only have Picasa and AcetoneISO in there.
So you should be all right if you recreate it with root as the owner and read+write for root and only read permissions for everyone else.

---

### Post by geraldm on 2008-01-12
The directory /opt should contain optional packages.  Your system should not break after removing the directory and its subdirectories.  You will not be able to use any programs that
were deleted, and the worst I would expect would be some broken links.

Gerald

---

### Post by taurus on 2008-01-12
Meanwhile, you can recreate /opt again if you wish.

```
sudo mkdir /opt
```

---

